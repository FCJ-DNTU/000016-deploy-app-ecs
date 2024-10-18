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

**INSERT IMAGE HERE**

Trong màn hình Target Group, ấn **Create target group**

**INSERT IMAGE HERE**

Trong phần Basic configuration, chọn **IP Address**.

**INSERT IMAGE HERE**

Nhập các thông tin

- Name: `FCJ-Lab-fe-tg`
- Protocol : Port: HTTP : 80
- VPC: chọn VPC mà chúng ta đã tạo trước đó
- Protocol version: HTTP1

**INSERT IMAGE HERE**

Trong phần Health check, chúng ta sẽ thêm Health check path là `/health` và ấn **Next** để tiếp tục

**INSERT IMAGE HERE**

Trong phần này chúng ta sẽ giữ nguyên các cấu hình

**INSERT IMAGE HERE**

Ấn **Create target group** để tạo target group

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**
