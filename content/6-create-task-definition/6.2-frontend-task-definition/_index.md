+++
title = "Frontend task definition"
date = 2024
weight = 1
chapter = false
pre = "<b>6.2. </b>"
+++

Similarly, now we will create the task definition for the frontend.

#### Configuring Task Definition for Frontend Service

Go back to the Task definition screen:

- Click on **Create new task definition**
- Select **Create new task definition**

![6.2.1](/images/6-create-task-definition/6.2.1.png)

Continue filling in the basic information:

- Family name: enter `fcjresbar-task-fe`
- In the **Infrastructure requirements**
  - Launch type: choose **AWS Fargate**
  - OS, Architecture, Network: choose **Linux/x86_64**, and the default network will be **awsvcp** when AWS Fargate is selected.

![6.2.2](/images/6-create-task-definition/6.2.2.png)

Next information:

- CPU: **2 vCPU**
- Memory: **6 GB**
- Task role and Task execution role as default.

![6.2.3](/images/6-create-task-definition/6.2.3.png)

In the container definition section, fill in the following details:

- Name: `frontend`
- Image URI: the URI of the frontend image from either ECR or Dockerhub; here, we will use ECR.
- Container port: `80`; protocol: **TCP**; App protocol: **HTTP**
- Resource allocation limits:
  - CPU: `1`
  - Memory hard limit: `3`
  - Memory soft limit: `2`

![6.2.4](/images/6-create-task-definition/6.2.4.png)

Next, add the environment variables, which include:

- `BACKEND_HOST` = `backend.fcjresbar.internal`
- `BACKEND_PORT` = `5000`

![6.2.5](/images/6-create-task-definition/6.2.5.png)

Keep the default configurations.

![6.2.6](/images/6-create-task-definition/6.2.6.png)

Finally, click **Create** to create the task definition.

![6.2.7](/images/6-create-task-definition/6.2.7.png)

![6.2.8](/images/6-create-task-definition/6.2.8.png)
