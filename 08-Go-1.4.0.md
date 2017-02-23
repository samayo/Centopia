## centopia | the nginx build steps

> This guide shows how to build/install Nginx 1.6.2 from src on CentOS 7  

##### If you want to just run 4 lines of code and be done with it, open & follow the "automation" file. 

Manual Build
-------

Update CentOs to use latest and stable tools
````bash
sudo yum install gcc glibc-devel
wget https://storage.googleapis.com/golang/go1.4.linux-386.tar.gz
 tar xzvf go1.4.linux-386.tar.gz
 cd go/src
 ./all.bash
  cp /usr/local/src/go/bin/go /usr/bin/go
````