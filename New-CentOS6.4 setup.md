 
### Below are the steps to setup a new CentOS 6.4 box.

Can't partition problem:
Basically, you can have 4 "real" partitions on a disk; to get more, you make up to 3 Primary partitions, 
then 1 "extended" partition that has multiple "logical" partitions inside of it.

Download the disk image from the stanford mirror DVD1.iso image
Use standard partition & Development image.
After instalation, do not disable the Bluetooth or wireless, it's a messed up. you need to un-install and 
re-install the Networkmanger-gnome applet again.

Software:
-Chrome,
-Adobe Flash,
-uninstall the openJdk 6 first & then install oracle Jdk 7.
-STS 3.2 -> juno 4.2.2
 -configure maven path

edit /etc/hosts
 127.0.0.1 linuxpc
 127.0.0.1 localhost

###To install cloudera CDH4, 
  disable seLinux,
   vi /etc/selinux/config
   selinux=enforcing to disable
   
   cloudera: admin/admin
   http://linuxpc:7180/cmf/services/status
   Edit /var/lib/pgsql/data/pg_hba.conf
     host hue hue 0.0.0.0/0 md5
   Database:hive, 
   username:hive,
   pass : PBBpMFZ70y


###### .bashrc
export JAVA_HOME="/usr/java/default"
export PATH=$PATH:/home/praveen/mydev/springsource/apache-maven-3.0.4/bin

#### To mount ntfs, follow below steps
First you need to install the Extra Packages for Enterprise Linux (EPEL) repository, 
which is done by typing the following into the shell as root assuming you are using 64bit CentOS 6.4:

    #>rpm -Uvh http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm  
    Retrieving http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
    warning: /var/tmp/rpm-tmp.93jDQT: Header V3 RSA/SHA256 Signature, key ID 0608b895: NOKEY
    Preparing...                ########################################### [100%]
       1:epel-release           ########################################### [100%]

    #>yum install ntfs-3g

    Loaded plugins: fastestmirror, refresh-packagekit, security
    Loading mirror speeds from cached hostfile
    epel/metalink                                                                                         |  13 kB     00:00     
     * base: mirror.nwresd.org
     * epel: linux.mirrors.es.net
     * extras: centos.netnitco.net
     * updates: mirrors.easynews.com
    adobe-linux-x86_64                                                                                    |  951 B     00:00     
    base                                                                                                  | 3.7 kB     00:00     
    cloudera-manager                                                                                      |  951 B     00:00     
    epel                                                                                                  | 4.2 kB     00:00     
    epel/primary_db                                                                                       | 5.0 MB     00:10     
    extras                                                                                                | 3.5 kB     00:00     
    google-chrome                                                                                         |  951 B     00:00     
    updates                                                                                               | 3.5 kB     00:00     
    Setting up Install Process
    Resolving Dependencies
    --> Running transaction check
    ---> Package ntfs-3g.x86_64 2:2011.4.12-5.el6 will be installed
    --> Finished Dependency Resolution
    
    Dependencies Resolved
    
    =============================================================================================================================
     Package                     Arch                       Version                               Repository                Size
    =============================================================================================================================
    Installing:
     ntfs-3g                     x86_64                     2:2011.4.12-5.el6                     epel                     247 k
    
    Transaction Summary
    =============================================================================================================================
    Install       1 Package(s)
    
    Total download size: 247 k
    Installed size: 624 k
    Is this ok [y/N]: y
    Downloading Packages:
    ntfs-3g-2011.4.12-5.el6.x86_64.rpm                                                                    | 247 kB     00:00     
    warning: rpmts_HdrFromFdno: Header V3 RSA/SHA256 Signature, key ID 0608b895: NOKEY
    Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
    Importing GPG key 0x0608B895:
     Userid : EPEL (6) <epel@fedoraproject.org>
     Package: epel-release-6-8.noarch (installed)
     From   : /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
    Is this ok [y/N]: y
    Running rpm_check_debug
    Running Transaction Test
    Transaction Test Succeeded
    Running Transaction
    Warning: RPMDB altered outside of yum.
      Installing : 2:ntfs-3g-2011.4.12-5.el6.x86_64                                                                          1/1 
      Verifying  : 2:ntfs-3g-2011.4.12-5.el6.x86_64                                                                          1/1 
    
    Installed:
      ntfs-3g.x86_64 2:2011.4.12-5.el6                                                                                           
    
    Complete!



