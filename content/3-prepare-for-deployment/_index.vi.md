+++  
title = "Chuẩn bị cho triển khai"  
date = 2024  
weight = 3  
chapter = false  
pre = "<b>3. </b>"  
+++

Để có thể triển khai được ứng dụng Node JS và Nginx với React, thì chúng ta cần phải chuẩn bị các Docker Images cho cả NodeJS và Nginx React. Docker Image đóng vai trò giống như Code đã được xây dựng và đóng gói (ngày trước thì Code được build xong thì sẽ nén lại).

Ở cuối bài trước thì chúng ta đã thực hiện thao tác build image cho cả NodeJS và Nginx React, và Docker Image của NodeJS đã có thể hoạt động được với ECS Service như bình thường, nhưng với Image của Nginx React thì cần phải thay đổi lại một chút, cho nên là ở trong phần này chúng ta sẽ thực hiện lại thao tác xây dựng image cho Nginx React.

#### Nội dung

1. [Tải Docker image lên ECR](3.1-push-image-to-ecr/)
2. [Tải Docker image lên Dockerhub](3.1-push-image-to-ecr/)
