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

![7.2.1](/images/7-configure-alb/7.2.1.png)

Load balancer type, chọn Application Load Balancer, ấn **Create**

![7.2.2](/images/7-configure-alb/7.2.2.png)

Trong phần Basic configuration

- Name: `FCJ-Lab-alb`
- Scheme: chọn **Internet-facing**
- Load balancer IP address type: IPv4

![7.2.3](/images/7-configure-alb/7.2.3.png)

Trong phần Network Mapping

- VPC: chọn VPC mà chúng ta đã tạo trước đó
- Availability Zones
  - Chọn 2 AZ, mỗi AZ chọn các Public subnet

![7.2.4](/images/7-configure-alb/7.2.4.png)

Tiếp theo

- Trong phần Security group, chọn SG mà chúng ta đã tạo trước đó
- Listeners and routing:
  - Protocol : Port: HTTP : 80
  - Target group: chọn **FCJ-Lab-fe-tg**

![7.2.5](/images/7-configure-alb/7.2.5.png)

Kiểm tra lại thông tin trước khi tạo

![7.2.6](/images/7-configure-alb/7.2.6.png)

Kết quả

![7.2.7](/images/7-configure-alb/7.2.7.png)
