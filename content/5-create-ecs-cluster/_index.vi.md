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

**INSERT IMAGE HERE**

Trong giao diện chính của ECS Console

- Chọn **Cluster**
- Ấn **Create cluster** để tạo một cluster mới

**INSERT IMAGE HERE**

Trong trang tạo Cluster

- Name: nhập `FCJ-Lab-cluster`
- Namespace: sẽ đươc tự động tạo
- Infrastructure: chọn **AWS Fargate**.

**INSERT IMAGE HERE**

Trong phần Monitoring

- Chọn **Use Container Insight**
- Ấn **Create** để tạo cluster

**INSERT IMAGE HERE**

{{% notice note %}}
Bật Container Insight là vì trong bài workshop sau chúng ta sẽ quan sát kĩ hơn về các ECS Service và các Container ở bên trong một Cluster.
{{% /notice %}}

Kết quả

**INSERT IMAGE HERE**
