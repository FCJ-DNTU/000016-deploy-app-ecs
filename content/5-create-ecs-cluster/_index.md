+++
title = "Create ECS Cluster"
date = 2024
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

#### Create ECS Cluster

In the search bar

- Type `ECS`
- Select **Elastic Container Service**

![5.1](/images/5-create-ecs-cluster/5.1.png)

On the main ECS Console interface

- Select **Cluster**
- Click **Create cluster** to create a new cluster

![5.2](/images/5-create-ecs-cluster/5.2.png)

On the Create Cluster page

- Name: Enter `FCJ-Lab-cluster`
- Namespace: It will be automatically created
- Infrastructure: Select **AWS Fargate**.

![5.3](/images/5-create-ecs-cluster/5.3.png)

In the Monitoring section

- Select **Use Container Insight**
- Click **Create** to create the cluster

![5.4](/images/5-create-ecs-cluster/5.4.png)

{{% notice note %}}
We enable Container Insight because in a later workshop, we will take a closer look at the ECS Services and the Containers inside a Cluster.
{{% /notice %}}

Result

![5.5](/images/5-create-ecs-cluster/5.5.png)

