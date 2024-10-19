+++
title = "Backend task definition"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

Note: As mentioned earlier, you can use images from either ECR or Dockerhub in this section.

![6.1.1](/images/6-create-task-definition/6.1.1.png)

![6.1.2](/images/6-create-task-definition/6.1.2.png)

#### Configuring Task Definition for Backend Service

Still within the ECS Console interface:

- Select **Task definitions**
- Click **Create new task definition**.

![6.1.3](/images/6-create-task-definition/6.1.3.png)

Enter the following information for the task definition:

- Family name: enter `fcjresbar-task-be`
- In the **Infrastructure requirements** section:
  - Launch type: choose **AWS Fargate**
  - OS, Architecture, Network: choose **Linux/x86_64**, and the default network will be **awsvcp** when AWS Fargate is selected.

![6.1.4](/images/6-create-task-definition/6.1.4.png)

Next information:

- CPU: **4 vCPU**
- Memory: **8 GB**
- Task role and Task execution role as default.

![6.1.5](/images/6-create-task-definition/6.1.5.png)

In the container definition section, fill in the following details:

- Name: `backend`
- Image URI: the URI of the backend image from either ECR or Dockerhub; here, we will use ECR.
- Container port: `5000`; protocol: **TCP**; App protocol: **HTTP**
- Resource allocation limits:
  - CPU: `2`
  - Memory hard limit: `4`
  - Memory soft limit: `3`

{{% notice note %}}
When configuring containers in AWS Fargate, you don’t need to worry about the host port, as the host port will default to the container's port. 
{{% /notice %}}

![6.1.6](/images/6-create-task-definition/6.1.6.png)

Next, add environment variables, which are important. Without this configuration, the NodeJS server inside won’t run. These include:

- `MYSQL_USER` = `admin`
- `MYSQL_PASSWORD` = `letmein12345`
- `MYSQL_DATABASE` = `fcjresbar`
- `DB_HOST` = "your rds endpoint"
- `DB_DIALECT` = `mysql`
- `PORT` = `5000`
- `JWT_SECRET` = `0bac010eca699c25c8f62ba86e319c2305beb94641b859c32518cb854addb5f4`

![6.1.7](/images/6-create-task-definition/6.1.7.png)

Keep the default configurations.

![6.1.8](/images/6-create-task-definition/6.1.8.png)

Finally, click **Create** to create the task definition.

![6.1.9](/images/6-create-task-definition/6.1.9.png)

![6.1.10](/images/6-create-task-definition/6.1.10.png)
