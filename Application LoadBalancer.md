# Create Application Loadbalancer

Using our reference architecture as a guide, build an application load balancer to direct traffic to the EC2 instances in the private app subnets.

Launch ec2 instances in each of the private app subnets before building the application loadbalancer. Continue with the previous steps to create an instance.

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/4bdaa5cd-0fba-4c51-ae27-ea343a8c1d88)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/68e41fb6-0038-4763-98b6-0c1354fe8622)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/bcaa3175-250e-49c5-9967-fdc27937d746)

Make sure to update the efs mount information by scrolling down and expanding "advance details" and then scrolling down to "user data" and pasting the command below in the box. This is the same command used to install WordPress.

```bash
#!/bin/bash
yum update -y
sudo yum install -y httpd httpd-tools mod_ssl
sudo systemctl enable httpd 
sudo systemctl start httpd
sudo amazon-linux-extras enable php7.4
sudo yum clean metadata
sudo yum install php php-common php-pear -y
sudo yum install php-{cgi,curl,mbstring,gd,mysqlnd,gettext,json,xml,fpm,intl,zip} -y
sudo rpm -Uvh https://dev.mysql.com/get/mysql57-community-release-el7-11.noarch.rpm
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
sudo yum install mysql-community-server -y
sudo systemctl enable mysqld
sudo systemctl start mysqld
echo "fs-03c9b3354880b36a6.efs.us-east-1.amazonaws.com:/ /var/www/html nfs4 nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2 0 0" >> /etc/fstab
mount -a
chown apache:apache -R /var/www/html
sudo service httpd restart
```

![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/d89e6230-3049-4f96-864e-20188431c018)

This command makes it easier for the EC2 to install all of its dependencies automatically, saving you the trouble of doing it by hand. "Click launch instance" after completion.
To start the second EC2 instance in the private app subnet AZ2, proceed in the same manner.

After that, view your instances by going to your EC2 dashboard.

![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/4a688847-daff-46d9-afde-df02de9147b8)
![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/214e1d06-2869-4104-add5-ab2257f9c116)


Select target groups in the left side of the ec2 management console and click create "target group". see screenshots below for instructions.

![7](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/32ff2821-b7f2-49ae-af2d-0fe4f805f079)
![8](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/181a3db1-31b5-441b-9bb9-96be35e93846)
![9](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/94a95e23-1276-49dc-8551-796ae1e221b4)

We can now go on and create the application loadbalancer, see screenshots below for instructions

![10](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3850946c-b5ea-4fa4-91cd-da1bf77a2cbf)
![11](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/d3568ce8-93a4-4790-86e0-5eabd80b8a74)
![12](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/eb98987c-8a14-436d-a7a8-0ff42eb18815)
![13](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/40cf9888-7cc6-4801-99c7-886546dd80e3)
![14](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/6c79343b-1d9f-4682-a317-a464b9fd8d6b)
![15](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/fa6f4f33-2ad0-4b85-8e81-01ec65e484a4)
![16](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/0bba7188-3876-4258-992f-0e8be59970f2)

Once the loadbalancer's status changes to active, copy its DNS address, put it into your browser, and hit the enter key. The loadbalancer has now been successfully created.

![17](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/21c5c3be-bc44-4936-a003-6ed22d9001ea)

With the application loadbalancer's DNS name, we can now access our website.

You must enter your WordPress domain settings and make the necessary changes each time you update your domain address. First, copy your domain name (the WordPress URL) to accomplish this.

![18](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/a3bbbe77-1d32-4176-9881-af60f5ad2980)

Then add "/wp-admin" to the end of it, press enter, this will prompt you to login, enter your details and you will be taking to the wordpress dashboard.

![19](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f6e77440-bab5-4916-89ff-e599f0b52ae4)

Once in, click "settings" and the "general", then update the "wordpress address" and "site address" by pasting in the url you copied earlier, ensure to remove the forward slash at the end. Then scroll down and click "save changes".

![20](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/09a47748-96fa-45b0-883d-cd21ea3ab218)
![21](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3f7b62bc-2d81-4381-a50c-fd52089dc9f7)

Once you hit "save changes, you will be prompted to log back in, do that,

![22](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/bad409c5-bd71-4b85-baf6-d4419055715c)

Consequently, the WordPress domain URL has been correctly adjusted.

We can now visit the WordPress website using our application balancer DNS as we have started two instances on the private app subnets. With this information, we can go into the console and end the initial setup server.

![23](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/7d0f3904-b0aa-4d20-ae2a-71aa764779c6)

