
## This is one of the most important shell script

          #!/bin/bash
          
          protodir="/root/qosmos/DemoCode"
          pcapdir="/root/benchmark/pcap-nutch"
          extdir="/root/benchmark/pcap-extracted"
          
          MINPARAMS=3
          
          if [ -n "$1" ]              
          then
           echo "Path to proto_extracter exec: $1" 
          fi 
          
          if [ -n "$2" ]
          then
           echo "PCAP directory: $2"
          fi 
          
          if [ -n "$3" ]
          then
           echo "Extract directory: $3"
          fi
          
          echo "-----------------------------------"
          #echo "command-line parameters are: "$*""
          
          if [ $# -lt "$MINPARAMS" ]
          then
            echo
            #echo "This script needs all the $MINPARAMS command-line arguments!"
          fi  
          
          SUFFIX="pcap"
          PCAPDIR="$pcapdir/*.$SUFFIX"
          echo "Pcap directory:  $PCAPDIR"
          echo
          
          pcount=0; #pcap count
          fcount=0; #failed pcap without any metadata 
          icount=0; #invalid file formatted pcap
          
          for i in $PCAPDIR
          do
            # if no pcap file found in directory break
            if [ "$i" == "$PCAPDIR" ] ; then 
              echo "No Pcap files found in directory $pcapdir"
              break
            fi
          
            IFS="_." read -r -a content<<<"$i"    #split the string into array  
            len="${#content[@]}"                  #array length
                
             if [ "$len" -eq 5 ] || [ "$len" -eq 6 ] ; then
              caseid="${content[1]}"
              #echo "extracting .... $i"
              if [ "$len" -eq 5 ] ; then
               pcapid="${content[2]}_${content[3]}"
              else   
               pcapid="${content[3]}_${content[4]}"
              fi
             else
                echo "skipping file:> $i"
                icount=$(($icount+1))
                continue
             fi
          
           proto="$protodir/proto_data_extract"
           destdir="$extdir/$caseid/$pcapid"
           #echo "dest dir : $destdir"
          
           mkdir -p $destdir
           cd $destdir
           $proto  $i &> /dev/null
           
           fcnt=`ls -1| wc -l`
           if [ "$fcnt" -eq 0 ] ; then
            mv $i "$i.fail"
            rm -rf ../$pcapid
            fcount=$(($fcount+1))
           else
            mv $i "$i.read"
            pcount=$(($pcount+1)) 
           fi
          done
          echo
          echo "Read PCAP files  : $pcount"
          echo "Failed PCAP file : $fcount"
          echo "Skipped PCAP file: $icount"
          exit 0
