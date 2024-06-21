# Create Security Group

## Security group reference architecture

![Screenshot 2024-06-21 213742](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f0e97b08-d2ec-4042-a709-3a4ecd645ece)


To build a security group, click "create security group," name it "alb security group," and choose our development VPC under vpc. Then, pick "security group" in the VPC dashboard and filter by the development VPC. Click "add rule" under "inbound rules". The initial guideline will be to look for and choose port 80, or http. "source" will be 0.0.0.0/0, denoting traffic coming from any location; choose it. The second rule is to look for and pick https, which is located on port 443. Furthermore, "0.0.0.0/0" will continue to be the "source". Click "create security group" after swiping down.

![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/e114e36f-af39-414d-abe2-ae88a1f1e373)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3a2cb4fd-ecaa-420d-8d68-0d9269787508)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/7e201945-1db4-475c-9692-6a0f9d683f94)

Next we create SSH Security group, using the security group architecture by follwing the same steps.

![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/420d0f2e-0ad4-4939-b15c-e23675acfe2a)
![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/d60cd158-9f4a-4298-b0c9-1788c08a1f39)

Apply the same procedures to create the security groups for the web server, database, and eFS, using the reference architecture for the security group as a guide for the various ports.

Once you're done, view the six (6) security groups—including the default security group—by filtering the security groups using your development virtual PC.

![7](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3284792a-e331-4f98-bf5d-ad15a08ca009)
