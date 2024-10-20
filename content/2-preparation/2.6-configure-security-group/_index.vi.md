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

Cấu hình Inbound rules:

- Chọn **All traffic**
- Source: **FCJ-Lab-sg-public**

![3.23](/images/2-preparation/3.23.png)

Cấu hình Outbound rules:

- Chọn **All traffic**
- Destination: **Anywhere IPv4**

![3.24](/images/2-preparation/3.24.png)

Liên kết Security Group với nhóm **FCJ-Lab-sg-db**:

- Chọn **FCJ-Lab-sg-db**
- Nhấn **Action**, sau đó chọn **Edit inbound rules**

![3.25](/images/2-preparation/3.25.png)

Cấu hình Inbound Rule:

- Nhấn **Add rule**
- Chọn **MYSQL/Aurora**
- Source: Chọn Security Group **FCJ-Lab-sg-private**
- Nhấn **Save rules**

![3.26](/images/2-preparation/3.26.png)

#### Tạo CodeDeploy Role

Tìm kiếm và chọn **IAM**

![3.29](/images/2-preparation/3.29.png)

- Chọn **Roles**
- Nhấn **Create role**

![3.30](/images/2-preparation/3.30.png)

Trong phần Use case, chọn:

- Service or use case: `CodeDeploy`
- Chọn **CodeDeploy - ECS**
- Nhấn **Next**

![3.31](/images/2-preparation/3.31.png)

- Nhấn **Next**

![3.32](/images/2-preparation/3.32.png)

- Role name: `CodeDeployServiceRole`

![3.33](/images/2-preparation/3.33.png)

- Nhấn **Create role**
