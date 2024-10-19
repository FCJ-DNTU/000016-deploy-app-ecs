+++
title = "Deploy Rolling with Frontend"
date = 2024
weight = 1
chapter = false
pre = "<b>8.2. </b>"
+++

After creating the Backend service, we will now proceed to create the Frontend service.

#### TCreate Frontend Service

Next, in the cluster console page, click **Create** to add the Frontend service.

#### ECS Service Environment

The Cluster will be automatically selected. In the Compute option section, we only need to select the Launch type; the remaining configurations will be added by default.

![8.2.1](/images/8-create-ecs-services/8.2.1.png)

#### Deployment configuration

In this section, we will configure the deployment:

- Application type: select **Service**
- Family: select `fcjresbar-task-fe`, choose the Revision labeled **LATEST**.
- Name: `frontend`
- Service type and Desired tasks leave as default

![8.2.2](/images/8-create-ecs-services/8.2.2.png)

#### Networking

Now, we will let this Service know which network and subnet it should be placed in.

- VPC: select the VPC that we created earlier
- Subnet: choose private subnet (**FCJ-Lab-subnet-private4**) that we created in the preparation section
- Security group: select **FCJ-Lab-sg-private**.

![8.2.3](/images/8-create-ecs-services/8.2.3.png)

{{% notice note %}}
 Similarly, Public IP should be disabled because the traffic is routed to the Service through the Load Balancer. 
{{% /notice %}}

#### Load balancing

In reality, we do not need to configure Load balancing for the backend service, as for testing, I will need to use a private network or VPN. However, in this tutorial, I will configure Load balancing, opening 2 listeners for production and testing so that developers/testers can use them for feature testing.

First, configure some information:

- Load balancing type: select **Application Load Balancer**
- Container: frontend 80:80 (the port here will be the host and container port)
- Choose **Use an existing load balancer**
- Choose **FCJ-Lab-alb** load balancer
- Health check grace period: 30

![8.2.4](/images/8-create-ecs-services/8.2.4.png)

In the listener section, we will create the listener created earlier:

- Select **Use an existing listener**, select 80:HTTP

For the target group, select the target group that I created:

- Select **Use an existing target group**, select **FCJ-Lab-fe-tg**

![8.2.5](/images/8-create-ecs-services/8.2.5.png)

![8.2.6](/images/8-create-ecs-services/8.2.6.png)

Wait a moment, and the service will be created.

![8.2.7](/images/8-create-ecs-services/8.2.7.png)
