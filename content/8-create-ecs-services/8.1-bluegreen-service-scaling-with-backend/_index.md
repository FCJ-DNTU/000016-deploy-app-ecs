+++
title = "Blue/Green Deployment and Service Scaling with Backend"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Create backend service

Return to the ECS console

- Select **Cluster**
- Choose the cluster **FCJ-Lab-cluster** that we created in the previous section

![8.1.1](/images/8-create-ecs-services/8.1.1.png)

Scroll down to the bottom, in the Services section, click **Create**

![8.1.2](/images/8-create-ecs-services/8.1.2.png)

#### ECS Service Environment

The Cluster will be automatically selected. In the Compute option section, we only need to select the Launch type; the remaining configurations will be added by default.

![8.1.3](/images/8-create-ecs-services/8.1.3.png)

#### Deployment configuration

In this section, we will configure the deployment:

- Application type: select **Service**
- Family: select `fcjresbar-task-be`, choose the Revision labeled **LATEST**.
- Name: `backend`
- Service type and Desired tasks leave as default

![8.1.4](/images/8-create-ecs-services/8.1.4.png)

In the deployment options section:

- Deployment type: select **Blue/green deployment (powered by AWS CodeDeploy)**
- Deployment configuration: select **CodeDeployDefault.ECSCanary10Percent5Minutes**
- Service role for CodeDeploy: select the role that we created in the preparation section

![8.1.5](/images/8-create-ecs-services/8.1.5.png)

#### Service discovery

This section is important; to allow the Frontend Service and Backend Service to communicate, we must configure Service discovery for the Backend Service with the namespace and service created in section 4 earlier.

- Select **Use service discovery**
- Select **Select an existing namespace**, Select namespace **fcjresbar.internal** that we created earlier
- Select **Select an existing service discovery service**, Select service **backend**
- Leave the remaining configurations as default

![8.1.6](/images/8-create-ecs-services/8.1.6.png)

#### Networking

Now, we will let this Service know which network and subnet it should be placed in.

- VPC: select the VPC that we created earlier
- Subnet: choose the private subnet (**FCJ-Lab-subnet-private4**) that we created in the preparation section
- Security group: select **FCJ-Lab-sg-private**.

![8.1.7](/images/8-create-ecs-services/8.1.7.png)

{{% notice note %}}
 Public IP should be disabled because the traffic is routed to the Service through the Load Balancer.
{{% /notice %}}

#### Load balancing

In reality, we do not need to configure Load balancing for the backend service, as for testing, I will need to use a private network or VPN. However, in this tutorial, I will configure Load balancing, opening 2 listeners for production and testing so that developers/testers can use them for feature testing.

First, configure some information:

- Load balancing type: select **Application Load Balancer**
- Container: backend 5000:5000 (the port here will be the host and container port)
- Select **Use an existing load balancer**
- Select **FCJ-Lab-alb** load balancer

![8.1.8](/images/8-create-ecs-services/8.1.8.png)

In the listener section, we will create two listeners with the following information:

- Production listener: port 5000, protocol HTTP
- Test listener: port 8080, protocol HTTP

The target group will automatically have the following parameters as shown in the image

![8.1.9](/images/8-create-ecs-services/8.1.9.png)

![8.1.10](/images/8-create-ecs-services/8.1.10.png)

![8.1.11](/images/8-create-ecs-services/8.1.11.png)

#### Service auto scaling

Giờ thì mình sẽ cấu hình scaling cho container

- Minimun: 1
- Maximun: 2
- Scaling policy type: Target tracking

![8.1.12](/images/8-create-ecs-services/8.1.12.png)

Now, I will configure scaling for the container.

- Name: `ScaleAtThreshold75Percent`
- ECS service metric: **ECSServiceAverageCPUUtilization**
- Target value: 75
- Scale-out cooldown period: 120
- Scale-in cooldown period: 120
- Click Create to create it

![8.1.13](/images/8-create-ecs-services/8.1.13.png)

Wait a moment, and the service will be created.

![8.1.14](/images/8-create-ecs-services/8.1.14.png)
