# Create VPC with Public and Private Subnets

We will construct a custom VPC to begin the project; the three-tiered enabled reference architecture for the VPC is shown below.
A public subnet housing a NAT gateway, bastion host, and loadbalancer is found in the first tier of a three-tier virtual private cloud reference architecture. The web servers (EC2 instances) are housed in a private subnet on the second tier, while the database is contained in a private subnet on the third tier. To offer high availability and fault tolerance, all of these subnets are replicated across various availability zones. Lastly, we will build an internet gateway and route table, which will enable the vpc's resources to be connected to the internet.

## VPC Reference Architecture
1
To create the VPC, go to the AWS console a type vpc in the search box and select vpc. In the VPC dashboard, select VPC, then click create VPC. Name the VPC "Dev VPC". In the IPv4 cidr block space, type "10.0.0.0/16". Leave everything as default and scroll down and click create vpc.

2
3
4
5

### Next step is to eneble DNS hostname in the vpc
To do that, select "action" and then edit "vpc setting". In the next page that opens, check the enable "DNS hostname" box and scroll down and hit save button.
6
7

### Create Subnets.
Subnets in the first and second availability zones must be created in accordance with the VPC Reference Architecture as the next step. Click "create subnets" after selecting "subnet" on the vpc dashboard to accomplish this. The "public subnet AZ1" is what our reference architecture calls it when you select our "Dev VPC" under "vpc id" and scroll down to the "subnet name" field. Choose "us-east-1a" under "availability zone". Enter "10.0.0.0/24" under the IPv4 Cidr block. After swiping down, select "create subnets"


