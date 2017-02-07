## centopia | the nginx build guide

This is a step-by-step guide on how to build Nginx-1.6.2 from source on a CentOS 7 VPS or Virtualbox.   

Manual Build
-------

update yum to use current & stable CentOs libraries
````bash
$ yum -y update
````

install the below packages that are needed to run / build Nginx
````bash
$ yum -y install bzip2 gcc-c++ pcre-devel zlib-devel openssl-devel libxslt-devel 
````

create a repository folder and dowmload the Nginx source file 
````bash
$ cd /usr/local/src && wget -O nginx-1.6.2.tar.gz http://nginx.org/download/nginx-1.6.2.tar.gz 
$ tar -xzf  nginx-1.6.2.tar.gz 
$ cd nginx-1.6.2
````

let's configure Nginx with the basic modules. (you can add/remove any module you want)
````bash
$ ./configure --user=nginx --group=nginx --prefix=/usr/share/nginx --sbin-path=/usr/sbin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx.pid --lock-path=/var/run/nginx.lock --with-http_ssl_module --with-http_gzip_static_module --with-pcre 
````

build Nginx using make and make install
````bash
$ make && make install
````

create nginx user
````bash 
$ useradd -r nginx
````

get Nginx script for the 'service' command and give it proper permissions (for exec)
````bash
$ wget -O https://raw.githubusercontent.com/samayo/centopia/master/nginx-1.6.2/utils/init /etc/init.d/nginx
$ chmod +x  /etc/init.d/nginx
````

reload system daemon, open & save firewall got (nginx) http ports
````bash
$ systemctl daemon-reload 
$ systemctl start firewalld
$ firewall-cmd --add-service=http 
$ firewall-cmd --permanent --add-service=http
````

Restart nginx
````bash
$ sudo service nginx start
````


Configuration
-------
To start using server{} blocks, you must create a conf.d folder and copy the example 
file as seen below.

````bash
# create a folder to store your server configuration file
$ mkdir /etc/nginx/conf.d
# Go to your centopia-master folder and copy the example configuration file. 
$ cp nginx/nginx-1.6.2/utils/my-site.conf /etc/nginx/conf.d/
````