Install Nginx on CentOS7
========================

### create nginx.repo and add contents
> Replace “OS” with “rhel” or “centos”, depending on the distribution used, 
and “OSRELEASE” with “5”, “6”, or “7”, for 5.x, 6.x, or 7.x versions, respectively. 
```
$ vi /etc/yum.repos.d/nginx.repo
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/mainline/centos/7/$basearch/
gpgcheck=0
enabled=1
```
### install nginx
```
$ yum install nginx 
```


### reload system daemon, open & save firewall for (nginx) http ports
```
$ systemctl daemon-reload 
$ systemctl start firewalld
$ firewall-cmd --permanent --add-service=http
$ sudo firewall-cmd --reload
```
