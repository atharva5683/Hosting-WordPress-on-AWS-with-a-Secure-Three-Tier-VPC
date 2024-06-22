# Create an Auto Scaling Group

To dynamically generate and scale the webservers in the private app subnets, we must set up an autoscaling group.

First, terminate the two manually established web servers before creating the autoscaling groups.

Let's get started by creating a launch template. To do this, simply follow the instructions in the photos below. To launch additional instances, the autoscaling group will use the launch template, which provides configuration about our instance.

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/59cfd99f-f2f3-49d3-8275-600443e6c834)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/afe3bad6-a3e2-414b-b754-1201b8d09d05)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/c3f849a7-d16a-452f-9d21-25f2a78a591e)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/69298ffd-dbb6-4bb3-8c51-ecb98afc2211)

Click "create launch template" after expanding the advance details tab, scrolling down to the user data box, and pasting the previous command we used to configure our ec2. Make sure to edit the efs mount information.

![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/d53804a9-16bb-423b-b401-811b1a4cefba)

Now go ahead and create our autoscaling group,

![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3c842c0d-df34-4527-8827-ea23a4638e04)
![7](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/42de8b91-ef3b-42c0-b93c-69ee85e3e887)
![8](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/5500a83d-11c3-44f6-9f2b-fb1def2e547e)
![9](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/da8b79ca-243b-435d-ab5e-6bcfcaf45b63)
![10](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/004dddd6-33d9-4263-bbc4-7feed198f707)
![11](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/6a486bd4-3058-494c-8733-e6090991e962)
![12](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/e89cbcba-3685-493f-9a3a-41f1bb80d424)
![13](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/9c4bf78e-0e8b-4b25-bebb-cd5bdeeba501)
![14](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/fb784686-d135-4d46-b200-59c962593d46)
![15](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/ada1a399-4f0a-465d-b920-2f0c05efe617)

Now go to the ec2 dashboard to see the two new instances created by our autoscaling group.

![16](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/5bc6ed66-8cf0-45b2-9fbb-a6adb31fe38b)
