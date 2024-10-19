+++
title = "Frontend task definition"
date = 2024
weight = 1
chapter = false
pre = "<b>6.2. </b>"
+++

Tương tự, giờ chúng ta sẽ tạo task definition cho frontend

#### Cấu hình Task Definition cho Frontend Service

Trở lại màn hình Task definition

- Xổ **Create new task definition**
- Chọn **Create new task definition**

![6.2.1](/images/6-create-task-definition/6.2.1.png)

Tiếp tục điền các thông tin cơ bản

- Family name: nhập `fcjresbar-task-fe`
- Trong phần **Infrastructure requirements**
  - Launch type: chọn **AWS Fargate**
  - OS, Architecture, Network: chọn **Linux/x86_64**, network mặc định là **awsvcp** khi chọn AWS Fargate.

![6.2.2](/images/6-create-task-definition/6.2.2.png)

Các thông tin tiếp theo

- CPU: **2 vCPU**
- Memory: **6 GB**
- Task role và Task execution role để mặc định

![6.2.3](/images/6-create-task-definition/6.2.3.png)

Trong phần định nghĩa container, điền các thông tin

- Name: `frontend`
- Image URI: uri của frontend image trong ECR hoặc Dockerhub, ở đây mình sẽ dùng trong ECR.
- Container port: `80`; protocol: **TCP**; App protocol: **HTTP**
- Resource allocation limits:
  - CPU: `1`
  - Memory hard limit: `3`
  - Memory soft limit: `2`

![6.2.4](/images/6-create-task-definition/6.2.4.png)

Tiếp theo là thêm biến môi trường, bao gồm:

- `BACKEND_HOST` = `backend.fcjresbar.internal`
- `BACKEND_PORT` = `5000`

![6.2.5](/images/6-create-task-definition/6.2.5.png)

Giữ các cấu hình này mặc định

![6.2.6](/images/6-create-task-definition/6.2.6.png)

Cuối cùng là ấn **Create** để tạo task definition

![6.2.7](/images/6-create-task-definition/6.2.7.png)

![6.2.8](/images/6-create-task-definition/6.2.8.png)
