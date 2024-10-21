+++
title = "Thêm Subnet"
date = 2024
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Thêm Subnet Private

Trong giao diện quản lý VPC, từ bảng chọn bên trái:

- Chọn **Subnet**
- Nhấn vào nút **Create subnet**

![3.1](/images/2-preparation/3.1.png)

- Chọn VPC **FCJ-Lab-vpc**

![3.2](/images/2-preparation/3.2.png)

Cấu hình các thông tin sau:

- Tên Subnet: `FCJ-Lab-subnet-private3`
- Chọn Availability Zone
- IPv4 CIDR block của VPC: `10.0.0.0/16`
- IPv4 CIDR block của Subnet: `10.0.32.0/20`
- Nhấn **Create subnet**

![3.3](/images/2-preparation/3.3.png)

Kết quả:

![3.4](/images/2-preparation/3.4.png)

Tương tự, tạo thêm một subnet khác:

- Tên Subnet: `FCJ-Lab-subnet-private4`
- Chọn Availability Zone khác với subnet vừa tạo
- IPv4 CIDR block của VPC: `10.0.0.0/16`
- IPv4 CIDR block của Subnet: `10.0.64.0/20`
- Nhấn **Create subnet**

![3.5](/images/2-preparation/3.5.png)

Kết quả:

![3.6](/images/2-preparation/3.6.png)
