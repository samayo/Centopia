Install Guest Additions
===================================

### Updates & Installs
run update and install to make sure other important libraries are installed

```
$ yum -y update
$ yum -y install wget zip unzip git kernel-devel gcc bzip2 firewalld
```

### download guest additions
Guest Additions allows you share files between your Windows/Linux Systems and many other [useful things][centos_minimal_iso]. 

Make sure to install GuestAddition version similar to your virtualbox. 
To check your version of virtualbox, go to Help > About VirtualBox. 

If your virtualbox is 5.1.10 then replace {VBOX_VERSION} with that number


### install guest additions
```bash
$ cd /usr/local/src
# Don't forget to replace {VBOX_VERSION} with your virtualbox version
$ wget http://download.virtualbox.org/virtualbox/{VBOX_VERSION}/VBoxGuestAdditions_{VBOX_VERSION}.iso
$ sudo mount -o loop VBoxGuestAdditions_5.0.10.iso /mnt
$ cd /mnt
$ sudo ./VBoxLinuxAdditions.run 
```

### Sharing a windows folder in VB. 
Create any folder in your windows ex: C:/projects

To access/share project folder in Centos, go to 
Settings > Shared Folders click on (+) icond and find the folder you want to share. Now in CentOs to access project do: 

```
$ mkdir /var/www/
$ mount -t vboxsf projects /var/www
```

If this last command does not work, reboot is retry it.. if problem still persists start again from command `sudo mount -o ...`

[virtual_box_intro]:http://www.makeuseof.com/tag/virtualbox-guest-additions-what-they-are-and-how-to-install-them/