
A guide to download, install and configure a vboxs running CentOs7. 

### Downloading VirtualBox install CentOs (for Windows users)

##### VirtualBox 
01 - Download virtualbox from [here] virtualbox download link
02 - Install it in your windows PC. 

#### CentOs 7 
Download CentOS-7 minimal from [here][centos_minimal_iso]

02 - Download CentOS-7.0-1406-x86_64-Minimal 
	 from 

- Allow vbox networking 
```bash
  $ vi /etc/sysconfig/network-scripts/ifcfg-enp0s3 
  	 @onboot=no => @onboot=yes
```
  
- open access http and ssh port
 vBox settings > network > nat > port forwarding & add ports:    
```bash 
	 http  tcp   127.0.0.1 80 10.0.2.15 80
	 ssh   tcp   127.0.0.1 22 10.0.2.15 22
```

reboot virtualbox

[centos_minimal_iso]:http://isoredirect.centos.org/centos/7/isos/x86_64/