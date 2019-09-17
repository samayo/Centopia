### INSTALL PHP From famillecollet

```bash
sudo yum install epel-release3
sudo yum install epel-release
sudo rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
yum --enablerepo=remi-php72 install php
yum --enablerepo=remi-php72 install php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt php-fpm
p`hp-fpm -v
``bash
