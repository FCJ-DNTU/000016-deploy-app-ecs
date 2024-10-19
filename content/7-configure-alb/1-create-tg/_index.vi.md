+++
title = "Tạo Target Group"
date = 2024
weight = 1
chapter = false
pre = "<b>7.1. </b>"
+++

#### Cấu hình Target Group

Trên thanh tìm kiếm

- Nhập `Target Groups`
- Chọn **Target Groups** (EC2 feature)

![7.1.1](/images/7-configure-alb/7.1.1.png)

Trong màn hình Target Group, ấn **Create target group**

![7.1.2](/images/7-configure-alb/7.1.2.png)

Trong phần Basic configuration, chọn **IP Address**.

![7.1.3](/images/7-configure-alb/7.1.3.png)

Nhập các thông tin

- Name: `FCJ-Lab-fe-tg`
- Protocol : Port: HTTP : 80
- VPC: chọn VPC mà chúng ta đã tạo trước đó
- Protocol version: HTTP1

![7.1.4](/images/7-configure-alb/7.1.4.png)

Trong phần Health check, chúng ta sẽ thêm Health check path là `/health` và ấn **Next** để tiếp tục

![7.1.5](/images/7-configure-alb/7.1.5.png)

Trong phần này chúng ta sẽ giữ nguyên các cấu hình

![7.1.6](/images/7-configure-alb/7.1.6.png)

Ấn **Create target group** để tạo target group

![7.1.7](/images/7-configure-alb/7.1.7.png)

![7.1.8](/images/7-configure-alb/7.1.8.png)
