+++
title = "Configure Route Table"
date = 2024
weight = 5
chapter = false
pre = "<b>2.5 </b>"
+++

#### Create Route Table

In the VPC management interface, from the left menu:

- Select **Route tables**
- Click on **Create route table**

![3.15](/images/2-preparation/3.15.png)

Configure the Route Table:

- Name: `FCJ-rtb-private`
- Choose VPC: **FCJ-Lab-vpc**
- Click **Create route table**

![3.16](/images/2-preparation/3.16.png)

Link the NAT Gateway with the Route Table:

- Select the route table you just created
- Click **Edit routes**

![3.17](/images/2-preparation/3.17.png)

- Click **Add route**
- Destination: **0.0.0.0/0**
- Target: **NAT Gateway**
- Select the NAT Gateway **FCJ-Lab-nat** you just created

![3.18](/images/2-preparation/3.18.png)

Associate the private subnets with the Route Table:

- In the Route Table details, select **Subnet associations**
- Click **Edit subnet associations**

![3.19](/images/2-preparation/3.19.png)

- Select the two private subnets you just created

![3.20](/images/2-preparation/3.20.png)
