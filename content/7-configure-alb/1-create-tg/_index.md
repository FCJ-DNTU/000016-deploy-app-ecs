+++
title = "Create Target Group"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Configure Target Group

In the search bar:

- Type `Target Groups`
- Select **Target Groups** (EC2 feature)

![7.1.1](/images/7-configure-alb/7.1.1.png)

On the Target Group screen, click **Create target group**

![7.1.2](/images/7-configure-alb/7.1.2.png)

In the Basic configuration section, select **IP Address**.

![7.1.3](/images/7-configure-alb/7.1.3.png)

Enter the following information:

- Name: `FCJ-Lab-fe-tg`
- Protocol : Port: HTTP : 80
- VPC: select the VPC that we created earlier.
- Protocol version: HTTP1

![7.1.4](/images/7-configure-alb/7.1.4.png)

In the Health check section, we will add a Health check path as `/health` and click **Next** to continue.

![7.1.5](/images/7-configure-alb/7.1.5.png)

In this section, we will keep the default configurations.

![7.1.6](/images/7-configure-alb/7.1.6.png)

Click **Create target group** to create the target group.

![7.1.7](/images/7-configure-alb/7.1.7.png)

![7.1.8](/images/7-configure-alb/7.1.8.png)
