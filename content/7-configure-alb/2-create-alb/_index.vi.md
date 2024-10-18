+++
title = "Tạo Application Load Balancer"
date = 2024
weight = 2
chapter = false
pre = "<b>7.2. </b>"
+++

#### Tạo Application load balancer

Vẫn trong giao diện này

- Chọn **Load balancers**
- Ấn **Create load balancer**

**INSERT IMAGE HERE**

Load balancer type, chọn Application Load Balancer, ấn **Create**

**INSERT IMAGE HERE**

Trong phần Basic configuration

- Name: `FCJ-Lab-alb`
- Scheme: chọn **Internet-facing**
- Load balancer IP address type: IPv4

**INSERT IMAGE HERE**

Trong phần Network Mapping

- VPC: chọn VPC mà chúng ta đã tạo trước đó
- Availability Zones
  - Chọn 2 AZ, mỗi AZ chọn các Public subnet

**INSERT IMAGE HERE**

Tiếp theo

- Trong phần Security group, chọn SG mà chúng ta đã tạo trước đó
- Listeners and routing:
  - Protocol : Port: HTTP : 80
  - Target group: chọn **FCJ-Lab-fe-tg**

**INSERT IMAGE HERE**

Kiểm tra lại thông tin trước khi tạo

**INSERT IMAGE HERE**

Kết quả

**INSERT IMAGE HERE**
