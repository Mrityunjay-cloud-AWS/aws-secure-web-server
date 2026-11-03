# CloudLab - Secure AWS Web Server

## About the Project

CloudLab is a hands-on AWS project I built to understand how websites are hosted on AWS and how different AWS services work together.

I started by launching an EC2 instance with Amazon Linux 2023 and installing Apache to host a website. After getting the website running, I created a private S3 bucket to store a configuration file and used an IAM role to allow the EC2 instance to access it securely.

I also used Git and GitHub to manage the project files and created a Bash script to make website deployment easier.

Through this project, I got practical experience with Linux, AWS networking, IAM, S3, and basic deployment automation.

## Architecture

Developer Laptop
|
| Git Push
v
GitHub Repository
|
| Git Pull
v
EC2 Instance (Amazon Linux 2023)
|
+---- Apache HTTP Server
|          |
|          v
|      Website Visitors
|
+---- IAM Role
|
v
IAM Policy
|
v
Private S3 Bucket
config.json

## AWS Services Used

### 1. Amazon EC2

I launched an EC2 instance using Amazon Linux 2023 and installed Apache to host my website.

### 2. Amazon VPC and Security Groups

I used Security Groups to control access to the EC2 instance. SSH access was restricted to my public IP, while HTTP access was allowed so visitors could open the website.

### 3. AWS IAM

I created an IAM role and attached it to my EC2 instance. Instead of storing AWS access keys on the server, I used the role to provide temporary credentials.

I also created a custom IAM policy that allows the instance to read a specific configuration file from S3.

### 4. Amazon S3

I created a private S3 bucket and uploaded a config.json file. Public access was blocked, and the EC2 instance accessed the file through its IAM role.

### 5. AWS CLI

I used the AWS CLI from the EC2 terminal to check the active AWS identity and download the configuration file from S3.

## Tools and Technologies

* Amazon EC2
* Amazon S3
* AWS IAM
* Amazon VPC
* Amazon Linux 2023
* Apache HTTP Server
* AWS CLI
* Linux and Bash scripting
* Git and GitHub
* HTML and CSS

## Security Configurations

Security was one of the main things I focused on while building this project.

The following configurations were implemented:

* Restricted SSH access to my public IP address.
* Allowed HTTP traffic for public website access.
* Kept the S3 bucket private with Block Public Access enabled.
* Used an IAM role instead of storing permanent AWS access keys on EC2.
* Created a custom IAM policy with access limited to a specific S3 object.
* Added private key and environment files to .gitignore to avoid accidentally committing sensitive files.

## Website Deployment

I stored the website code in GitHub and cloned the repository onto my EC2 instance.

The website files were copied to Apache's document root at /var/www/html/.

I also created a Bash script called deploy.sh to simplify the deployment process.

The script performs the following tasks:

1. Pulls the latest code from the GitHub main branch.
2. Copies the updated HTML file to Apache's document root.
3. Checks the Apache configuration.
4. Reloads the Apache service.
5. Checks whether the website is responding locally.

This gave me practical experience with automating repetitive deployment tasks using shell scripting.

## What I Learned

While working on this project, I got hands-on experience with:

* Creating and configuring an EC2 instance.
* Connecting to Linux servers using SSH.
* Working with Linux commands and file permissions.
* Installing and managing Apache.
* Configuring Security Groups and inbound rules.
* Managing code using Git and GitHub.
* Creating IAM roles and custom permission policies.
* Understanding how EC2 uses IAM roles to access AWS services.
* Creating private S3 buckets and managing objects.
* Using AWS CLI to interact with AWS services.
* Writing Bash scripts for basic deployment automation.

## Limitations and Future Improvements

This is a learning project, so the setup is intentionally simple. There are several things I would like to improve as I continue learning AWS.

Possible improvements include:

* Configure HTTPS instead of serving the website only over HTTP.
* Use an Application Load Balancer to distribute incoming traffic.
* Add an Auto Scaling Group for better availability and scalability.
* Set up CloudWatch metrics and alarms.
* Create a CI/CD pipeline for automated deployment.
* Add deployment rollback and automated testing.

## Cost Management

I used AWS resources for learning and testing, so I also reviewed the resources that could generate charges.

When the project is not being used, I plan to stop or remove resources that are no longer needed and check AWS Billing to monitor costs.

## Author

Built as part of my hands-on learning journey in AWS and Cloud Engineering.
