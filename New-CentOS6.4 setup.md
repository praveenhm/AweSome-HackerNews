 
### Follow the steps given below to setup a new CentOS 6.4 box.
 
when setting up on windows m/c with a shared partition, make sure there are only 4 master partitons, otherwise 
we can format the rest of partition.

Download the os from the stanford mirror DVD1.iso image
Use standard partition & Development image.
After instalation, do not diable the Bluetooth or wireless, it is a messed up. you need to re-install the 
Networkmanger-gnome applet again.

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



###### .bashrc
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

yum install ntfs-3g

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






