+++
title = "Configure NAT Gateway"
date = 2024
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++

#### Create NAT Gateway

First, you need to create an Elastic IP to associate with the NAT Gateway. From the left menu:

- Select **Elastic IPs**
- Click on **Allocate Elastic IP address**

![3.7](/images/2-preparation/3.7.png)

Configure the Elastic IP:

- Public IPv4 address pool: **Amazon's pool of IPv4 address**
- Network border group: **ap-southeast-1** (if you are using the same region)

![3.8](/images/2-preparation/3.8.png)

In the tags section (optional):

- Key: `Name`
- Value: `FCJ-Lab-IP`
- Click **Allocate**

![3.9](/images/2-preparation/3.9.png)

Next, create the NAT Gateway:

- Select **NAT gateways**
- Click on **Create NAT gateway**

![3.11](/images/2-preparation/3.11.png)

Configure the NAT Gateway:

- Name: `FCJ-Lab-nat`
- Select the public subnet you created
- Connectivity type: **Public**
- Associate the Elastic IP you just created
- Click **Create NAT gateway**

![3.12](/images/2-preparation/3.12.png)

After creation, wait for the status to change to **Available**.

![3.14](/images/2-preparation/3.14.png)
