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

**INSERT IMAGE HERE**

Liệt kê lại các Image đang có, giờ chúng ta sẽ không build lại nữa, mà chỉ cần thêm một tag khác cho Dockerhub là được. Gắn tag xong thì liệt kê lại thì mình sẽ thấy tag mới đã được thêm.

**INSERT IMAGE HERE**

Giờ thì tiếp tục tải image này lên Dockerhub

**INSERT IMAGE HERE**

Và kiểm tra lại kết quả

**INSERT IMAGE HERE**

Như vậy thì chúng ta đã tải image lên cả ECR và Dockerhub. Giờ thì bạn có thể dùng image ở bất cứ Registry nào để triển khai Frontend Service.
