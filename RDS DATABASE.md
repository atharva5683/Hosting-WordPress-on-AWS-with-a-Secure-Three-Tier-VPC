# Create RDS DATABASE

## RDS database architecture

![Screenshot 2024-06-21 215441](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/392694c3-0e94-4cbd-81c6-a7f6a2bc02a4)

In the management console, type "rds" and choose "rds" under "services" to create a rds database.

Once in the rds dashboard, choose "create db subnet group" after selecting "subnet groups" as our first step. Rename the subnets database using the same name as the "description". Next, choose the "dev" VPC under "vpc", scroll down and choose "us-east-1a" and "us-east-1b" under "add subnet". Next, under "subnets", choose the private data subnets with cidr block "10.0.5.0/24" and "10.0.4.0/24". Finally, scroll down and click "create".

![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/154bcbf2-5cf2-40c4-85ae-c74b4f5b23b7)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/63fa9b05-5ef6-4cdc-b84c-04dc045e3445)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/67088d58-56c4-4306-81ac-603b8c73625e)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/21f7cddf-6978-493f-92d2-3c4cb6d42dc3)

After that, pick "database" and press "create database." pick "standard create" under "choose a database creation method," "mysql" under "engine type," and the most recent version of MySQL 5.7 under "version." Under "template," scroll down and choose "dev/test." Then, under "db instance identifier," fill in the name "dev-rds-db." Lastly, under "credential settings," enter your login and password, then repeat it. Choose "bustable classes" under "db instance class" by scrolling down and toggling the preceding instance classes. Scroll down and pick the development VPC under connectivity (vpc), then choose the newly formed subnet group under "subnet group" Move down and click "choose existing" under "vpc security group". Then, in the search box, remove the default and choose "database security group",Choose "us-east-1b" under "availability zone". Navigate all the way down and select "create database" after expanding "additional configuration" and typing "applicationdb" under database name. The rds instance typically takes a few minutes to create.

![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/59917f84-b0a1-41b1-8ca1-f858a7964748)
![7](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/b71cefd0-08c5-473c-a4a5-4dc06ceebab6)
![8](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/ae171eee-3b4c-4302-a9e3-4b1c303cb118)
![9](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/cd62902b-5368-46c7-958e-c66227946a6c)
![10](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/04bc3a77-ff67-40af-afd2-9e67ed0ad13e)
![11](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/ae07647e-ad71-431e-84b0-e679908aad3f)
![12](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/a701be40-5f03-4286-8982-0af184253cfb)
![13](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/e158d05d-f6cd-481b-bb87-38505c3be032)
![14](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/ba6b676f-7ce9-451e-94ec-a2ecd65371c7)

