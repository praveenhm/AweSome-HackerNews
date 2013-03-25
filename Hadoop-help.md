
Hadoop 

Startup/shutdown: 
Edit /etc/puppet/manifests/nodes.pp, 
change “include namenode_running”  “include namenode_stopped”
change “include datanode_running”  “include datanode_stopped”

After shutdown, wait for 2 mins, then run ps –ef | grep java, and kill stray processes manually (usually tasks)
After startup, wait for 2-5 mins before running etl start etc.

Debugging hadoop issues
Puppet messages: /var/log/messages
Hadoop messages: /var/log/hadoop/ (look for hadop-hadoop-jobtracker.log, hadoop-hadoop-tasktracker.log)
Oozie messages (only on name node): /var/log/oozie/oozie.log

TaskTracker PID:
$  ps -u mapred -f | grep TaskTracker

JobTracker PID:
$ ps –u mapred –f | grep JobTracker

Changing hadoop properties

Edit /etc/puppet/modules/hadoop/templates/* 
(for puppet-managed configuration files like: mapred-site.xml, core-site.xml, hdfs-site.xml)

For all other files, edit /etc/hadoop/conf/*

Restarting hadoop services selectively 

Job tracker restart (name node only)
# service hadoop-0.20-jobtracker restart

Tasktracker restart (all nodes)
# service hadoop-0.20-tasktracker restart

(Some currently running tasks might fail and get moved to insight/outgoing if you restart jobtracker and/or tasktracker)

Other services:
# service oozie restart
# service hadoop-0.20-namenode restart
# service hadoop-0.20-datanode restart

All puppet-managed services have to be started/stopped through puppet, otherwise puppet will restart automatically

Enabling oozie web console

(Do this only when oozie is down, bring down through puppet)
# cd /tmp
# wget http://extjs.com/deploy/ext-2.2.zip 
# cp /opt/insight/install/repo/ojdbc6.jar /tmp
# sudo -u oozie /usr/lib/oozie/bin/oozie-setup.sh -extjs /tmp/ext-2.2.zip -jars /tmp/ojdbc6.jar

Checking to see if hadoop logs are getting full (all nodes)

# cd /var/log/hadoop/userlogs
# ls | wc –l
(If this number exceeds 31000, no more jobs can run)

Cleaning logs manually
First bring down hadoop (using puppet) 
# cd /var/log/hadoop/userlogs/ (run on both nodes)
# rm –rf *
Restart hadoop using puppet
(If you don’t want to bring down hadoop, remove the logs and only restart jobtracker and tasktracker)

Application (etlfw)

Checking ftp in/out locations: /opt/insight/etlfw-*/conf/etl.xml

Checking data cleaning frequency: /opt/insight/etlfw-*/conf/etl/workflow.xml (check Action for oldFileCleaner)

Checking all files in incoming queue:
# hadoop fs -lsr insight/incoming | grep -i csv

Checking to see how many files are yet to be processed in incoming queue:
# hadoop fs -lsr insight/incoming | grep -i csv | grep -v done

Checking to see how many files are processed (raw+aggregate), i.e. all “part” files
# hadoop fs -lsr insight/outgoing | grep -i part

Checking to see how many files have been processed but not transferred to DB machine
# hadoop fs -lsr insight/outgoing | grep -i part| grep -v processed

FTP configuration

To configure a new vsftpd server, add/modify following properties in /etc/vsftpd/vsftpd.conf
Then restart vsftpd: service vsftpd restart
idle_session_timeout=86400
(default is 300)
data_connection_timeout=86400
(default is 300)

To allow us to send .files (for .pig_header)
force_dot_files=YES

To force FTP server to use local time instead of GMT:
use_localtime=YES

Checking FTP logs on DB machine (on .131)
# less /var/log/vsftpd.log

Oozie database cleanup (optional; speeds up startup/shutdown. do this when oozie+hadoop is down)

On database machine (.131), login as xman/xman

[xman@isca-db01 ~]$ sqlplus oozie/oozie
SQL> select table_name from user_tables;

TABLE_NAME
------------------------------
SLA_EVENTS
COORD_ACTIONS
WF_ACTIONS
WF_JOBS
COORD_JOBS

Truncate all above tables, 
SQL> truncate table SLA_EVENTS;
…
SQL> commit;

