Install FTP
----

#### update yum & install required libraries
```bash
$ yum -y update
$ yum -y install vsftpd
```

#### Configure  /etc/vsftpd/vsftpd.conf
```bash
listen=YES
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd 
```
add `rsa_cert_file=/etc/ssl/private/vsftpd.pem`  if you have an ssl certificate

#### reload/restart
```bash
$ firewall-cmd --permanent --add-service=ftp
$ firewall-cmd --reload
```

##### enable and restart 
```bash
$ systemctl restart vsftpd.service
$ systemctl enable vsftpd.service
```
