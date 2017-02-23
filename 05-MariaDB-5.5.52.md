Install MariaDB on CentOs7
========================
```
$ sudo yum install -y mariadb-server mariadb
$ sudo systemctl start mariadb.service
$ sudo systemctl enable mariadb.service
$ sudo systemctl restart mariadb.service
$ sudo /usr/bin/mysql_secure_installation
```