## centopia | the node.js install guide

> This guide shows how the centopia bash script builds latest Ghost platform from src on CentOS 7
> which means you can follow this guide to install Ghost yourself.  

##### If you don!t want to do this manually, check the "centopia way" at the end of this page. 

Manual Build
-------

Update CentOs to use latest and stable tools
````bash
$ yum -y update
````

Install the tools that are required to run build / run Node.js
````bash
$ yum -y install gcc-c++ openssl-devel 
````

Download nodejs and extract the source file
````bash
$ cd /usr/local/src && wget -O node-latest.tar.gz http://nodejs.org/dist/node-latest.tar.gz 
$ tar -xzf node-latest.tar.gz 
$ cd node-v* # example:  cd node-v0.10.33/
````

Configure and Install
````bash
./configure
make && make install
````

Just copy node/npm service scripts or create symlinks
````bash
cp /usr/local/bin/node /usr/bin/node
cp /usr/local/bin/npm  /usr/bin/npm
````

mkdir  -p /var/www/ && cd /var/www/
curl -L -O https://ghost.org/zip/ghost-latest.zip
unzip -d ghost ghost-latest.zip
cd ghost
useradd ghost
chown -R ghost:ghost /var/www/ghost/
npm install --production
npm start --production
Il est accessible à l'adresse suivante http://monIPdeServeur:2368
 

 
On créé un fichier de configuration et on l'édite
vi /etc/nginx/conf.d/ghost.conf

server {
listen 80;
server_name mondomaine.fr;
error_log  /var/log/nginx/blog_ghost-error.log warn;
access_log /var/log/nginx/blog_ghost-access.log;

location / {
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header Host $http_host;
proxy_set_header X-NginX-Proxy true;

proxy_pass http://127.0.0.1:2368;
proxy_redirect off;
}
}

On redémarre le service nginx
systemctl restart nginx

On relance le service ghost
npm start --production

Vous pouvez désormais accéder à votre site avec votre nom de domaine.

Voilà l'installation de base est terminée.

Dans un prochain article, nous verrons comment automatiser le démarrage du service Ghost avec supervisor.

Source 


