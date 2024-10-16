+++  
title = "Chuẩn bị cho ECS"  
date = 2024  
weight = 3  
chapter = false  
pre = "<b>3. </b>"  
+++

#### Thêm Subnet Private

Trong giao diện quản lý VPC, từ bảng chọn bên trái:

- Chọn **Subnet**
- Nhấn vào nút **Create subnet**

![3.1](/images/3-prepare-for-ecs/3.1.png)

- Chọn VPC **FCJ-Lab-vpc**

![3.2](/images/3-prepare-for-ecs/3.2.png)

Cấu hình các thông tin sau:

- Tên Subnet: `FCJ-Lab-subnet-private3`
- Chọn Availability Zone
- IPv4 CIDR block của VPC: `10.0.0.0/16`
- IPv4 CIDR block của Subnet: `10.0.32.0/20`
- Nhấn **Create subnet**

![3.3](/images/3-prepare-for-ecs/3.3.png)

Kết quả:

![3.4](/images/3-prepare-for-ecs/3.4.png)

Tương tự, tạo thêm một subnet khác:

- Tên Subnet: `FCJ-Lab-subnet-private4`
- Chọn Availability Zone khác với subnet vừa tạo
- IPv4 CIDR block của VPC: `10.0.0.0/16`
- IPv4 CIDR block của Subnet: `10.0.64.0/20`
- Nhấn **Create subnet**

![3.5](/images/3-prepare-for-ecs/3.5.png)

Kết quả:

![3.6](/images/3-prepare-for-ecs/3.6.png)

#### Tạo NAT Gateway

Trước tiên, cần tạo Elastic IP để gán cho NAT Gateway. Từ bảng chọn bên trái:

- Chọn **Elastic IPs**
- Nhấn **Allocate Elastic IP address**

![3.7](/images/3-prepare-for-ecs/3.7.png)

Cấu hình Elastic IP:

- Public IPv4 address pool: **Amazon's pool of IPv4 address**
- Network border group: **ap-southeast-1** (nếu bạn dùng cùng region)

![3.8](/images/3-prepare-for-ecs/3.8.png)

Trong phần tags (tùy chọn):

- Key: `Name`
- Value: `FCJ-Lab-IP`
- Nhấn **Allocate**

![3.9](/images/3-prepare-for-ecs/3.9.png)

Tiếp theo, tạo NAT Gateway:

- Chọn **NAT gateways**
- Nhấn **Create NAT gateway**

![3.11](/images/3-prepare-for-ecs/3.11.png)

Cấu hình NAT Gateway:

- Name: `FCJ-Lab-nat`
- Chọn Subnet public đã tạo
- Connectivity type: **Public**
- Gắn Elastic IP vừa tạo
- Nhấn **Create NAT gateway**

![3.12](/images/3-prepare-for-ecs/3.12.png)

Sau khi tạo, chờ trạng thái **Available**.

![3.14](/images/3-prepare-for-ecs/3.14.png)

#### Tạo Route Table

Trong giao diện quản lý VPC, từ bảng chọn bên trái:

- Chọn **Route tables**
- Nhấn **Create route table**

![3.15](/images/3-prepare-for-ecs/3.15.png)

Cấu hình Route Table:

- Name: `FCJ-rtb-private`
- Chọn VPC: **FCJ-Lab-vpc**
- Nhấn **Create route table**

![3.16](/images/3-prepare-for-ecs/3.16.png)

Liên kết NAT Gateway với Route Table:

- Chọn route table vừa tạo
- Nhấn **Edit routes**

![3.17](/images/3-prepare-for-ecs/3.17.png)

- Nhấn **Add route**
- Destination: **0.0.0.0/0**
- Target: **NAT Gateway**
- Chọn NAT Gateway **FCJ-Lab-nat** vừa tạo

![3.18](/images/3-prepare-for-ecs/3.18.png)

Liên kết các Subnet private với Route Table:

- Trong mục thông tin của Route Table, chọn **Subnet associations**
- Nhấn **Edit subnet associations**

![3.19](/images/3-prepare-for-ecs/3.19.png)

- Chọn hai Subnet private vừa tạo

![3.20](/images/3-prepare-for-ecs/3.20.png)

#### Tạo Security Groups

Trong bảng chọn bên trái:

- Chọn **Security groups**
- Nhấn **Create security group**

![3.22](/images/3-prepare-for-ecs/3.22.png)

Cấu hình Security Group:

- Name: `FCJ-Lab-sg-private`
- Description: `Allow access for Internet`
- Chọn VPC vừa tạo

Cấu hình Inbound rules:

- Chọn **All traffic**
- Source: **FCJ-Lab-sg-public**

![3.23](/images/3-prepare-for-ecs/3.23.png)

Cấu hình Outbound rules:

- Chọn **All traffic**
- Destination: **Anywhere IPv4**

![3.24](/images/3-prepare-for-ecs/3.24.png)

Liên kết Security Group với nhóm **FCJ-Lab-sg-db**:

- Chọn **FCJ-Lab-sg-db**
- Nhấn **Action**, sau đó chọn **Edit inbound rules**

![3.25](/images/3-prepare-for-ecs/3.25.png)

Cấu hình Inbound Rule:

- Nhấn **Add rule**
- Chọn **MYSQL/Aurora**
- Source: Chọn Security Group **FCJ-Lab-sg-private**
- Nhấn **Save rules**

![3.26](/images/3-prepare-for-ecs/3.26.png)

#### Tạo CodeDeploy Role

Tìm kiếm và chọn **IAM**

![3.29](/images/3-prepare-for-ecs/3.29.png)

- Chọn **Roles**
- Nhấn **Create role**

![3.30](/images/3-prepare-for-ecs/3.30.png)

Trong phần Use case, chọn:

- Service or use case: `CodeDeploy`
- Chọn **CodeDeploy - ECS**
- Nhấn **Next**

![3.31](/images/3-prepare-for-ecs/3.31.png)

- Nhấn **Next**

![3.32](/images/3-prepare-for-ecs/3.32.png)

- Role name: `CodeDeployServiceRole`

![3.33](/images/3-prepare-for-ecs/3.33.png)

- Nhấn **Create role**

Như vậy, bạn đã hoàn thành các bước chuẩn bị cho workshop.
