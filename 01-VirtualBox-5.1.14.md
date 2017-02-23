Download VirtualBox & CentOs 7
------

### VirtualBox 

01 - Download virtualbox for windows 7/8/10 [from this link][download_virtualbox]    
02 - Install it in your windows PC. 

Once installed, create a new machine and chose Linux as Distro, and redhat64 OS

### CentOs 7 

Download CentOS-7 minimal from [here][centos_minimal_iso] (file name: CentOS-7-x86_64-DVD-1611.iso)


Once loged in your virtual box, enable networking by changing onboot to yes, in your network-scripts/ directory 
```bash
  $ vi /etc/sysconfig/network-scripts/ifcfg-enp0s3 
  	 @onboot=no => @onboot=yes
```
  
If you want to access ssh, and from your host machine go to: 
settings > network > nat > port forwarding & add ports and add these 
```bash 
	 http  tcp   127.0.0.1 80 10.0.2.15 80
	 ssh   tcp   127.0.0.1 22 10.0.2.15 22
```

reboot virtualbox

[centos_minimal_iso]:http://buildlogs.centos.org/rolling/7/isos/x86_64/
[download_virtualbox]:https://www.virtualbox.org/wiki/Downloads
