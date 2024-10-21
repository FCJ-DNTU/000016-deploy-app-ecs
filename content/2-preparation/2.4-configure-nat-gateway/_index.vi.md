+++
title = "Cấu hình NAT gateway"
date = 2024
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++

#### Tạo NAT Gateway

Trước tiên, cần tạo Elastic IP để gán cho NAT Gateway. Từ bảng chọn bên trái:

- Chọn **Elastic IPs**
- Nhấn **Allocate Elastic IP address**

![3.7](/images/2-preparation/3.7.png)

Cấu hình Elastic IP:

- Public IPv4 address pool: **Amazon's pool of IPv4 address**
- Network border group: **ap-southeast-1** (nếu bạn dùng cùng region)

![3.8](/images/2-preparation/3.8.png)

Trong phần tags (tùy chọn):

- Key: `Name`
- Value: `FCJ-Lab-IP`
- Nhấn **Allocate**

![3.9](/images/2-preparation/3.9.png)

Tiếp theo, tạo NAT Gateway:

- Chọn **NAT gateways**
- Nhấn **Create NAT gateway**

![3.11](/images/2-preparation/3.11.png)

Cấu hình NAT Gateway:

- Name: `FCJ-Lab-nat`
- Chọn Subnet public đã tạo
- Connectivity type: **Public**
- Gắn Elastic IP vừa tạo
- Nhấn **Create NAT gateway**

![3.12](/images/2-preparation/3.12.png)

Sau khi tạo, chờ trạng thái **Available**.

![3.14](/images/2-preparation/3.14.png)
