Install PHP(-FPM) on CentOs7
========================

$ rpm -Uvh https://mirror.webtatic.com/yum/el7/epel-release.rpm
$ rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm


$ yum install php56w-fpm php56w-cli php56w-gd php56w-opcache php56w-pgsql php56w-pdo php56w-pear php56w-mysqlnd

# reload system daemon, open & save firewall for (php-fpm) http ports
$ systemctl daemon-reload 
$ systemctl start firewalld
$ firewall-cmd --add-service=http 
$ firewall-cmd --permanent --add-service=http
$ sudo firewall-cmd --reload

$ service php-fpm reload


## configuration with nginx. 
$ vi /etc/php-fpm.d/www.conf
	user = nginx
	group = nginx
