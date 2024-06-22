# Create a Record Set in Route 53

To view the website with our domain, establish a record set in route 53.

Enter route 53 into the console, choose it under services, and then click on "hosted zone" to select your domain. On the next page, click "create record" and type "www" under "record name". Then, toggle on the "alias" feature. Scroll down and select the drop-down menu, then choose "alias to application and classic loadbalancer," then select "us-east-1." Finally, select the drop-down menu to select the application loadbalancer that was created. Next, select "create record"

![1](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/7430888a-6c6c-4c81-bd58-a6c16b48d8a2)
![2](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/bc6a515e-1ea4-41c5-9be7-e4cfdcc2e9b3)
![3](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/0f4680cb-b552-4a43-9b65-4cab7a99fb63)

The record set has now been generated. To visit our website, copy the record name, paste it into your browser, and hit the enter key.

![4](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/0b028e66-226a-479e-913e-40b6c4392f1a)
![5](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/c2b3c59d-29d2-490f-ad0f-b4f8b824973e)

With our domain name, we can now access the WordPress website.

Remember that if our domain name changes, we also need to update the WordPress domain name settings. If you follow the same steps as before, you should have the result displayed in the screenshot below, which indicates that our domain name is now our WordPress website url.

![6](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/1df24358-8ac7-4bfd-bfed-f31aabb972e3)
