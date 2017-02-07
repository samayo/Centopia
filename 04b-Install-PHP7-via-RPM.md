Install PHP-FPM via RPM 
========================

### install some libraries
```bash
$ yum install -y autoconf gcc bison
```

### Add webtatic yum repository information corresponding to your CentOS/RHEL version to yum:
```bash
$ rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
$ rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
```

### install PHP
Install PHP with the extensions you need. check out https://webtatic.com/packages/php70/ for more extensions if needed
```bash
$ yum install --enablerepo=webtatic-testing php70w php70w-opcache php70w-fpm php70w-cli php70w-gd php70w-xml php70w-opcache php70w-pgsql php70w-pdo php70w-pear php70w-mysqlnd php70w-phpdbg php70w-intl
```

If you are using Nginx as your server, the open www.conf and change user/group from 'apache' to 'nginx'
```
$ vi /etc/php-fpm.d/www.conf
	user = nginx
	group = nginx
```