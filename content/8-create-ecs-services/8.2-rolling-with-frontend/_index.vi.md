+++
title = "Triển khai Rolling với Frontend"
date = 2024
weight = 1
chapter = false
pre = "<b>8.2. </b>"
+++

Sau khi tạo Backend service xong, thì giờ mình sẽ tiến hành tạo Frontend service.

#### Tạo frontend service

Tiếp tục, trong trang console của cluster, ấn **Create** để tạo thêm Frontend service.

#### ECS Service Environment

Cluster thì đã được tự động chọn, trong phần Compute option, chúng ta chỉ cần chọn Launch type, các cấu hình còn lại sẽ được thêm mặc định

![8.2.1](/images/8-create-ecs-services/8.2.1.png)

#### Deployment configuration

Trong phần này thì chúng ta sẽ cấu hình triển khai

- Application type: chọn **Service**
- Family: chọn `fcjresbar-task-fe`, chọn Revision có nhãn là **LATEST**.
- Name: `frontend`
- Service type và Desired tasks để mặc định

![8.2.2](/images/8-create-ecs-services/8.2.2.png)

#### Networking

Giờ thì mình sẽ cho Service này biết là nó nên đặt host và các container ở trong vùng mạng nào, subnet nào.

- VPC: chọn VPC mà chúng ta đã tạo trước đó
- Subnet: chọn private subnet (**FCJ-Lab-subnet-private4**) mà chúng ta đã tạo trong phần chuẩn bị
- Security group: chọn **FCJ-Lab-sg-private**.

![8.2.3](/images/8-create-ecs-services/8.2.3.png)

{{% notice note %}}
Tương tự, Public IP nên tắt đi, vì traffic được chuyển tới Service thông qua Load Balancer.
{{% /notice %}}

#### Load balancing

Theo như trên thực tế, thì chúng ta sẽ không cần phải cấu hình Load balancing cho backend service, vì để test thì mình sẽ cần phải dùng một mạng riêng hoặc là VPN. Nhưng trong bài này thì mình sẽ cầu hình Load balancing, mở 2 listener cho production và test để cho các dev/tester có thể dùng để kiểm thử tính năng.

Đầu tiên, cấu hình một số thông tin

- Load balancing type: chọn **Application Load Balancer**
- Container: frontend 80:80 (port ở đây sẽ là port của host và container)
- Chọn **Use an existing load balancer**
- Chọn **FCJ-Lab-alb** load balancer
- Health check grace period: 30

![8.2.4](/images/8-create-ecs-services/8.2.4.png)

Trong phần listener, chúng ta sẽ tạo ra listener đã tạo trước đó

- Chọn **Use an existing listener**, chọn 80:HTTP

Target group, chọn target group mà mình đã tạo

- Chọn **Use an existing target group**, chọn **FCJ-Lab-fe-tg**

![8.2.5](/images/8-create-ecs-services/8.2.5.png)

![8.2.6](/images/8-create-ecs-services/8.2.6.png)

Chờ một xíu thì service sẽ được tạo xong

![8.2.7](/images/8-create-ecs-services/8.2.7.png)
