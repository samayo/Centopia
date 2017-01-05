Install PHP(-FPM) on CentOs7
========================

delel tools 

yum install git autoconf gcc gcc-c++ bison libxml2-devel curl-devel libxslt-devel icu libicu libicu-devel openssl-devel libjpeg-devel libpng-devel libXpm-devel freetype-devel bzip2-devel curl-devel gd-devel  libxml2-devel bison-devel bison re2c libvpx-devel
wget http://hk1.php.net/get/php-7.1.0.tar.bz2/from/this/mirror  -q -O master.tar.bz2 
#wget http://de1.php.net/get/php-7.0.3.tar.bz2/from/this/mirror -q -O master.tar.bz2 
bzip2 -d master.tar.bz2
tar -xvf master.tar
cd php-7.0.3

# ? ./buildconf

./configure  --with-config-file-path=/etc/php --enable-phpdbg --enable-intl --with-libdir=/lib/x86_64-linux-gnu --disable-all --with-iconv --with-openssl --with-zlib --with-curl --with-xsl --enable-pdo --enable-sockets --enable-mbstring --with-mysqli --enable-phar --enable-ctype --enable-hash --enable-json --enable-filter --enable-zip --enable-libxml --enable-simplexml --enable-xmlreader --enable-dom --enable-tokenizer --enable-posix --enable-pcntl --enable-cli --enable-exif --with-pdo-mysql=mysqlnd --with-gd --enable-session --enable-fpm --enable-ctype --with-jpeg-dir --with-png-dir --with-xpm-dir --with-freetype-dir  

make && make install

cp sapi/cli/php /bin/php
cp php.ini-production /usr/local/php/lib/php.ini    ==== cp php.ini-production /etc/php.ini
cp /usr/local/etc/php-fpm.conf.default /usr/local
/etc/php-fpm.conf   
cp /usr/local/php/etc/php-fpm.d/www.conf.default /usr/local/php/etc/php-fpm.d/www.conf
cp sapi/fpm/init.d.php-fpm /etc/init.d/php-fpm    
chmod +x /etc/init.d/php-fpm     

$ vi /usr/local/php/etc/php-fpm.d/www.conf
	$ user nginx 
	$ group nginx

$ vi /usr/local/php/lib/php.ini
	cgi.fix_pathinfo=1  --> cgi.fix_pathinfo=0



