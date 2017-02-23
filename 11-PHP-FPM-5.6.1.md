## centopia | the php-fpm install guide

> This guide shows how the centopia bash script builds PHP-FPM 5.6.1 from src on CentOS 7
> or follow the "Manual Build" means you can follow this guide to install PHP-FPM yourself. 

##### If you don!t want to do this manually, check the "centopia way" at the end of this page. 
 
Manual Build
-------

Install the necassary devel components to build/run php
````bash
$ yum -y install wget gcc libxml2-devel bison-devel bison re2c libvpx-devel libjpeg-devel git openssl-devel libpng-devel libXpm-devel freetype-devel bzip2-devel curl-devel  gd-devel 
````

Download and save the PHP source
````bash
$ cd /usr/local/src/ && wget -qO php-5.6.1.tar.bz2 http://ch1.php.net/get/php-5.6.1.tar.bz2/from/this/mirror   
````

Extract and configure (/customize) php
````bash
$ tar jxf php-5.6.1.tar.bz2 && cd php-5.6.1
$ ./configure --prefix=/usr/local/php --with-mysql  --with-curl --enable-cli --enable-mbstring --enable-exif --with-pdo-mysql=mysqlnd --with-gd  --enable-session --enable-dom --enable-phpdbg --enable-fpm --enable-ctype --with-vpx-dir --with-jpeg-dir --with-png-dir --with-xpm-dir --with-freetype-dir 
````

If your VPS has less than  512RAM create a swap file to prevent running out of memory
````bash
$ dd if=/dev/zero of=/swapfile1 bs=1024 count=524288 
$ mkswap /swapfile1 
$ chown root:root /swapfile1 
$ chmod 0600 /swapfile1 
$ swapon /swapfile1 
$ sed -i '/swapfile1 swap swap defaults 0 0' /etc/fstab
````

Do make and install
````bash 
$ make && make install 
````

Copy some configs files to standard directory
````bash
$ cp sapi/cli/php /bin/php
$ cp php.ini-development /usr/local/php/lib/php.ini    
$ cp etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf    
$ cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm    
$ chmod +x /etc/init.d/php-fpm     
````

Restart PHP and open firewall.
````bash 
$ systemctl start firewalld  
$ firewall-cmd --add-service=http 
$ firewall-cmd --permanent --add-service=http 
$ systemctl restart firewalld 
$ firewall-cmd --zone=public --add-port=http/tcp --permanent
$ service php-fpm start    
$ service php-fpm restart
````

#### THE centopia WAY 
Type these commands in your terminal to get exactly the same result as above but with a lot less time. 

````bash
$ wget -qO ~/centopia  http://goo.gl/pXvjVl
$ cp ~/centopia /usr/bin/centopia
$ chmod ug+x /usr/bin/centopia
$ bash centopia install php-fpm-5.6.1
````
