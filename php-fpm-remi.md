### PHP 7.2 from famillecollet


```bash
sudo yum install epel-release
sudo rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
yum --enablerepo=remi-php72 install php php-mbstring php-xml php-soap php-xmlrpc php-mbstring php-json php-gd php-mcrypt php-fpm php-pdo 
```

```bash
php -v
```
