 # Create the NAT Gateway

 ## Nat Gateway reference architecture.

![Screenshot 2024-06-21 183143](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/1051b2d4-d68a-43cf-9794-d38d6c0abce4) 

 The NAT gateway enables the EC2 instances in the private subnet to access the internet. 
 The NAT Gateway is an AWS managed service for the NAT instance. <br>
 We are building two NAT gateways, one in public subnet az1 and the other in public subnet az2, in accordance with the architecture. Click "create nat gateways" after selecting "natgateway" in the vpc dashboard. Name it "nat gatway az1" and choose "public subnet az1". Then, scroll down to "elastic ip allocation id" and click "allocate elastic ip". Finally, scroll down and select "create nat gateway."
 
 1
 2
 3

 Next we create the second nat gateway in the public subnet az2. see screenshots below

 4
 5
 
