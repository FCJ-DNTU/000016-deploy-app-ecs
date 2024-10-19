+++
title = "Tải Docker image lên Dockerhub"
date = 2024
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

#### Tải image lên Dockerhub

Ở trong bước trước thì chúng ta đã đẩy lên ECR thành công, trong bước này thì chúng ta sẽ tải image lên trên Dockerhub.

- Đăng xuất (xoá ECR Credential) ECR khỏi Docker với `docker logout`.
- Và tiến hành đăng nhập với `docker login -u "your-docker-username"`.

![3.2.1](/images/3-prepare-for-deployment/3.2.1.png)

Liệt kê lại các Image đang có, giờ chúng ta sẽ không build lại nữa, mà chỉ cần thêm một tag khác cho Dockerhub là được. Gắn tag xong thì liệt kê lại thì mình sẽ thấy tag mới đã được thêm.

![3.2.2](/images/3-prepare-for-deployment/3.2.2.png)

Giờ thì tiếp tục tải image này lên Dockerhub

![3.2.3](/images/3-prepare-for-deployment/3.2.3.png)

Và kiểm tra lại kết quả

![3.2.4](/images/3-prepare-for-deployment/3.2.4.png)

Như vậy thì chúng ta đã tải image lên cả ECR và Dockerhub. Giờ thì bạn có thể dùng image ở bất cứ Registry nào để triển khai Frontend Service.
