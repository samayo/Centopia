Install NodeJS v4.1.0
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
$ wget http://nodejs.org/dist/v4.1.0/node-v4.1.0.tar.gz
$ tar zxf node-v4.1.0.tar.gz
$ cd node-v4.1.0
```

#### Configure and install
```
$ ./configure --prefix=/usr/local
$ make 
$ make install 

# check version to make sure it was installed
$ node -v  
```
