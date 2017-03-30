Install MariaDB 5.5
----

#### install mariadb server
$ sudo yum install -y mariadb-server mariadb
$ sudo systemctl start mariadb.service
$ sudo systemctl enable mariadb.service
$ sudo systemctl restart mariadb.service

#### configure
$ sudo /usr/bin/mysql_secure_installation
```
