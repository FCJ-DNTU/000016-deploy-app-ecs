+++
title = "Cấu hình Route Table"
date = 2024
weight = 5
chapter = false
pre = "<b>2.5 </b>"
+++

#### Tạo Route Table

Trong giao diện quản lý VPC, từ bảng chọn bên trái:

- Chọn **Route tables**
- Nhấn **Create route table**

![3.15](/images/2-preparation/3.15.png)

Cấu hình Route Table:

- Name: `FCJ-rtb-private`
- Chọn VPC: **FCJ-Lab-vpc**
- Nhấn **Create route table**

![3.16](/images/2-preparation/3.16.png)

Liên kết NAT Gateway với Route Table:

- Chọn route table vừa tạo
- Nhấn **Edit routes**

![3.17](/images/2-preparation/3.17.png)

- Nhấn **Add route**
- Destination: **0.0.0.0/0**
- Target: **NAT Gateway**
- Chọn NAT Gateway **FCJ-Lab-nat** vừa tạo

![3.18](/images/2-preparation/3.18.png)

Liên kết các Subnet private với Route Table:

- Trong mục thông tin của Route Table, chọn **Subnet associations**
- Nhấn **Edit subnet associations**

![3.19](/images/2-preparation/3.19.png)

- Chọn hai Subnet private vừa tạo

![3.20](/images/2-preparation/3.20.png)
