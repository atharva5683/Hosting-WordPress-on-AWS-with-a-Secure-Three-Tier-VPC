# Hosting WordPress on AWS: A Step-by-Step Guide with a Three-Tier VPC and Database

Amazon Web Services (AWS) WordPress hosting may greatly improve the speed, scalability, and security of your website. We'll walk through configuring WordPress on AWS with a three-tier Virtual Private Cloud (VPC) architecture—a web server layer, an application server tier, and a database tier—in this comprehensive guide. A number of AWS services are used: Route 53, Autoscaling Group, Certificate Manager, EFS, RDS, Application Loadbalancer, Security group, Ec2, and more.

## Why Use a Three-Tier Architecture?

A three-tier architecture offers several advantages:
- **Separation of Concerns**: Each layer has a specific role, improving maintainability and scalability.
- **Improved Security**: Isolating each layer reduces the risk of security breaches.
- **Scalability**: Each layer can be scaled independently based on demand.

# Project Architecture
![ezgif-6-fed214532a (1)](https://github.com/atharva5683/Hosting-WordPress-on-AWS-with-a-Secure-Three-Tier-VPC/assets/160429511/3999131f-8cb8-4eb8-ae56-eca24b2d2ecb)
  
## Architecture Overview

The three-tier architecture consists of:
- **Presentation Tier (Web Tier)**: EC2 instances behind an Application Load Balancer.
- **Application Tier**: PHP processing handled by EC2 instances.
- **Database Tier**: Amazon RDS for the WordPress database.
- **Shared Storage**: EFS for shared file storage across EC2 instances.
- **Domain Management**: Route 53 for DNS.
- **Security and Scaling**: Security Groups, Autoscaling Groups, and NAT Gateway for internet access in private subnets.

## Step-by-Step Guide

### Step 1: Set Up a VPC

1. **Create a VPC**:
   - Navigate to the VPC Dashboard and click “Create VPC”.
   - Name your VPC (e.g., "WordPressVPC") and use the IPv4 CIDR block 10.0.0.0/16.
   - Click “Create VPC”.

2. **Create Subnets**:
   - Create three subnets: Web (Public), Application (Private), and Database (Private).
     - Web Subnet: 10.0.1.0/24 (Public)
     - Application Subnet: 10.0.2.0/24 (Private)
     - Database Subnet: 10.0.3.0/24 (Private)
   
3. **Create and Attach an Internet Gateway**:
   - Navigate to Internet Gateways, click “Create Internet Gateway”, and attach it to your VPC.

4. **Configure Route Tables**:
   - Create a public route table and associate it with the Web Subnet.
   - Add a route to the Internet (0.0.0.0/0) via the Internet Gateway.
   - Create private route tables for the Application and Database subnets and add routes to the NAT Gateway (which will be created later).

### Step 2: Set Up a NAT Gateway

1. **Create a NAT Gateway**:
   - Navigate to NAT Gateways and create a NAT Gateway in the Web Subnet.
   - Allocate an Elastic IP for the NAT Gateway.
   - Update the private route tables to use the NAT Gateway for internet traffic (0.0.0.0/0).

### Step 3: Set Up Security Groups

1. **Create Security Groups**:
   - Web Server Security Group: Allow HTTP (80), HTTPS (443), and SSH (22) from anywhere.
   - Application Server Security Group: Allow traffic from the Web Server Security Group and Database Server Security Group.
   - Database Security Group: Allow MySQL/Aurora traffic (port 3306) from the Application Server Security Group.

### Step 4: Launch EC2 Instances

1. **Launch EC2 Instances**:
   - Create EC2 instances for the Web and Application tiers in the respective subnets.
   - Use the Amazon Linux 2 AMI and t2.micro instance type.
   - Assign appropriate security groups.

### Step 5: Set Up RDS

1. **Create an RDS Instance**:
   - Navigate to RDS, click “Create Database”, choose MySQL, and use the Free Tier option.
   - Place the RDS instance in the Database Subnet.
   - Configure the RDS instance with a database name (e.g., "wordpressdb"), master username, and password.
   - Use the Database Security Group for the RDS instance.

### Step 6: Set Up EFS

1. **Create an EFS File System**:
   - Navigate to EFS, click “Create File System”, and follow the prompts to create a file system.
   - Create mount targets in each of your subnets.

2. **Mount EFS on EC2 Instances**:
   - Install the EFS mount helper on each EC2 instance:
     ```bash
     sudo yum install -y amazon-efs-utils
     ```
   - Mount the EFS file system:
     ```bash
     sudo mkdir /var/www/html
     sudo mount -t efs fs-XXXXXX:/ /var/www/html
     ```

### Step 7: Install and Configure WordPress

1. **Install Apache and PHP**:
   - On the Web and Application EC2 instances:
     ```bash
     sudo yum update -y
     sudo yum install -y httpd
     sudo amazon-linux-extras install php7.4 -y
     sudo yum install -y php php-mysqlnd
     sudo systemctl start httpd
     sudo systemctl enable httpd
     ```

2. **Download and Configure WordPress**:
   - Download and extract WordPress:
     ```bash
     cd /var/www/html
     sudo wget https://wordpress.org/latest.tar.gz
     sudo tar -xzf latest.tar.gz
     sudo mv wordpress/* .
     sudo rm -rf wordpress latest.tar.gz
     ```

3. **Set Permissions**:
   - Set the correct permissions:
     ```bash
     sudo chown -R apache:apache /var/www/html
     sudo chmod -R 755 /var/www/html
     ```

4. **Configure WordPress to Use RDS**:
   - Edit the `wp-config.php` file with database details:
     ```bash
     sudo mv wp-config-sample.php wp-config.php
     sudo nano wp-config.php
     ```
   - Modify the database settings:
     ```php
     define('DB_NAME', 'wordpressdb');
     define('DB_USER', 'your_master_username');
     define('DB_PASSWORD', 'your_master_password');
     define('DB_HOST', 'your_rds_endpoint');
     ```

### Step 8: Set Up Application Load Balancer

1. **Create an Application Load Balancer**:
   - Navigate to the EC2 Dashboard and create an Application Load Balancer.
   - Configure it to distribute traffic across your Web EC2 instances.
   - Set up health checks to monitor instance health.

### Step 9: Set Up Autoscaling Group

1. **Create an Autoscaling Group**:
   - Navigate to EC2 and create a Launch Configuration with the Web Server AMI.
   - Create an Autoscaling Group and attach it to the Application Load Balancer.
   - Configure scaling policies based on traffic load.

### Step 10: Set Up Certificate Manager

1. **Request an SSL Certificate**:
   - Navigate to AWS Certificate Manager and request a public certificate for your domain.

2. **Attach the Certificate to the Load Balancer**:
   - Configure the Application Load Balancer to use the SSL certificate for HTTPS traffic.

### Step 11: Configure Route 53

1. **Register or Transfer Your Domain**:
   - Navigate to Route 53 and register a new domain or transfer an existing domain.

2. **Create a Hosted Zone**:
   - Create a hosted zone for your domain and configure DNS records.

3. **Point Your Domain to Your Load Balancer**:
   - Create an A record in Route 53 pointing to your Application Load Balancer.

### Step 12: Complete the WordPress Installation

1. **Access Your WordPress Site**:
   - Open a web browser and navigate to your domain.
   - Follow the on-screen instructions to complete the WordPress installation.
   - Enter your site title, admin username, password, and email.
