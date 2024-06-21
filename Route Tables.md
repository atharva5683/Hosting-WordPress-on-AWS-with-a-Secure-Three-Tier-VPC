# Create Two Route Tables

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
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/8adff94c-4e6b-45b0-8a8c-3f7388690207)
![12](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/00b01468-4e59-4b7f-acab-b98d29fb205c)
![13](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/130e4e60-0f71-4696-a84f-4bc9b87f3895)
![14](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/c07f0fd1-e557-441e-ab09-7ccc20f1982d)

Next associte this route table with "private app subnet az1" and "private data subnet az1" following the nat gateway reference architecture.

Like before select the "subnet associations" tab and then click "edit subnet associations". Under "available subnets", select private app subnet az1 and private data subnet az1 respectively and click "save associations".
![15](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/50fb2903-43cc-4e19-bd8b-ee5fb2aad611)
![16](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3dba05e2-7ccd-41f0-8e72-6486b477700c)
![17](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f55906ce-a6cc-4552-9268-a05ec5adf012)

### For private route table az2

[5 2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/9d123d3b-c4e9-4c88-ae51-61979f99353c)

Next step add a route to the private route table az2 to route traffic to the internet through the nat gateway in the public subnet az2. Follow the steps we use in creating the previous one.
![18](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f2967cc0-c848-4160-85f3-1cb280c2d9dd)
![19](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/36275220-5690-4efd-907b-89a6941a36be)


Next step associate this route table with private app subnet az2 and private data subnet az2, like before, follow the previous steps.
![20](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/cdbc174f-d197-4a2f-92ae-52b241d3a057)
![21](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/0bb15425-f31c-4cb6-bc78-cd04c8dd8b54)
