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

**INSERT IMAGE HERE**

Tiếp tục điền các thông tin cơ bản

- Family name: nhập `fcjresbar-task-fe`
- Trong phần **Infrastructure requirements**
  - Launch type: chọn **AWS Fargate**
  - OS, Architecture, Network: chọn **Linux/x86_64**, network mặc định là **awsvcp** khi chọn AWS Fargate.

**INSERT IMAGE HERE**

Các thông tin tiếp theo

- CPU: **2 vCPU**
- Memory: **6 GB**
- Task role và Task execution role để mặc định

**INSERT IMAGE HERE**

Trong phần định nghĩa container, điền các thông tin

- Name: `frontend`
- Image URI: uri của frontend image trong ECR hoặc Dockerhub, ở đây mình sẽ dùng trong ECR.
- Container port: `80`; protocol: **TCP**; App protocol: **HTTP**
- Resource allocation limits:
  - CPU: `1`
  - Memory hard limit: `3`
  - Memory soft limit: `2`

**INSERT IMAGE HERE**

Tiếp theo là thêm biến môi trường, bao gồm:

- `BACKEND_HOST` = `backend.fcjresbar.internal`
- `BACKEND_PORT` = `5000`

**INSERT IMAGE HERE**

Giữ các cấu hình này mặc định

**INSERT IMAGE HERE**

Cuối cùng là ấn **Create** để tạo task definition

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**
