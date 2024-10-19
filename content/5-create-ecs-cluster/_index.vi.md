+++
title = "Tạo ECS Cluster"
date = 2024
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

#### Tạo ECS Cluster

Trên thanh tìm kiếm

- Gõ `ECS`
- Chọn **Elastic Container Service**

![5.1](/images/5-create-ecs-cluster/5.1.png)

Trong giao diện chính của ECS Console

- Chọn **Cluster**
- Ấn **Create cluster** để tạo một cluster mới

![5.2](/images/5-create-ecs-cluster/5.2.png)

Trong trang tạo Cluster

- Name: nhập `FCJ-Lab-cluster`
- Namespace: sẽ đươc tự động tạo
- Infrastructure: chọn **AWS Fargate**.

![5.3](/images/5-create-ecs-cluster/5.3.png)

Trong phần Monitoring

- Chọn **Use Container Insight**
- Ấn **Create** để tạo cluster

![5.4](/images/5-create-ecs-cluster/5.4.png)

{{% notice note %}}
Bật Container Insight là vì trong bài workshop sau chúng ta sẽ quan sát kĩ hơn về các ECS Service và các Container ở bên trong một Cluster.
{{% /notice %}}

Kết quả

![5.5](/images/5-create-ecs-cluster/5.5.png)
