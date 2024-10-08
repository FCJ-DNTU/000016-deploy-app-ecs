+++
title = "Deploy Application on Docker"
date = 2024
weight = 1
chapter = false
+++

# Deploy Application on Docker

#### Overview
In this first lab, you will be creating your new **AWS** account and use Multi-factor Authentication (**MFA**) to improve your account security. Next, you will create an **Administrator Group** and **Admin User** to manage access to resources in your account instead of using the root user. \
Finally, we will step through account authentication with **AWS Support** in the event you experience authentication problems.

#### AWS Account
**An AWS account** is the basic container for all the AWS resources you can create as an AWS customer. By default, each AWS account will have a _root user_. The _root user_ has full access within your AWS account, and root user permissions cannot be limited. When you first create your AWS account, you will be assessing it as the _root user_.

{{% notice note%}}
As a best practice, do not use the AWS account _root user_ for any task where it's not required. Instead, create a new IAM user for each person that requires administrator access. Thereafter, the users in the administrators user group should set up the user groups, users, and so on, for the AWS account. All future interaction should be through the AWS account's users and their own keys instead of the root user. However, to perform some account and service management tasks, you must log in using the root user credentials.
{{% /notice%}}



#### Main Content

1. [Introduction](1-introduction/)
2. [Deploy on Local](2-deploy-local/)
3. [Preparation](3-preparation/)
4. [Configure RDS](4-configure-rds/)
5. [Configure EC2 Instance](5-configure-ec2/)
6. [Deploy use only Docker Image](6-docker-image/)
7. [Deploy with Docker Compose](7-docker-compose/)
8. [Push Image](8-push-image/)
9. [Clean up resources](9-clean-up/)
<!-- need to remove parenthesis for path in Hugo 0.88.1 for Windows-->