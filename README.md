\# CloudLab — Secure AWS Web Server



\## Project Overview



CloudLab is a beginner cloud engineering project that demonstrates how to deploy a website on Amazon EC2, serve it using Apache, and securely retrieve a private configuration file from Amazon S3 using an IAM role.



The project combines Linux administration, networking, Git version control, AWS identity and access management, and basic deployment automation.



\## Architecture



```text

Developer Laptop

&#x20;     |

&#x20;     | Git push

&#x20;     v

GitHub Repository

&#x20;     |

&#x20;     | Git pull

&#x20;     v

Amazon EC2 — Amazon Linux 2023

&#x20;     |

&#x20;     +---- Apache HTTP Server

&#x20;     |          |

&#x20;     |          v

&#x20;     |      Website Visitors

&#x20;     |

&#x20;     +---- IAM Role

&#x20;                |

&#x20;                v

&#x20;          IAM Permissions

&#x20;                |

&#x20;                v

&#x20;          Private Amazon S3

&#x20;            config.json

```



\## AWS Services Used



\### Amazon EC2



Hosts the website on an Amazon Linux 2023 instance.



\### Amazon VPC and Security Groups



Control network access to the instance. SSH access is restricted to the administrator's IP address, while HTTP is publicly accessible for the demonstration website.



\### AWS IAM



An EC2 IAM role provides temporary AWS credentials without requiring permanent access keys to be stored on the instance.



The custom IAM permissions policy grants `s3:GetObject` access to the designated configuration object.



\### Amazon S3



Stores the application's configuration file in a private bucket with Block Public Access enabled.



\### AWS CLI



Tests the EC2 instance's AWS identity and retrieves the private configuration object.



\## Tools and Technologies



\* Amazon Linux 2023

\* Amazon EC2

\* Amazon S3

\* AWS IAM

\* AWS CLI

\* Apache HTTP Server

\* Linux shell scripting

\* Git and GitHub

\* HTML and CSS



\## Security Practices



\* Restrict SSH access to the administrator's public IP address.

\* Allow public HTTP access only as required for the demonstration.

\* Keep the S3 bucket private.

\* Use an EC2 IAM role instead of permanent AWS access keys.

\* Apply least-privilege permissions to S3 access.

\* Avoid committing private keys, credentials, and environment files to Git.

\* Review AWS resources and costs after testing.



\## Deployment



The website is stored in the GitHub repository and deployed to Apache's document root at `/var/www/html/`.



The `deploy.sh` script pulls updates from the `main` branch, installs the website's HTML file, validates Apache's configuration, reloads Apache, and checks the local HTTP response.



\## Project Learning Outcomes



\* Launch and connect to an EC2 instance using SSH.

\* Configure Security Group inbound rules.

\* Install and manage Apache on Linux.

\* Use Git and GitHub for version control.

\* Create and attach IAM roles and policies.

\* Access a private S3 object using an EC2 IAM role.

\* Use AWS CLI commands for identity and S3 operations.

\* Automate a basic website deployment using Bash.

\* Apply foundational cloud security practices.



\## Limitations and Future Improvements



This is a learning project, not a production-hardened architecture.



Possible improvements include:



\* Configure HTTPS with a suitable certificate.

\* Use an Application Load Balancer and Auto Scaling for a more resilient architecture.

\* Add monitoring and alarms with Amazon CloudWatch.

\* Introduce a CI/CD pipeline.

\* Add automated tests and deployment rollback.

\* Review and tighten IAM permissions as requirements evolve.



\## Cost Management



AWS resources may incur charges depending on their configuration and usage.



Review running instances, attached storage, public IPv4 addresses, and other billable resources when the project is not in use.



\## Author



Cloud engineering learning project.



