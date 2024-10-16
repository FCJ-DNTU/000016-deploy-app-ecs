+++
title = "Chuẩn bị cho ECS"
date = 2024
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

#### Thêm subnet private

Ở giao diện quản lý VPC, ở bảng chọn phía bên trái

- Chọn **Subnet**
- Nhấn vào nút **Create subnet**

![3.1](/images/3-prepare-for-ecs/3.1.png)

- Chọn VPC **FCJ-Lab-vpc**

![3.2](/images/3-prepare-for-ecs/3.2.png)

Làm theo hướng dẫn

- Subnet name `FCJ-Lab-subnet-private3`
- Chọn Availability Zone
- IPv4 VPC CIDR block `10.0.0.0/16`
- IPv4 subnet CIDR block `10.0.32.0/20`
- Chọn **Create subnet**

![3.3](/images/3-prepare-for-ecs/3.3.png)

Kết quả

![3.4](/images/3-prepare-for-ecs/3.4.png)

Tương tự chúng ta tạo thêm một subnet nữa

- Subnet name `FCJ-Lab-subnet-private4`
- Chọn Availability Zone khác với zone của subnet chúng ta vừa tạo ở trên
- IPv4 VPC CIDR block `10.0.0.0/16`
- IPv4 subnet CIDR block `10.0.64.0/20`
- Chọn **Create subnet**

![3.5](/images/3-prepare-for-ecs/3.5.png)

Kết quả

![3.6](/images/3-prepare-for-ecs/3.6.png)

#### Tạo NAT Gateway

Trước tiên chúng ta cần tạo Elastic IPs để gán cho NAT Gateway. Ở giao diện quản lý VPC, ở mục chọn bên trái

- Chọn **Elastic IPs**
- Chọn **Allocate Elastic IP address**

![3.7](/images/3-prepare-for-ecs/3.7.png)

Cấu hình Elastic IP address

- Public IPv4 address pool **Amazon's pool of IPv4 address**
- Network border group **ap-southeast-1** nếu bạn sử dụng cùng region

![3.8](/images/3-prepare-for-ecs/3.8.png)

Ở tags optional

- Key `Name`
- Value `FCJ-Lab-IP`
- Chọn Allocate

![3.9](/images/3-prepare-for-ecs/3.9.png)

Tiếp theo chúng ta sẽ tiến hành tạo NAT Gateway. Ở mục chọn bên phải

- Chọn **NAT gateways**
- Chọn **Create NAT gateway**

![3.11](/images/3-prepare-for-ecs/3.11.png)

Cấu hình cho NAT gateway

- Name `FCJ-Lab-nat`
- Subnet chọn public subnet như hướng dẫn
- Connectivity type **Public**
- Chọn Elastic IP vừa tạo ở bước trên
- Chọn **Create NAT gateway**

![3.12](/images/3-prepare-for-ecs/3.12.png)

Sau khi tạo chúng ta sẽ đợi một chút cho tới khi state **Available**

![3.14](/images/3-prepare-for-ecs/3.14.png)

#### Route table

Ở giao diện quản lý VPC, ở bảng chọn bên trái

- Chọn **Route tables**
- Chọn **Create route table**

![3.15](/images/3-prepare-for-ecs/3.15.png)

- Name `FCJ-rtb-private`
- VPC **FCJ-Lab-vpc**
- Chọn **Create route table**

![3.16](/images/3-prepare-for-ecs/3.16.png)

Tiếp theo chúng ta sẽ gắn NAT gateway cho route table

- Chọn vào route table ta vừa tạo
- Chọn **Edit routes**

![3.17](/images/3-prepare-for-ecs/3.17.png)

- Chọn **Add route**
- Chọn Destination **0.0.0.0/0**
- Target **NAT Gateway**
- Chọn NAT gateway có tên **FCJ-Lab-nat** mà chúng ta vừa tạo ở bước trước

![3.18](/images/3-prepare-for-ecs/3.18.png)

Tiếp theo chúng ta sẽ thực hiện liên kết các private subnet tới Route table chúng ta vừa tạo. Ở trong phần thông tin của Route table chúng ta vừa tạo.

- Chọn **Subnet associations**
- Chọn **Edit subnet associations**

![3.19](/images/3-prepare-for-ecs/3.19.png)

- Chọn 2 subnet private mà chúng ta vừa tạo trước đó

![3.20](/images/3-prepare-for-ecs/3.20.png)

#### Tạo security groups

Ở quản lý VPC, bảng chọn phía bên trái

- Chọn **Security groups**
- Chọn **Create security group**

![3.22](/images/3-prepare-for-ecs/3.22.png)

Cấu hình cho security group

- Name `FCJ-Lab-sg-private`
- Description `Allow access for Internet`
- Chọn VPC chúng ta đã tạo

Ở phần Inbound rules

- Chọn **All traffic**
- Chọn **FCJ-Lab-sg-public**

![3.23](/images/3-prepare-for-ecs/3.23.png)

Ở phần Outbound rules

- Chọn **All traffic**
- Chọn **Anywhere IPv4**

![3.24](/images/3-prepare-for-ecs/3.24.png)

Tiếp theo chúng ta sẽ gán security group chúng ta vừa tạo vào security group **FCJ-Lab-sg-db**

Ở giao diện quản lý các Security groups

- Chọn **FCJ-Lab-sg-db**
- Chọn **Action**
- Chọn **Edit inbound rules**

![3.25](/images/3-prepare-for-ecs/3.25.png)

Ở phần Inbound Rule

- Chọn add rule
- Chọn MYSQL/Aurora
- Chọn Custom và chọn tới security group **FCJ-Lab-sg-private**
- Chọn **Save rules**

![3.26](/images/3-prepare-for-ecs/3.26.png)
