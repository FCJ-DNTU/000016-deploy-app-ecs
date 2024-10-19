+++
title = "Create Application Load Balancer"
date = 2024
weight = 2
chapter = false
pre = "<b>7.2. </b>"
+++

#### Create Application Load Balancer

Still in this interface:

- Select **Load balancers**
- Click **Create load balancer**

![7.2.1](/images/7-configure-alb/7.2.1.png)

For Load balancer type, select Application Load Balancer and click **Create**

![7.2.2](/images/7-configure-alb/7.2.2.png)

In the Basic configuration section:

- Name: `FCJ-Lab-alb`
- Scheme: select **Internet-facing**
- Load balancer IP address type: IPv4

![7.2.3](/images/7-configure-alb/7.2.3.png)

In the Network Mapping section:

- VPC: select the VPC that we created earlier
- Availability Zones
  - Select 2 AZs, and for each AZ, select the Public subnets.

![7.2.4](/images/7-configure-alb/7.2.4.png)

Next:

- In the Security group section, select the SG (Security Group) that we created earlier.
- In Listeners and routing:
  - Protocol : Port: HTTP : 80
  - Target group: select **FCJ-Lab-fe-tg**

![7.2.5](/images/7-configure-alb/7.2.5.png)

Review the information before creating.

![7.2.6](/images/7-configure-alb/7.2.6.png)

Result:

![7.2.7](/images/7-configure-alb/7.2.7.png)
