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


## Create Subnets.
The subnet is a way for us to group our resources within the VPC with their IP range. A subnet can be public or private. EC2 instances within a public subnet have public IPs and can directly access the internet while those in the private subnet does not have public IPs and can only access the internet through a NAT gateway.

For our setup, we shall be creating the following subnets with the corresponding IP ranges.

public-subnet-1 | CIDR (10.0.0.0/24) | Availability Zone (us-east-1a) <br>
public-subnet-2 | CIDR (10.0.1.0/24) | Availability Zone (us-east-1b) <br>
private-subnet-1 | CIDR (10.0.2.0/24) | Availability Zone (us-east-1a) <br>
private-subnet-2 | CIDR(10.0.3.0/24) | Availability Zone (us-east-1b) <br>
private-subnet-3 | CIDR (10.0.4.0/24) | Availability Zone (us-east-1a) <br>
private-subnet-4 | CIDR(10.0.5.0/24) | Availability Zone (us-east-1b) <br>

### Public Subnets
![8](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f420b304-a083-4fbb-a6e5-1988dc2c2e8e)
![9](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/89cb0360-5aca-4fea-9263-93e8a4b7bf7d)
![10](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/e745e125-bb58-406b-8486-6ebf39fe84c6)

To create our second subnet, just follow the same steps as for the first one: choose "us-east-1b" for availability zones and name it "public subnet AZ2" under "subnet name". Enter "10.0.0.1.0/24" under the IPv4 Cidr bock, scroll down, and select "Create subnets." Use the generated VPC as a filter to view the two subnets.

![11](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f9444c4a-9218-45b3-a4e6-ec619dc810e7)
![12](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/9937877c-0da9-4042-a383-1a6d9c6a6987)
![13](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/35fdcd63-2ff9-4a38-b8f4-746cb6f348db)
### enable auto-assign ip for the subnet

To accomplish this, choose the first subnet, click "action," "edit subnets settings," activate "auto-assign public ipv4 address" under "auto-assign ip setting," scroll down, and click "save."

![14](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/ddf84289-dfce-4988-ae7a-e47db5cf42d6)
![15](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/a6167166-f3b8-4c03-8b64-34e1f61f90ec)
![16](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f813a11c-af3b-470c-b534-77cc4d12ca5b)

Repeat the same step for the second subnet.
## Private subnet.
We will design 4 private subnets in accordance with our vpc reference architecture. Click "create subnets" after selecting "subnets" on the left side of your VPC dashboard. Make sure you only see the two public subnets that were previously formed by filtering by the Dev vpc that was built earlier.
![17](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/1f40ec1d-c8f0-4cd4-b1d4-0f7a4e0731df)

Do the same for the remaining three(3) subnets by following the VPC reference architecture, see screenshots below.

![18](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/5da64575-7ada-4837-965d-678aa48b8532)
![19](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/6615e713-eb5f-452c-81cd-45619a7e19cc)
![20](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/4b40e532-4870-4538-8c0d-d62f25098da7)

TO see all the subnets(6), filter by the dev vpc.

![21](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/a60173a7-63b4-42e0-a8fb-8d7fd4b229bb)
