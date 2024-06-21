# Create  Route Tables

Route tables is a set of rule that determines how data moves within our network. We need two route tables; private route table and public route table. The public route table will define which subnets that will have direct access to the internet ( ie public subnets) while the private route table will define which subnet goes through the NAT gateway (ie private subnet).

To create route tables, navigate over to the Route Tables page and click on Create route table button.
![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/66f0a16d-fe9b-43c7-9d14-a12012d66b13)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/b17664c4-fda3-4c3f-8d86-56c098db16cf)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/a553a2f4-5aef-4e43-86bf-8e232ac53fcd)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/68ff068b-3ea4-490a-933c-493c73c711e7)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/8adff94c-4e6b-45b0-8a8c-3f7388690207)
![5 1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/c37977d2-ebdc-4a88-97dd-5c743bfb9918)
![5 2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/9d123d3b-c4e9-4c88-ae51-61979f99353c)

## Next step Add public route to the route table
The route aalows the public route table to route traffic to the internet.

To do this, make sure you are on the route tab, then click "edit routes", then click "add route", under "destination", type in "0.0.0.0/0" in the box. After that, under "target", select "internet gateway", then click "save changes"
Tier-VPC/assets/160429511/17972966-6f3f-4936-8949-3e878be6b64f)
![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/83dacd0b-ff8b-46ca-af75-3444baa0e8e3)
![7](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/86dbf6bd-5893-4a1b-a36c-9f0883a4a1e0)
![8](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/319f511e-2bd2-4978-814c-71e2cd8af9be)

## Next step, associate the two public subnet to the route table
To this, select the "subnet association" tab, then click "edit subnet association", once in the next page, select the two subnet that you see and hit "save aasociation".
![9](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/34a76a4f-c510-4e7f-b346-e20ed03ef6a8)
![10](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/2869620c-d546-4592-b67f-595545460b72)
![11](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/b8c7c7ec-2415-45ea-8c7d-04869d2798b2)

## Next we add route to the the private route table

Next we add route to the the private route table az1 to route traffic to the internet through the nat gateway in the public subnet az1

To this, like before, select the "route" tab and click "edit route", click "add route", under "destination", type "0.0.0.0/0 and click it. under "local" select our nat gateway az1 in the public subnet and hit "save changes".
