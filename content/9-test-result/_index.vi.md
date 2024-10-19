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

![9.1](/images/9-test-result/9.1.png)

Sang tab Logs, chúng ta có thể thấy dịch vụ này cho ra các logs bình thường

![9.2](/images/9-test-result/9.2.png)

Còn lại là tương tự với backend

![9.3](/images/9-test-result/9.3.png)

![9.4](/images/9-test-result/9.4.png)

Vào trong giao diện của Load balacner, chọn **FCJ-Lab-alb**, chọn tab **Resource map**.

![9.5](/images/9-test-result/9.5.png)

Có thể thấy là hệ thống của chúng ta đã hoạt động bình thường. Nhớ sao chép lại DNS của Load Balancer.

#### Dùng thử ứng dụng

Dán DNS của Load Balancer vào trong thanh tìm kiếm, ấn enter và chúng ta sẽ có được giao diện đăng nhập

![9.6](/images/9-test-result/9.6.png)

Sau khi đăng nhập dưới dạng một người dùng có vai trò là User thì chúng ta sẽ thấy được giao diện dashboard

![9.7](/images/9-test-result/9.7.png)

Xem một số trang khác

![9.8](/images/9-test-result/9.8.png)

![9.9](/images/9-test-result/9.9.png)

Giờ thì thử thực hiện một chức năng nào đó, ở đây mình sẽ tạo một order

![9.10](/images/9-test-result/9.10.png)

Sau khi tạo một order xong thì chúng ta có thể thấy được thông tin của order đó

![9.11](/images/9-test-result/9.11.png)

Đăng xuất và đăng nhập vào người dùng với vai trò là Admin

![9.12](/images/9-test-result/9.12.png)

Đây là trang dashboard của Admin

![9.13](/images/9-test-result/9.13.png)

Vào trang order thì chúng ta có thể thấy được order mà chúng ta đã tạo vừa nãy

![9.14](/images/9-test-result/9.14.png)

Ok, như vậy thì hệ thống của chúng ta đã hoạt động bình thường, từ Database Server tới Backend và Frontend.
