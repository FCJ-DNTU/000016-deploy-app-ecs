+++ 
title = "Preparing for ECS" 
date = 2024 
weight = 3 
chapter = false 
pre = "<b>3. </b>" 
+++

#### Adding a Private Subnet

In the VPC management interface, from the left-hand menu:

- Select **Subnet**
- Click **Create subnet**

![3.1](/images/3-prepare-for-ecs/3.1.png)

- Select the VPC **FCJ-Lab-vpc**

![3.2](/images/3-prepare-for-ecs/3.2.png)

Follow these settings:

- Subnet name: `FCJ-Lab-subnet-private3`
- Choose Availability Zone
- IPv4 VPC CIDR block: `10.0.0.0/16`
- IPv4 subnet CIDR block: `10.0.32.0/20`
- Click **Create subnet**

![3.3](/images/3-prepare-for-ecs/3.3.png)

Result:

![3.4](/images/3-prepare-for-ecs/3.4.png)

Similarly, create another subnet:

- Subnet name: `FCJ-Lab-subnet-private4`
- Choose a different Availability Zone than the one chosen earlier
- IPv4 VPC CIDR block: `10.0.0.0/16`
- IPv4 subnet CIDR block: `10.0.64.0/20`
- Click **Create subnet**

![3.5](/images/3-prepare-for-ecs/3.5.png)

Result:

![3.6](/images/3-prepare-for-ecs/3.6.png)

#### Creating a NAT Gateway

First, we need to create Elastic IPs to assign to the NAT Gateway. In the VPC management interface, from the left-hand menu:

- Select **Elastic IPs**
- Click **Allocate Elastic IP address**

![3.7](/images/3-prepare-for-ecs/3.7.png)

Elastic IP address configuration:

- Public IPv4 address pool: **Amazon's pool of IPv4 address**
- Network border group: **ap-southeast-1** if using the same region

![3.8](/images/3-prepare-for-ecs/3.8.png)

For tags (optional):

- Key: `Name`
- Value: `FCJ-Lab-IP`
- Click **Allocate**

![3.9](/images/3-prepare-for-ecs/3.9.png)

Next, we'll create the NAT Gateway. From the right-hand menu:

- Select **NAT gateways**
- Click **Create NAT gateway**

![3.11](/images/3-prepare-for-ecs/3.11.png)

NAT Gateway configuration:

- Name: `FCJ-Lab-nat`
- Subnet: Select a public subnet as instructed
- Connectivity type: **Public**
- Select the Elastic IP created earlier
- Click **Create NAT gateway**

![3.12](/images/3-prepare-for-ecs/3.12.png)

Wait a moment until the state changes to **Available**.

![3.14](/images/3-prepare-for-ecs/3.14.png)

#### Route Table

In the VPC management interface, from the left-hand menu:

- Select **Route tables**
- Click **Create route table**

![3.15](/images/3-prepare-for-ecs/3.15.png)

- Name: `FCJ-rtb-private`
- VPC: **FCJ-Lab-vpc**
- Click **Create route table**

![3.16](/images/3-prepare-for-ecs/3.16.png)

Next, we'll associate the NAT Gateway with the route table:

- Select the route table created
- Click **Edit routes**

![3.17](/images/3-prepare-for-ecs/3.17.png)

- Click **Add route**
- Destination: **0.0.0.0/0**
- Target: **NAT Gateway**
- Select the NAT Gateway **FCJ-Lab-nat** created earlier

![3.18](/images/3-prepare-for-ecs/3.18.png)

Next, associate the private subnets to the route table created. In the route table details:

- Select **Subnet associations**
- Click **Edit subnet associations**

![3.19](/images/3-prepare-for-ecs/3.19.png)

- Select the two private subnets created earlier

![3.20](/images/3-prepare-for-ecs/3.20.png)

#### Creating Security Groups

In the VPC management interface, from the left-hand menu:

- Select **Security groups**
- Click **Create security group**

![3.22](/images/3-prepare-for-ecs/3.22.png)

Security group configuration:

- Name: `FCJ-Lab-sg-private`
- Description: `Allow access for Internet`
- Select the VPC created earlier

For Inbound rules:

- Select **All traffic**
- Choose **FCJ-Lab-sg-public**

![3.23](/images/3-prepare-for-ecs/3.23.png)

For Outbound rules:

- Select **All traffic**
- Choose **Anywhere IPv4**

![3.24](/images/3-prepare-for-ecs/3.24.png)

Next, assign this security group to the **FCJ-Lab-sg-db** security group.

In the Security groups management interface:

- Select **FCJ-Lab-sg-db**
- Click **Action**
- Choose **Edit inbound rules**

![3.25](/images/3-prepare-for-ecs/3.25.png)

In the Inbound Rules:

- Add rule
- Select **MYSQL/Aurora**
- Custom, select the security group **FCJ-Lab-sg-private**
- Click **Save rules**

![3.26](/images/3-prepare-for-ecs/3.26.png)
