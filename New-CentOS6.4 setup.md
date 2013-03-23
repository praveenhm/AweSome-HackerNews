Below are the things to set up in new CentOS 6.4 box.

Download the os from the stanford mirror DVD1.iso image
Use standard partition & Development image.
Do not diable the Bluetooth or wireless, it is a messed up. you need to re-install the Networkmanger-gnome applet 
again.

Software:
-Chrome,
-Adobe Flash,
-uninstall the openJdk & install oracle Jdk.
-STS 3.2 -> juno 4.2.2
 -configure maven path

edit /etc/hosts
127.0.0.1 linuxpc
127.0.0.1 localhost

To install cloudera, disable seLinux,
vi /etc/selinux/config
selinux=enforcing to disable
cloudera: admin/admin
http://linuxpc:7180/cmf/services/status
Edit /var/lib/pgsql/data/pg_hba.conf
  host hue hue 0.0.0.0/0 md5



# .bashrc
export JAVA_HOME="/usr/java/default"
export PATH=$PATH:/home/praveen/mydev/springsource/apache-maven-3.0.4/bin

# To mount ntfs, follow below steps
First you need to install the Extra Packages for Enterprise Linux (EPEL) repository, 
which is done by typing the following into the shell as root assuming you are using 64bit CentOS 6.4:

rpm -Uvh http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-7.noarch.rpm


  Retrieving http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
  warning: /var/tmp/rpm-tmp.93jDQT: Header V3 RSA/SHA256 Signature, key ID 0608b895: NOKEY
  Preparing...                ########################################### [100%]
     1:epel-release           ########################################### [100%]



