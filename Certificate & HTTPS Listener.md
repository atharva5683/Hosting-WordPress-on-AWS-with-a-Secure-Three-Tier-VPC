# Register using AWS Certificate Manager to obtain an SSL certificate.

All communication between the web browser and our web servers is encrypted thanks to the certificate manager.

Go to the certificate manager dashboard in the console and follow the instructions shown in the screenshots below to create a free certificate.

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/c6d13392-909c-4c10-8465-f5a195fdf5b5)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/0952a4d5-65dc-4f0a-9b84-7775c56f52f2)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/d43ddbb4-c805-4e62-99ba-7d8a3cd5122e)
![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/48724ad3-531e-471c-a1ea-5e5a1efcc5ce)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/d1abcf8a-74dd-4630-8c74-8b58a5e8d8bd)

Our request for a certificate was sent successfully; however, it is still pending validation via route 53. To accomplish that, navigate to the "create a record" page and adhere to the screenshots' directions.

![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/d8acbf95-128a-441f-967d-f041326d5849)
![7](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/b580bb8e-4159-4f2b-92b4-17f49c873fbe)
![8](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/fddc4039-9b22-4b55-8466-b7877f6e6d4d)

Checking the status now indicates that it has been "issued" and that our two names are now in "success" state.

# Create a HTTPS Listener

Next, by setting up a https listener in the loadbalancer dashboard, we will use the SSL certificate to protect all interactions with our website.

Observe the guidelines provided in the screenshots.

![9](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/40f29a80-9ab0-4c89-a657-d5087e24572f)
![10](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/f439296f-52b1-40aa-a498-82337a7d5eca)
![11](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/8523976e-7995-4e24-9805-36a5821d8f75)
![12](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/afee814e-91c6-4d9e-a105-db59a23b451e)

The HTTPS listener has been created, next thing is to modify our HTTP Listener to redirect traffic to HTTPS. See screenshots below for instruction.

![13](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/2f593536-e917-4376-9f1f-8e900c7d665a)
![14](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3b96e4c1-8af7-4743-bf03-293b82bca8c0)
![15](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/c318f2a4-e294-4cfb-9cac-c2a9a19624d6)

Now you can check to see if you can access the website. Go to your browser and type in your domain name starting with "https//www.domain name".

![16](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/a99357d7-b3c6-4824-be1a-263f4c930b7a)
