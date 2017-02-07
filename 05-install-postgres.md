Install Postgres
========================

### install rpm and update
```
rpm -Uvh http://yum.postgresql.org/9.4/redhat/rhel-7-x86_64/pgdg-centos94-9.4-1.noarch.rpm
yum update
```

### update 
```
yum install postgresql94-server postgresql94-contrib
/usr/pgsql-9.4/bin/postgresql94-setup initdb

systemctl enable postgresql-9.4
systemctl start postgresql-9.4
```

### configure
open firewall access and configure
````
firewall-cmd --permanent --add-port=5432/tcp
firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --reload
setsebool -P httpd_can_network_connect_db 1
```

make sure it works by accessing postgres
```
su - postgres
psql
```