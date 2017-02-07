Build PHP-FPM from source
========================

> NOTE: This guide needs small fixes

### Install libraries needed to compile/run PP
```
yum install git autoconf gcc gcc-c++ bison libxml2-devel curl-devel libxslt-devel icu libicu libicu-devel openssl-devel libjpeg-devel libpng-devel libXpm-devel freetype-devel bzip2-devel curl-devel gd-devel  libxml2-devel bison-devel bison re2c libvpx-devel
```

Download the PHP source code and extract it. 

```
wget http://hk1.php.net/get/php-7.1.0.tar.bz2/from/this/mirror  -q -O master.tar.bz2 
bzip2 -d master.tar.bz2
tar -xvf master.tar
cd php-7.0.3
```

Configure PHP with the libraries you want installed. run `./configure --help` if you need more information

```
./configure  --with-config-file-path=/etc/php --enable-phpdbg --enable-intl --with-libdir=/lib/x86_64-linux-gnu --disable-all --with-iconv --with-openssl --with-zlib --with-curl --with-xsl --enable-pdo --enable-sockets --enable-mbstring --with-mysqli --enable-phar --enable-ctype --enable-hash --enable-json --enable-filter --enable-zip --enable-libxml --enable-simplexml --enable-xmlreader --enable-dom --enable-tokenizer --enable-posix --enable-pcntl --enable-cli --enable-exif --with-pdo-mysql=mysqlnd --with-gd --enable-session --enable-fpm --enable-ctype --with-jpeg-dir --with-png-dir --with-xpm-dir --with-freetype-dir  
```

install
```
make && make install
```

Replace the configuration files ... 
```
cp sapi/cli/php /bin/php
cp php.ini-production /etc/php.ini
cp /usr/local/etc/php-fpm.conf.default /usr/local/etc/php-fpm.conf   
cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf
cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm    
chmod +x /etc/init.d/php-fpm     
```
If you are using Nginx as your server, the open www.conf and change user/group from 'apache' to 'nginx'
```
$ vi /usr/local/php/etc/php-fpm.d/www.conf
	$ user nginx 
	$ group nginx
```



