Install Postgres on CentOs7
========================
rpm -Uvh http://yum.postgresql.org/9.4/redhat/rhel-7-x86_64/pgdg-centos94-9.4-1.noarch.rpm
http://www.unixmen.com/postgresql-9-4-released-install-centos-7/

yum update

yum install postgresql94-server postgresql94-contrib

/usr/pgsql-9.4/bin/postgresql94-setup initdb

systemctl enable postgresql-9.4
systemctl start postgresql-9.4
	
firewall-cmd --permanent --add-port=5432/tcp
firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --reload

setsebool -P httpd_can_network_connect_db 1

su - postgres

psql
