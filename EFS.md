# Create EFS

## EFS Architecture

![Screenshot 2024-06-21 220105](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/0016590d-8698-4720-8328-d5a565060b4d)

In each availability zone, construct an Elastic File System (EFS) with a mount target in the private data saubnet. The application code and configuration files can be pulled from the same location by the webservers within the private app subnet thanks to the EFS.

In your console, type EFS into the search box, choose EFS under services, click "create file system," and then click "customize." Name it "Def-Efs," scroll down, uncheck the "encryption" box, and leave everything else as it is. Name the tag "dev-efs," then click "next." Next, under "vpc" in the network, choose "dev vpc." Next, under "availability zone" in the mount target, choose, respectively, US-east-1a and US-east-1b. Finally, select the EFS security group for both, under "security," and move to the left. 

![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/a072736f-122b-462b-83ac-0ff57d8d937a)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3e8749d8-fa1f-47b2-8055-dbcd6f6f1ded)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/8a9c3395-9b22-4b2d-9b87-0d4781450cfd)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/dd8bd684-34c1-4e3d-802f-8e8784106433)
![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/9e2c5b20-efe8-4253-920d-8b3f1932b258)

