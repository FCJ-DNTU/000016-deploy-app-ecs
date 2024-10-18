+++
title = "Đăng ký namespace trong Cloud Map"
date = 2024
weight = 4
chapter = false
pre = "<b>4. </b>"
+++

Các bước sắp tới thì chúng ta sẽ cấu hình Frontend và Backend ở trong từng ECS Service riêng biệt, tuy nhiên thì chúng ta không có hình thức giao tiếp giữa các Services với nhau (mặc dù ở trong cùng một Cluster) thế nên là trong phần này thì chúng ta sẽ phải cấu hình Namespace và Service ở trong Cloud Map.

Khi có được Serivce Discovery Name thì Frontend Service có thể dùng cái "tên" đó để phân giải ra được địa chỉ IP của Backend Service, khi đó thì Frontend Service có thể giao tiếp được với Backend Service.

#### Tạo namespace

Tìm `Cloud Map` ở trên trang console

- Chọn Cloud Map

**INSERT IMAGE HERE**

Trong mục namespace

- Ấn **Create namespace**

**INSERT IMAGE HERE**

Trong giao diện tạo namespace

- Name: `fcjresbar.internal`
- Description: `Use for internal API Calls and DNS`
- Instance discovery: chọn **API calls and DNS queries in VPCs**.

**INSERT IMAGE HERE**

Tiếp theo

- Chọn VPC mà chúng ta đã tạo trước đó
- TTL (Time to live): 20s
- Ấn **Create namespace**

**INSERT IMAGE HERE**

Namespace của chúng ta đã được tạo thành công

**INSERT IMAGE HERE**

#### Tạo service trong namespace

Giờ thì chúng ta sẽ tạo service trong Namespace mới tạo

- Vào lại thông tin của namespace mới tạo
- Kéo xuống dưới cùng
- Ấn **Create service**

**INSERT IMAGE HERE**

Điền một số thông tin sau để tạo service

- Name: `backend`
- Description: `Backend Service Discovery Name`
- Discoverable by: chọn **API and DNS**

**INSERT IMAGE HERE**

{{% notice note %}}
Với service name là **backend**, thì chúng ta sẽ có tên đầy đủ của Service Discovery cho Backend là `backend.fcjresbar.internal`, nhớ sao chéo lại tên này vì chúng ta cần nó để cấu hình Task Definition cho Frontend service.
{{% /notice %}}

Tiếp theo trong phần DNS Configuration

- Routing policy: chọn **WEIGHTED**
- Record type: **A** (cho IPv4)
- TTL: 300
- Health check option: chọn No health check

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**

Giờ chúng ta phải chờ một lúc để service có thể được tạo xong

**INSERT IMAGE HERE**