#### list of handy commands --

    /etc/init.d/network restart
    cd /etc/sysconfig/network-scripts/
    vi ifcfg-wlan0   -wireless lan   
    service NetworkManger restart
    nm-applet
    rpm -qa |grep network
    rfkill list     - gives the list of devices
    rfkill killall   - kills all
    rfkill unblock 0  
    rfkill unblock all
    ncli nw wifi on
    getfacl /dev/rfkill
    iwconfig
    rpm -e java-1.6.0-openjdk-1.6.0.0-1.50.1.11.5.el6_3.x86_64
    rpm -e jdk-1.7.0_17-fcs.x86_64
    rpm -qa |grep jdk
    rpm -ivh /tmp/jdk-7u17-linux-x64.rpm
    yum install ./jdk-7u17-linux-x64.rpm
    ls /etc/alternatives
    vi /etc/hosts
    chmod +x cloudera-manager-installer.bin
    ./cloudera-manager-installer.bin 
    vi /etc/selinux/config 
    chmod +x vpnsetup.sh 
    ./vpnsetup.sh 
    cd /etc/hadoop/conf
    vi hadoop-env.sh 
    vi mapred-site.xml 
    vi hdfs-site.xml 
    vi core-site.xml
    ls /etc/default/cloudera-scm-agent 
    ls /etc/cloudera-scm-server/
    less  /etc/init.d/cloudera-scm-server
    less /var/log/cloudera-scm-server/cloudera-scm-server.log 
    vi /var/log/cloudera-scm-server/db.log 
    vi /var/log/cloudera-scm-agent/cloudera-scm-agent.log
    postgresql status
    /etc/init.d/postgresql status
    service postgresql status
    service postgresql initdb
    psql -U hive -d hive -p PBBpMFZ70y
    sevice cloudera-scm-agent status
    service cloudera-scm-server status
    service cloudera-scm-server-db status
    vi /etc/cloudera-scm-agent/config.ini 
    tail /var/log/cloudera-scm-agent/cloudera-scm-agent.log
    tail -f /var/log/cloudera-scm-agent/cloudera-scm-agent.log
    hdfs dfs /
    psql
    psql -U postgres
    psql -h linuxpc -U hue -d hue
    sql: FATAL:  Ident authentication failed for user
    vi /var/lib/pgsql/data/pg_hba.conf  # edit the file
    service postgresql restart
    psql -h localhost -U hue -d hue
    psql -h localhost -U hive -d hive
    psql -h localhost -U hive 
    psql -h linuxpc -U hive -d hive
    psql  -U hive -d hive
    service postgresql status
    vi /var/lib/pgsql/data/postgresql.conf 
    hadoop fs -ls /
    hadoop fs -ls /user
    psql -h loacalhost -U scm -d scm -p s6uJqlJJPt
    psql -h linuxpc -U scm -d scm -p s6uJqlJJPt
    psql -h linuxpc -U scm -d scm
    find / -name hadoop-examples*
    cd /opt/cloudera/parcels/CDH-4.2.0-1.cdh4.2.0.p0.10/lib/hadoop-0.20-mapreduce/
    hadoop  jar hadoop-examples.jar  pi 10 100   # can't owner is hdfs change it
    psql -U hive -d hive -p PBBpMFZ70y
    find / -name hdfs-site.xml
    vi /etc/hadoop/conf.cloudera.mapreduce1/hdfs-site.xml  
    find / -exec grep -Hn dfs.permissions {} \;      # find dfs.permissions string in every file
    sudo -u hdfs hadoop fs -ls -R /
    sudo -u hdfs hadoop fs -chown mapred:hadoop /tmp/mapred/system
    sudo -u hdfs hadoop fs -ls -R /
    sudo -u hdfs hadoop fs -chown praveen:supergroup /user  # you can't run the example, since owner is hdfs change it to praveen
    
### posgtgresql 8.4.11
    yum install pgadmin3    # install the admin tool
    subl /var/lib/pgsql/data/postgresql.conf 
    subl /var/lib/pgsql/data/pg_hba.conf
    service postgresql status
    service postgresql stop
    service postgresql start
    chkconfig postgresql on   
    sudo -u postgres psql   
    
    
    $ sudo -u postgres psql
    could not change directory to "/home/praveen"
    psql (8.4.13)
    Type "help" for help.
    
    postgres=# select name, setting from pg_settings where category = 'File Locations';
           name        |               setting               
    -------------------+-------------------------------------
     config_file       | /var/lib/pgsql/data/postgresql.conf
     data_directory    | /var/lib/pgsql/data
     external_pid_file | 
     hba_file          | /var/lib/pgsql/data/pg_hba.conf
     ident_file        | /var/lib/pgsql/data/pg_ident.conf
    (5 rows)
    
    postgres=# SELECT name, context, setting, boot_val, reset_val FROM pg_settings WHERE name in('listen_addresses','max_connections','shared_buffers','effective_cache_size','work_mem', 'maintenance_work_mem') ORDER BY context,name;
    
             name         |  context   | setting | boot_val  | reset_val 
    ----------------------+------------+---------+-----------+-----------
     listen_addresses     | postmaster | *       | localhost | *
     max_connections      | postmaster | 100     | 100       | 100
     shared_buffers       | postmaster | 4096    | 1024      | 4096
     effective_cache_size | user       | 16384   | 16384     | 16384
     maintenance_work_mem | user       | 16384   | 16384     | 16384
     work_mem             | user       | 1024    | 1024      | 1024
    (6 rows)




    

For sudo previlage add the user praveen
 visudo


