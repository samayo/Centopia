Install Python on CentOs7
========================
> NOTE: install guide not finished
```
yum -y install scl-utils
rpm -Uvh https://www.softwarecollections.org/en/scls/rhscl/python33/epel-7-x86_64/download/rhscl-python33-epel-7-x86_64.noarch.rpm
yum -y install python33
scl enable python33 bash
python -V
easy_install pip
#pip install PyMySQL
yum install mysql-devel
sudo yum install MySQL-python
pip install mysqlclient

#### VIA RMP
```
sudo yum install epel-release
yum install python34
wget https://bootstrap.pypa.io/get-pip.py
python3.4 get-pip.py
```
 
