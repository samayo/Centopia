Install gitlab on CentOs7
==========================

# install things, open things
sudo yum install openssh-server
sudo systemctl enable sshd
sudo systemctl start sshd
sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix
sudo firewall-cmd --permanent --add-service=http
sudo systemctl reload firewalld

# Download the Omnibus package and install everything
curl -O https://downloads-packages.s3.amazonaws.com/centos-7.1.1503/gitlab-ce-7.10.0~omnibus.2-1.x86_64.rpm
sudo rpm -i gitlab-ce-7.10.0~omnibus.2-1.x86_64.rpm

# Configure and start GitLab
sudo gitlab-ctl reconfigure

// localhost 