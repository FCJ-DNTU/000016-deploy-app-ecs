+++
title = "Triển khai Blue/Green và Service Scaling với Backend"
date = 2024
weight = 1
chapter = false
pre = "<b>8.1. </b>"
+++

#### Tạo backend service

Quay trở lại với trang console của ECS

- Chọn **Cluster**
- Chọn cluster **FCJ-Lab-cluster** mà chúng ta đã tạo ở phần trước

![8.1.1](/images/8-create-ecs-services/8.1.1.png)

Kéo xuống dưới cùng, trong mục Services, ấn **Create**

![8.1.2](/images/8-create-ecs-services/8.1.2.png)

#### ECS Service Environment

Cluster thì đã được tự động chọn, trong phần Compute option, chúng ta chỉ cần chọn Launch type, các cấu hình còn lại sẽ được thêm mặc định

![8.1.3](/images/8-create-ecs-services/8.1.3.png)

#### Deployment configuration

Trong phần này thì chúng ta sẽ cấu hình triển khai

- Application type: chọn **Service**
- Family: chọn `fcjresbar-task-be`, chọn Revision có nhãn là **LATEST**.
- Name: `backend`
- Service type và Desired tasks để mặc định

![8.1.4](/images/8-create-ecs-services/8.1.4.png)

Trong mục deployment options

- Deployment type: chọn **Blue/green deployment (powered by AWS CodeDeploy)**
- Deployment configuration: chọn **CodeDeployDefault.ECSCanary10Percent5Minutes**
- Service role for CodeDeploy: chọn role mà chúng ta đã tạo trong phần chuẩn bị

![8.1.5](/images/8-create-ecs-services/8.1.5.png)

#### Service discovery

Phần này quan trọng, để cho Frontend Service và Backend Service thì chúng ta phải cấu hình Service discovery cho Backend Service với namespace và serivce đã tạo trong phần 4 trước đó.

- Chọn **Use service discovery**
- Chọn **Select an existing namespace**, chọn namespace **fcjresbar.internal** mà chúng ta đã tạo trước đó
- Chọn **Select an existing service discovery service**, chọn service **backend**
- Các cấu hình còn lại để mặc định

![8.1.6](/images/8-create-ecs-services/8.1.6.png)

#### Networking

Giờ thì mình sẽ cho Service này biết là nó nên đặt host và các container ở trong vùng mạng nào, subnet nào.

- VPC: chọn VPC mà chúng ta đã tạo trước đó
- Subnet: chọn private subnet (**FCJ-Lab-subnet-private4**) mà chúng ta đã tạo trong phần chuẩn bị
- Security group: chọn **FCJ-Lab-sg-private**.

![8.1.7](/images/8-create-ecs-services/8.1.7.png)

{{% notice note %}}
Public IP nên tắt đi, vì traffic được chuyển tới Service thông qua Load Balancer.
{{% /notice %}}

#### Load balancing

Theo như trên thực tế, thì chúng ta sẽ không cần phải cấu hình Load balancing cho backend service, vì để test thì mình sẽ cần phải dùng một mạng riêng hoặc là VPN. Nhưng trong bài này thì mình sẽ cầu hình Load balancing, mở 2 listener cho production và test để cho các dev/tester có thể dùng để kiểm thử tính năng.

Đầu tiên, cấu hình một số thông tin

- Load balancing type: chọn **Application Load Balancer**
- Container: backend 5000:5000 (port ở đây sẽ là port của host và container)
- Chọn **Use an existing load balancer**
- Chọn **FCJ-Lab-alb** load balancer

![8.1.8](/images/8-create-ecs-services/8.1.8.png)

Trong phần listener, chúng ta sẽ tạo mẫu 2 listerns có các thông tin

- Production listener: port 5000, protocol HTTP
- Test listener: port 8080, protocol HTTP

Target group lần lượt sẽ có các thông số tự động như trong hình

![8.1.9](/images/8-create-ecs-services/8.1.9.png)

![8.1.10](/images/8-create-ecs-services/8.1.10.png)

![8.1.11](/images/8-create-ecs-services/8.1.11.png)

#### Service auto scaling

Giờ thì mình sẽ cấu hình scaling cho container

- Minimun: 1
- Maximun: 2
- Scaling policy type: Target tracking

![8.1.12](/images/8-create-ecs-services/8.1.12.png)

Cấu hình chính sách cho scaling

- Name: `ScaleAtThreshold75Percent`
- ECS service metric: **ECSServiceAverageCPUUtilization**
- Target value: 75
- Scale-out cooldown period: 120
- Scale-in cooldown period: 120
- Và ấn **Create** để tạo

![8.1.13](/images/8-create-ecs-services/8.1.13.png)

Chờ một xíu thì service sẽ được tạo xong

![8.1.14](/images/8-create-ecs-services/8.1.14.png)
