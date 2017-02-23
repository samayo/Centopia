## centopia | the mariadb install guide

> This guide shows how to build/install MariaDB 5.5.40 from src on CentOS 7  

##### If you want to just run 4 lines of code and be done with it, open & follow the "automation" file. 

Manual Build
-------

Update CentOs to use latest and stable tools
````bash
$ yum -y update
````

Install the tools that are required to run build / run MariaDB
````bash
// for 32 bit
$ yum -y install cmake glibc.i686 ncurses-devel
// for 64 bit
yum -y install gcc gcc-c++ libtool automake autoconf cmake python-devel libxml2-devel libpng-devel curl-devel freetype-devel mesa-libGL-devel mysql-server mysql-devel libvorbis-devel
````

Get a copy of the current mariadb source code
````bash
$  wget https://downloads.mariadb.org/f/mariadb-5.5.40/source/mariadb-5.5.40.tar.gz
$  tar xzvf mariadb-5.5.40.tar.gz
$  cd mariadb-5.5.40
````

We will configure the install with the below settings. You are free to add/remove as long as you know
what you are doing. 
````php
$ mkdir build
$ cd build
$ cmake ..  -DWITH_READLINE=1  -DWITH_SSL=bundled  -DWITH_ZLIB=system  -DDEFAULT_CHARSET=utf8  -DDEFAULT_COLLATION=utf8_general_ci  -DENABLED_LOCAL_INFILE=1  -DWITH_EXTRA_CHARSETS=all  -DWITH_ARIA_STORAGE_ENGINE=1  -DWITH_XTRADB_STORAGE_ENGINE=1  -DWITH_ARCHIVE_STORAGE_ENGINE=1  -DWITH_INNOBASE_STORAGE_ENGINE=1  -DWITH_PARTITION_STORAGE_ENGINE=1  -DWITH_BLACKHOLE_STORAGE_ENGINE=1  -DWITH_FEDERATEDX_STORAGE_ENGINE=1  -DWITH_PERFSCHEMA_STORAGE_ENGINE=1  -DCMAKE_INSTALL_PREFIX=/usr/local/mariadb  -DMYSQL_DATADIR=/usr/local/mariadb/data
````

make and make install
````bash 
make && make install 
````

configure
````bash 
$ groupadd -g 27 -o -r mysql
$ useradd -M -g mysql -o -r -d /usr/local/mariadb/data -s /bin/false -c "MariaDB" -u 27 mysql

$ mkdir -p /usr/local/mariadb/InnoDB/{redoLogs,undoLogs,ib_data}
$ chgrp -R mysql /usr/local/mariadb
$ chown -R mysql /usr/local/mariadb/data
$ mkdir /usr/local/mariadb/logs /usr/local/mariadb/tmp
$ chown mysql:mysql /usr/local/mariadb/{tmp,logs}
$ cd /usr/local/mariadb/scripts
$ ./mysql_install_db --basedir=/usr/local/mariadb --datadir=/usr/local/mariadb/data
$ chown -R mysql:mysql /usr/local/mariadb/data
$ cp /usr/local/mariadb/support-files/mysql.server /etc/init.d/mysqld
$ echo "/usr/local/mariadb/lib" > /etc/ld.so.conf.d/mysql.conf
$ cp ../support-files/my-huge.cnf /etc/my.cnf
$ ln -s /usr/local/mariadb/bin/mysql /usr/local/bin/mysql
$ ln -s /usr/local/mariadb/bin/mysqladmin /usr/local/bin/mysqladmin
$ ln -s /usr/local/mariadb/bin/mysqldump /usr/local/bin/mysqldump
$ /etc/init.d/mysqld start
$ /usr/local/mariadb/bin/mysql_secure_installation
$ service mysqld restart
````
