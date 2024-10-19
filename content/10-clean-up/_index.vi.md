+++
title = "Dọn Dẹp Tài Nguyên"
date = 2024
weight = 10
chapter = false
pre = "<b>10. </b>"
+++

### Xoá Elastic Container Service

- Tìm kiếm và chọn **Elastic Container Service**.

![10.1](/images/10-clean-up/10.1.png)

- Chọn **FCJ-Lab-cluster**.

![10.2](/images/10-clean-up/10.2.png)

Trong phần **Services**:

- Chọn hai Service đang chạy.
- Nhấn **Delete service**.

![10.3](/images/10-clean-up/10.3.png)

- Nhập `delete`.
- Chọn **Delete**.

![10.4](/images/10-clean-up/10.4.png)

Sau khi đã dọn dẹp xong các service đang chạy, tiếp theo chúng ta sẽ xoá Cluster:

- Nhấn **Delete cluster**.

![10.5](/images/10-clean-up/10.5.png)

- Nhập `delete FCJ-Lab-cluster`.
- Chọn **Delete**.

![10.6](/images/10-clean-up/10.6.png)

Tiếp theo, chúng ta sẽ dọn dẹp các task definitions:

- Chọn **Task definitions**.
- Chọn task cần xóa.

![10.7](/images/10-clean-up/10.7.png)

- Tiếp tục làm theo hướng dẫn:
  - Chọn task definition.
  - Nhấn **Action**.
  - Chọn **Deregister**.

![10.8](/images/10-clean-up/10.8.png)

Lặp lại quy trình để xoá task còn lại.

![10.9](/images/10-clean-up/10.9.png)

- Thực hiện theo hướng dẫn.

![10.10](/images/10-clean-up/10.10.png)

Như vậy, bạn đã hoàn thành việc xoá ECS và các ECS services.

### Dọn Dẹp Elastic Container Registry

Trên giao diện AWS Console:

- Tìm kiếm và chọn **Elastic Container Registry**.

![10.11](/images/10-clean-up/10.11.png)

Bạn sẽ thấy hai kho lưu trữ đã tạo trước đó:

- Chọn **fcjresbar-be**.
- Nhấn **Delete**.

![10.12](/images/10-clean-up/10.12.png)

- Xác nhận hành động **Delete**.

![10.13](/images/10-clean-up/10.13.png)

Tương tự, thực hiện cho kho còn lại:

- Chọn **fcjresbar-fe**.
- Nhấn **Delete**.

![10.14](/images/10-clean-up/10.14.png)

- Xác nhận hành động **Delete**.

![10.15](/images/10-clean-up/10.15.png)

### Xoá Load Balancer

- Tìm và chọn **Load Balancer**.

![10.16](/images/10-clean-up/10.16.png)

- Chọn Load Balancer đã tạo.
- Nhấn **Action**.
- Chọn **Delete load balancer**.

![10.17](/images/10-clean-up/10.17.png)

- Nhập **confirm**.
- Chọn **Delete**.

![10.18](/images/10-clean-up/10.18.png)

### Dọn Dẹp Target Groups

Trong bảng bên trái:

- Chọn **Target Groups**.
- Chọn target group đã tạo.
- Nhấn **Action**.
- Chọn **Delete**.

![10.19](/images/10-clean-up/10.19.png)

### Dọn Dẹp RDS

Trên giao diện AWS Console:

- Tìm kiếm và chọn **RDS**.

![10.20](/images/10-clean-up/10.20.png)

- Chọn **Databases**.
- Chọn RDS instance đã tạo.
- Nhấn **Action**.
- Chọn **Delete**.

![10.21](/images/10-clean-up/10.21.png)

- Chọn **I acknowledge that upon instance deletion, automated backups, including system snapshots and point-in-time recovery, will no longer be available.**
- Nhập `delete me`.
- Nhấn **Delete**.

![10.22](/images/10-clean-up/10.22.png)
