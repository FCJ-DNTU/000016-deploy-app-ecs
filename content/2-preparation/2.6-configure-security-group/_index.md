+++
title = "Configure Security Group"
date = 2024
weight = 6
chapter = false
pre = "<b>2.6 </b>"
+++

#### Create Security Groups

From the left menu:

- Select **Security groups**
- Click on **Create security group**

![3.22](/images/2-preparation/3.22.png)

Configure the Security Group:

- Name: `FCJ-Lab-sg-private`
- Description: `Allow access for Internet`
- Choose the VPC you created

Configure Inbound rules:

- Select **All traffic**
- Source: **FCJ-Lab-sg-public**

![3.23](/images/2-preparation/3.23.png)

Configure Outbound rules:

- Select **All traffic**
- Destination: **Anywhere IPv4**

![3.24](/images/2-preparation/3.24.png)

Link the Security Group with the group **FCJ-Lab-sg-db**:

- Select **FCJ-Lab-sg-db**
- Click **Action**, then select **Edit inbound rules**

![3.25](/images/2-preparation/3.25.png)

Configure Inbound Rule:

- Click **Add rule**
- Select **MYSQL/Aurora**
- Source: Choose Security Group **FCJ-Lab-sg-private**
- Click **Save rules**

![3.26](/images/2-preparation/3.26.png)

#### Create CodeDeploy Role

Search for and select **IAM**.

![3.29](/images/2-preparation/3.29.png)

- Select **Roles**
- Click on **Create role**

![3.30](/images/2-preparation/3.30.png)

In the use case section, choose:

- Service or use case: `CodeDeploy`
- Select **CodeDeploy - ECS**
- Click **Next**

![3.31](/images/2-preparation/3.31.png)

- Click **Next**

![3.32](/images/2-preparation/3.32.png)

- Role name: `CodeDeployServiceRole`

![3.33](/images/2-preparation/3.33.png)

- Click **Create role**
