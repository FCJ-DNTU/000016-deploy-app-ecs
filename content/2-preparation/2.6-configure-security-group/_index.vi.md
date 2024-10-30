+++
title = "Cấu hình Security Group"
date = 2024
weight = 6
chapter = false
pre = "<b>2.6 </b>"
+++

#### Tạo Security Groups

Trong bảng chọn bên trái:

- Chọn **Security groups**
- Nhấn **Create security group**

![3.22](/images/2-preparation/3.22.png)

Cấu hình Security Group:

- Name: `FCJ-Lab-sg-private`
- Description: `Allow access for Internet`
- Chọn VPC vừa tạo

Cấu hình Inbound rules, tạo inbound một cái trỏ đến public security group, một cái trỏ vào chính private security group:

- Chọn **All traffic**
- Source: **FCJ-Lab-sg-public**

- Tạo thêm một inbound

![3.23](/images/2-preparation/3.23.png)

Tương tự cấu hình thêm cho cổng private security group

- Chọn **All traffic**
- Destination: **Anywhere IPv4**
- Source: **FCJ-Lab-sg-private**

![3.23](/images/2-preparation/3.23.1.png)

Cấu hình Outbound rules:

- Chọn **All traffic**
- Destination: **Anywhere IPv4**
- Source: **FCJ-Lab-sg-public**

![3.24](/images/2-preparation/3.24.png)

Liên kết Security Group với nhóm **FCJ-Lab-sg-db**:

- Chọn **FCJ-Lab-sg-db**
- Nhấn **Action**, sau đó chọn **Edit inbound rules**

![3.25](/images/2-preparation/3.26.png)

Cấu hình Inbound Rule:

- Nhấn **Add rule**
- Chọn **MYSQL/Aurora**
- Source: Chọn Security Group **FCJ-Lab-sg-private**
- Nhấn **Save rules**

![3.26](/images/2-preparation/3.27.png)
