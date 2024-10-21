+++
title = "Add Subnet"
date = 2024
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Add Private Subnet

In the VPC management interface, from the left menu:

- Select **Subnets**
- Click on the **Create subnet** button

![3.1](/images/2-preparation/3.1.png)

- Choose VPC **FCJ-Lab-vpc**

![3.2](/images/2-preparation/3.2.png)

Configure the following information:

- Subnet Name: `FCJ-Lab-subnet-private3`
- Select an Availability Zone
- IPv4 CIDR block of VPC: `10.0.0.0/16`
- IPv4 CIDR block of Subnet: `10.0.32.0/20`
- Click **Create subnet**

![3.3](/images/2-preparation/3.3.png)

Result:

![3.4](/images/2-preparation/3.4.png)

Similarly, create another subnet:

- Subnet Name: `FCJ-Lab-subnet-private4`
- Select a different Availability Zone than the previously created subnet
- IPv4 CIDR block of VPC: `10.0.0.0/16`
- IPv4 CIDR block of Subnet: `10.0.64.0/20`
- Click **Create subnet**

![3.5](/images/2-preparation/3.5.png)

Result:

![3.6](/images/2-preparation/3.6.png)
