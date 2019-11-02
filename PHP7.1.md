Install PHP7 via RPM 
----

#### update yum & install required libraries
```bash
$ yum -y update
$ yum install -y autoconf gcc bison
```

#### Add webtatic yum repository information corresponding to your CentOS/RHEL
```bash
$ rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
$ rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
```

#### install PHP
Install PHP with the extensions you need. check out https://webtatic.com/packages/php70/ for more extensions if needed
```bash
$ yum install --enablerepo=webtatic-testing php71w php71w-opcache php71w-fpm php71w-cli php71w-gd php71w-xml php71w-opcache php71w-pgsql php71w-pdo php71w-pear php71w-mysqlnd php71w-phpdbg php71w-intl php71w-mbstring
```
