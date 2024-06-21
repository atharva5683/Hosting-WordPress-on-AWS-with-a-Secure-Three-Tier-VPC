# Launch the setup server (Ec2 instance)

The ec2 instance that will be used to install WordPress in the public subnet az1 must now be launched. To accomplish that, navigate to the ec2 dashboard by searching for "ec2" in the console. Select "instances running" and click "launch instance". Then, under "name and tag", select "setup server". Scroll down, select "quick start" tab and choose "amazon linux". Scroll down, "under keypair", select your keypair. Next, under "network setting", click "edit" and select our "dev vpc", then select "public subnet az1". Finally, under "firewall", select "existing security group" and use the drop-down menu to select the ssh, alb, and webserver security groups. Select "launch instance" by clicking.

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/6e9feea0-3aa6-4961-ac65-d24dbe26114c)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/30cf873a-b003-45d1-bd41-32f02ea6c825)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/77a92538-6068-4660-adbc-23349c211eea)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/514303ab-406d-42c2-a47b-2414fcee7043)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/40f7a45f-0c48-47d7-9037-5db9873fbf43)
