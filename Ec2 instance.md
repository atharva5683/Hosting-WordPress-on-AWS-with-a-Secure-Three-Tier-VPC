# Launch the setup server (Ec2 instance)

The ec2 instance that will be used to install WordPress in the public subnet az1 must now be launched. To accomplish that, navigate to the ec2 dashboard by searching for "ec2" in the console. Select "instances running" and click "launch instance". Then, under "name and tag", select "setup server". Scroll down, select "quick start" tab and choose "amazon linux". Scroll down, "under keypair", select your keypair. Next, under "network setting", click "edit" and select our "dev vpc", then select "public subnet az1". Finally, under "firewall", select "existing security group" and use the drop-down menu to select the ssh, alb, and webserver security groups. Select "launch instance" by clicking.

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/6e9feea0-3aa6-4961-ac65-d24dbe26114c)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/30cf873a-b003-45d1-bd41-32f02ea6c825)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/77a92538-6068-4660-adbc-23349c211eea)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/514303ab-406d-42c2-a47b-2414fcee7043)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/40f7a45f-0c48-47d7-9037-5db9873fbf43)


# SSH INTO THE SERVER

Next step is to ssh into the server created

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/2cfacd18-cddb-48e0-b448-4d6b576f7bfc)


After logging in to the server, use the following commands to install WordPress and transfer the files to efs. Each command has an explanation at the end explaining what it does.

Remember to update the mount information in the first command before executing the instructions. To do this, go back to the efs you created, copy the mount information, and then return to the code to edit it.

## Install and Configure WordPress

1.
**create the html directory and mount the efs to it**
```bash
sudo su
yum update -y
mkdir -p /var/www/html
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-aed8ad5b.efs.us-east-1.amazonaws.com:/ /var/www/html
```

3.
**install apache **
```bash
sudo yum install -y httpd httpd-tools mod_ssl
sudo systemctl enable httpd 
sudo systemctl start httpd
```

3
**install php 7.4**
```bash
sudo amazon-linux-extras enable php7.4
sudo yum clean metadata
sudo yum install php php-common php-pear -y
sudo yum install php-{cgi,curl,mbstring,gd,mysqlnd,gettext,json,xml,fpm,intl,zip} -y
```

4
**install mysql5.7**
```bash
sudo rpm -Uvh https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
sudo yum install mysql-community-server -y
sudo systemctl enable mysqld
sudo systemctl start mysqld
```

5
**set permissions**
```bash
sudo usermod -a -G apache ec2-user
sudo chown -R ec2-user:apache /var/www
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
sudo find /var/www -type f -exec sudo chmod 0664 {} \;
chown apache:apache -R /var/www/html 
```

6.
**download wordpress files**
```bash
wget https://wordpress.org/latest.tar.gz
tar -xzf latest.tar.gz
cp -r wordpress/* /var/www/html/
```

7.
**create the wp-config.php file**
```bash
cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
```

8.
**edit the wp-config.php file**
```bash
nano /var/www/html/wp-config.php
```
9.
**restart the webserver**
```bash
service httpd restart
```

Once all of the scripts have been executed, copy the server's IPv4 public address (ec2) and paste it into your browser. If you enter it, your browser will launch the WordPress website.

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/aa65ecf9-838a-4932-9d71-f0a478680570)

Enter your information and click "install wordpress".

![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/9a0fd008-9562-451a-8ee4-819739b1e29e)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/44bf3f1e-07dc-46b8-a16f-acb0c1f1c5fc)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/ade115c5-26cc-4f6c-922b-509486a31d4e)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/e72eae53-75ee-4755-b506-03e66a9b625e)
![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/7ca60848-fac0-43fe-ba70-e09e23280f50)
