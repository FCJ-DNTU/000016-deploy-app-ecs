+++
title = "Backend task definition"
date = 2024
weight = 1
chapter = false
pre = "<b>6.1. </b>"
+++

Lưu ý, như mình đã nói ở trên thì trong phần này, bạn có thể dùng image ở ECR hoặc Dockerhub đều được.

![6.1.1](/images/6-create-task-definition/6.1.1.png)

![6.1.2](/images/6-create-task-definition/6.1.2.png)

#### Cấu hình Task Definition cho Backend Service

Vẫn ở trong giao diện ECS Console

- Chọn **Task definitions**
- Ấn **Create new task definition**.

![6.1.3](/images/6-create-task-definition/6.1.3.png)

Điền trước một số thông tin cho task definition

- Family name: nhập `fcjresbar-task-be`
- Trong phần **Infrastructure requirements**
  - Launch type: chọn **AWS Fargate**
  - OS, Architecture, Network: chọn **Linux/x86_64**, network mặc định là **awsvcp** khi chọn AWS Fargate.

![6.1.4](/images/6-create-task-definition/6.1.4.png)

Các thông tin tiếp theo

- CPU: **4 vCPU**
- Memory: **8 GB**
- Task role và Task execution role để mặc định

![6.1.5](/images/6-create-task-definition/6.1.5.png)

Trong phần định nghĩa container, điền các thông tin

- Name: `backend`
- Image URI: uri của backend image trong ECR hoặc Dockerhub, ở đây mình sẽ dùng trong ECR.
- Container port: `5000`; protocol: **TCP**; App protocol: **HTTP**
- Resource allocation limits:
  - CPU: `2`
  - Memory hard limit: `4`
  - Memory soft limit: `3`

{{% notice note %}}
Khi cấu hình container trong AWS Fargate, thì mình sẽ không cần quan tâm tới Port của host, vì mặc định port của host sẽ là của container.
{{% /notice %}}

![6.1.6](/images/6-create-task-definition/6.1.6.png)

Tiếp theo là thêm biến môi trường, phần này quan trọng, nếu như không cấu hình thì NodeJS server ở bên trong không chạy được, bao gồm:

- `MYSQL_USER` = `admin`
- `MYSQL_PASSWORD` = `letmein12345`
- `MYSQL_DATABASE` = `fcjresbar`
- `DB_HOST` = "your rds endpoint"
- `DB_DIALECT` = `mysql`
- `PORT` = `5000`
- `JWT_SECRET` = `0bac010eca699c25c8f62ba86e319c2305beb94641b859c32518cb854addb5f4`

![6.1.7](/images/6-create-task-definition/6.1.7.png)

Giữ các cấu hình này mặc định

![6.1.8](/images/6-create-task-definition/6.1.8.png)

Cuối cùng là ấn **Create** để tạo task definition

![6.1.9](/images/6-create-task-definition/6.1.9.png)

![6.1.10](/images/6-create-task-definition/6.1.10.png)
