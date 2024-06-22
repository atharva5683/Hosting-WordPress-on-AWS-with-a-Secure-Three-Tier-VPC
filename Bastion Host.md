# Create Bastion Host

The next step is to SSH into the instance in the private subnet. However, before we can do that, we must first start an instance in the public subnet. We will SSH into this instance, which is named Bastion Host. Once we are in the public subnet, we can SSH into the instance in the private subnet.

To launch an instance in the public subnet, use precisely the same action as previously. View the screenshots that follow.

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/7f7dfdf1-6ecd-43a9-9d27-8b728affcb5c)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/b42688a5-b1e1-426c-a4c7-e47bc983d96c)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/b0ba249a-9ee7-48e3-8f26-bcbb4f1a5254)

Then go to your ec2 dashboard to see all instances.

![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f8c7d7f9-af75-4e80-94ed-d3aae54c4e1e)

Copy the ipv4 public address of the bastion host and ssh into it, once that is done, type the command "ssh ec2-user@private ip address of any of the webserver"

![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/c3c0252f-2973-4b59-8f59-90affac2cbba)
![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/bf0acfa6-ff18-49f8-b8ad-e5b4c2d15ded)

The fact that our machine's IP address matches the private IP of our web server instance, if you look closely, indicates that we were able to successfully shell into the instance on the private subnet.
