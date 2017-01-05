Install Guest Additions on CentOS 7
===================================

# update yum and install some components. 
$ yum -y update
$ yum -y install wget zip unzip git kernel-devel gcc bzip2 firewalld

# switch directory and download guest additions. (same version to vbox)
$ cd /usr/local/src
$ wget http://download.virtualbox.org/virtualbox/5.0.10/VBoxGuestAdditions_5.0.10.iso
$ sudo mount -o loop VBoxGuestAdditions_5.0.10.iso /mnt
$ cd /mnt

# run virtualbox 
# if this does not work, reboot and start again from line 11 i.e sudo mount -o ..
$ sudo ./VBoxLinuxAdditions.run 

# Open, vBox > Device > Shared Folders and choose a folder you want to share

$ mkdir /var/www/
$ mount -t vboxsf *folder_name_you_want_to_share* /var/www

