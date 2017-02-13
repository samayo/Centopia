Install Node.js 0.10.30
----

#### update yum & install required libraries
```
$ yum -y update
$ yum install yum-utils bzip2 bzip2-devel wget curl tar
$ yum install sudo gcc-c++
```
#### Download and unpack the source
```
$ cd /usr/local/src
$ wget http://nodejs.org/dist/v0.10.30/node-v0.10.30.tar.gz
$ tar zxf node-v0.10.30.tar.gz
$ cd node-v0.10.30
```

#### Configure and install
```
$ ./configure --prefix=/usr/local
$ make 
$ make install 
