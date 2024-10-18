+++
title = "Kết quả kiểm tra"
date = 2024
weight = 9
chapter = false
pre = "<b>9. </b>"
+++

#### Quan sát

Trước khi dùng thử ứng dụng thì chúng ta nên quan sát các Service và Load balancer một xíu.

- Chọn **frontend** service, chúng ta sẽ vào trong trang chi tiết của service này
- Chọn tab **Task**

Ở đây thì chúng ta có thể thấy là một task đang chạy, vì nó đang quản lý một container ở trong đó (cũng đang chạy)

**INSERT IMAGE HERE**

Sang tab Logs, chúng ta có thể thấy dịch vụ này cho ra các logs bình thường

**INSERT IMAGE HERE**

Còn lại là tương tự với backend

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**

Vào trong giao diện của Load balacner, chọn **FCJ-Lab-alb**, chọn tab **Resource map**.

**INSERT IMAGE HERE**

Có thể thấy là hệ thống của chúng ta đã hoạt động bình thường. Nhớ sao chép lại DNS của Load Balancer.

#### Dùng thử ứng dụng

Dán DNS của Load Balancer vào trong thanh tìm kiếm, ấn enter và chúng ta sẽ có được giao diện đăng nhập

**INSERT IMAGE HERE**

Sau khi đăng nhập dưới dạng một người dùng có vai trò là User thì chúng ta sẽ thấy được giao diện dashboard

**INSERT IMAGE HERE**

Xem một số trang khác

**INSERT IMAGE HERE**

**INSERT IMAGE HERE**

Giờ thì thử thực hiện một chức năng nào đó, ở đây mình sẽ tạo một order

**INSERT IMAGE HERE**

Sau khi tạo một order xong thì chúng ta có thể thấy được thông tin của order đó

**INSERT IMAGE HERE**

Đăng xuất và đăng nhập vào người dùng với vai trò là Admin

**INSERT IMAGE HERE**

Đây là trang dashboard của Admin

**INSERT IMAGE HERE**

Vào trang order thì chúng ta có thể thấy được order mà chúng ta đã tạo vừa nãy

**INSERT IMAGE HERE**

Ok, như vậy thì hệ thống của chúng ta đã hoạt động bình thường, từ Database Server tới Backend và Frontend.
