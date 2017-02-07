Install Nginx
========================
To install Nginx create a file at: 
```
$ vi /etc/yum.repos.d/nginx.repo
```
Now copy past this below text, replace {OS} with CentOs and {OSRELEASE} with your CentOs version eg:  
for now, replace {OS} with "centos" and {OSRELEASE} with "7". without the quotes 
```
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/mainline/{OS}/{OSRELEASE}/$basearch/
gpgcheck=0
enabled=1
```
### install nginx
```
$ yum install nginx 
```


### reload system daemon, open & save firewall accessW for (nginx) http ports
```
$ systemctl daemon-reload 
$ systemctl start firewalld
$ firewall-cmd --permanent --add-service=http
$ sudo firewall-cmd --reload
```
