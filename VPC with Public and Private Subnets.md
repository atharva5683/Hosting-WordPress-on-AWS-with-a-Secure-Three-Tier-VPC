# Create VPC with Public and Private Subnets

We will construct a custom VPC to begin the project; the three-tiered enabled reference architecture for the VPC is shown below.
A public subnet housing a NAT gateway, bastion host, and loadbalancer is found in the first tier of a three-tier virtual private cloud reference architecture. The web servers (EC2 instances) are housed in a private subnet on the second tier, while the database is contained in a private subnet on the third tier. To offer high availability and fault tolerance, all of these subnets are replicated across various availability zones. Lastly, we will build an internet gateway and route table, which will enable the vpc's resources to be connected to the internet.

## VPC Reference Architecture
![Screenshot 2024-06-21 145910](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/1dd24eb1-8c98-4d8f-be7b-a77a871631cb)

To create the VPC, go to the AWS console a type vpc in the search box and select vpc. In the VPC dashboard, select VPC, then click create VPC. Name the VPC "Dev VPC". In the IPv4 cidr block space, type "10.0.0.0/16". Leave everything as default and scroll down and click create vpc.

![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/364fc278-a00f-4691-b687-f5f7dcf3a7cc)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/08d56ca8-8d3a-4589-8c58-641c606e5fb7)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/e1e54f10-ae1c-4bb4-997d-7ec507f38e38)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/cc197c54-65f8-405a-a923-0aed46e9be06)


### Next step is to eneble DNS hostname in the vpc
To do that, select "action" and then edit "vpc setting". In the next page that opens, check the enable "DNS hostname" box and scroll down and hit save button.
![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/215dbe87-e9bb-4767-b5bb-165d22b81ef0)
![7](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/5fd5beee-23d0-40d1-8603-ba6f8d9b83b5)


### Create Subnets.
Create 4 Subnets: The subnet is a way for us to group our resources within the VPC with their IP range. A subnet can be public or private. EC2 instances within a public subnet have public IPs and can directly access the internet while those in the private subnet does not have public IPs and can only access the internet through a NAT gateway.

For our setup, we shall be creating the following subnets with the corresponding IP ranges.

demo-public-subnet-1 | CIDR (10.0.1.0/24) | Availability Zone (us-east-1a)
demo-public-subnet-2 | CIDR (10.0.2.0/24) | Availability Zone (us-east-1b)
demo-private-subnet-3 | CIDR (10.0.3.0/24) | Availability Zone (us-east-1a)
demo-private-subnet-4 | CIDR(10.0.4.0/24) | Availability Zone (us-east-1b)


