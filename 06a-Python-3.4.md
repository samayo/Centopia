Install Python 3.4
----

#### update yum & install required libraries
```
$ yum -y update
$ yum install gcc openssl-devel
```

#### Download and unpack the source
```
$ wget https://www.python.org/ftp/python/3.4.3/Python-3.4.3.tar.xz
$ tar xf Python-3.* 
$ cd Python-3.*
```

#### Configure and install
Note: It is important to use `make altinstall` instead of `make install` if don't want to endup with two versions of Python in your system
which might cause you problems since most libraries still use 2.7      
```
$ ./configure --prefix=/opt/python3
$ make
$ make altinstall # or make install
```

### Check version and copy to usr/bin
check if python 3.4 is installed correctly
```
$ ./python -V
```
if all is good, include it in usr/bin to access it globaly
```
cp python /usr/bin/python3
```




