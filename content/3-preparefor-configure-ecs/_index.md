+++
title = "Preparing for ECS"
date = 2024
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Adding a Private Subnet

In the VPC management console, on the left-side panel:

- Select **Subnet**
- Click **Create subnet**

![3.1](/images/3-prepare-for-ecs/3.1.png)

- Choose VPC **FCJ-Lab-vpc**

![3.2](/images/3-prepare-for-ecs/3.2.png)

Follow the instructions:

- Subnet name: `FCJ-Lab-subnet-private3`
- Select Availability Zone
- IPv4 VPC CIDR block: `10.0.0.0/16`
- IPv4 subnet CIDR block: `10.0.32.0/20`
- Click **Create subnet**

![3.3](/images/3-prepare-for-ecs/3.3.png)

Result:

![3.4](/images/3-prepare-for-ecs/3.4.png)

Similarly, create another subnet:

- Subnet name: `FCJ-Lab-subnet-private4`
- Choose a different Availability Zone from the one above
- IPv4 VPC CIDR block: `10.0.0.0/16`
- IPv4 subnet CIDR block: `10.0.64.0/20`
- Click **Create subnet**

![3.5](/images/3-prepare-for-ecs/3.5.png)

Result:

![3.6](/images/3-prepare-for-ecs/3.6.png)

#### Creating a NAT Gateway

First, create Elastic IPs for the NAT Gateway. In the VPC management console, on the left-side panel:

- Select **Elastic IPs**
- Click **Allocate Elastic IP address**

![3.7](/images/3-prepare-for-ecs/3.7.png)

Configure Elastic IP address:

- Public IPv4 address pool: **Amazon's pool of IPv4 address**
- Network border group: **ap-southeast-1** (if using the same region)

![3.8](/images/3-prepare-for-ecs/3.8.png)

In the optional tags:

- Key: `Name`
- Value: `FCJ-Lab-IP`
- Click **Allocate**

![3.9](/images/3-prepare-for-ecs/3.9.png)

Next, create the NAT Gateway. In the right-side panel:

- Select **NAT gateways**
- Click **Create NAT gateway**

![3.11](/images/3-prepare-for-ecs/3.11.png)

Configure the NAT Gateway:

- Name: `FCJ-Lab-nat`
- Subnet: select the public subnet as instructed
- Connectivity type: **Public**
- Select the Elastic IP created in the previous step
- Click **Create NAT gateway**

![3.12](/images/3-prepare-for-ecs/3.12.png)

Wait until the state becomes **Available**.

![3.14](/images/3-prepare-for-ecs/3.14.png)

#### Creating a Route Table

In the VPC management console, on the left-side panel:

- Select **Route tables**
- Click **Create route table**

![3.15](/images/3-prepare-for-ecs/3.15.png)

- Name: `FCJ-rtb-private`
- VPC: **FCJ-Lab-vpc**
- Click **Create route table**

![3.16](/images/3-prepare-for-ecs/3.16.png)

Next, associate the NAT gateway with the route table:

- Select the route table you just created
- Click **Edit routes**

![3.17](/images/3-prepare-for-ecs/3.17.png)

- Click **Add route**
- Set Destination to **0.0.0.0/0**
- Set Target to **NAT Gateway**
- Choose the NAT gateway named **FCJ-Lab-nat** created earlier

![3.18](/images/3-prepare-for-ecs/3.18.png)

Next, associate the private subnets with the route table. In the details section of the route table:

- Select **Subnet associations**
- Click **Edit subnet associations**

![3.19](/images/3-prepare-for-ecs/3.19.png)

- Select the two private subnets created earlier

![3.20](/images/3-prepare-for-ecs/3.20.png)

#### Creating Security Groups

In the VPC management console, on the left-side panel:

- Select **Security groups**
- Click **Create security group**

![3.22](/images/3-prepare-for-ecs/3.22.png)

Configure the security group:

- Name: `FCJ-Lab-sg-private`
- Description: `Allow access for Internet`
- Select the VPC you created

For Inbound rules:

- Choose **All traffic**
- Select **FCJ-Lab-sg-public**

![3.23](/images/3-prepare-for-ecs/3.23.png)

For Outbound rules:

- Choose **All traffic**
- Select **Anywhere IPv4**

![3.24](/images/3-prepare-for-ecs/3.24.png)

Next, attach the security group you just created to the **FCJ-Lab-sg-db** security group.

In the Security Groups management:

- Select **FCJ-Lab-sg-db**
- Click **Action**
- Click **Edit inbound rules**

![3.25](/images/3-prepare-for-ecs/3.25.png)

For Inbound rules:

- Add a new rule
- Select MYSQL/Aurora
- Set Custom to point to the **FCJ-Lab-sg-private** security group
- Click **Save rules**

![3.26](/images/3-prepare-for-ecs/3.26.png)

#### Creating a CodeDeploy Role

- Search and select `IAM`

![3.29](/images/3-prepare-for-ecs/3.29.png)

- Select `Roles`
- Click **Create role**

![3.30](/images/3-prepare-for-ecs/3.30.png)

In the Use Case section, fill out the following details:

- Services or use case: `CodeDeploy`
- Select **CodeDeploy - ECS**
- Click **Next**

![3.31](/images/3-prepare-for-ecs/3.31.png)

Continue by clicking **Next**.

![3.32](/images/3-prepare-for-ecs/3.32.png)

- Role name: `CodeDeployServiceRole`

![3.33](/images/3-prepare-for-ecs/3.33.png)

- Click **Create role**

![3.34](/images/3-prepare-for-ecs/3.34.png)

Now we've completed all the steps to prepare for the workshop.
