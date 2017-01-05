Install PHP(-FPM) on CentOs7
========================

### Install devel tools 
$ yum install -y git autoconf gcc bison

### Add webtatic yum repository information corresponding to your CentOS/RHEL version to yum:

$ rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
$ rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm


### install PHP
$ yum install --enablerepo=webtatic-testing php70w php70w-opcache php70w-fpm php70w-cli php70w-gd php70w-xml php70w-opcache php70w-pgsql php70w-pdo php70w-pear php70w-mysqlnd php70w-phpdbg php70w-intl

$ y

## configure 

## configuration with nginx. 
$ vi /etc/php-fpm.d/www.conf
	user = nginx
	group = nginx
