+++
title = "Giới thiệu"
date = 2024
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

#### Kiến trúc

![1](/images/1-introduction/1.1.png)

#### Amazon Elastic Container Service (ECS)

**Amazon Elastic Container Service (Amazon ECS)**, theo định nghĩa của AWS là một dịch vụ quản lý container có khả năng mở rộng cao, dễ dàng run, stop, hay quản lý docker container ở trong một cluster. Bạn có thể host một serverless infrastructure bằng cách chạy service hay task sử dụng Fargate launch type hoặc sử dụng EC2 launch type để chạy các EC2 instance. Amazon ECS được so sánh với Kubernetes, Docker Swarm và Azure Container Instances.

Amazon ECS chạy các containers trong cluster gồm nhiều Amazon EC2 instance được cài sẵn Docker. Dịch vụ này xử lý việc cài đặt container, mở rộng quy mô, giám sát và quản lý những instance này (launch/stop) thông qua cả API và AWS Management Console.

Amazon Elastic Container Service cho phép đơn giản hóa chế độ xem các EC2 instance thành một pool tài nguyên, chẳng hạn như CPU và bộ nhớ.

Bạn có thể sử dụng Amazon ECS để cài đặt container thông qua cluster và dựa vào nguồn tài nguyên mà bạn cần, chính sách độc lập hay khả năng thay đổi. Với Amazon ECS, bạn không phải vận hành hệ thống quản lý cấu hình và quản lý cụm của riêng mình hoặc lo lắng về việc mở rộng cơ sở hạ tầng quản lý của mình.

Amazon ECS là một dịch vụ theo region, nó đơn giản hoá việc chạy ứng dụng containers trên nhiều AZ trong cùng một Region. Bạn có thể tạo một ECS cluster bên trong một VPC mới hoặc cũ. Sau khi một cluster được khởi tạo và chạy, bạn có thể định nghĩa các task và services mà nó chỉ định Docker container image sẽ chạy thông qua clusters.

#### Amazon ECS Task definitions

Trong Amazon ECS, **Task definitions** được tạo ra để xác định thông số thiết lập trước khi khởi chạy các Docker container trong Amazon ECS. Các thông số có thể được thiết lập trong task definition là:

- Docker image được sử dụng.
- Lượng CPU và memory được sử dụng trong task hay mỗi container trong task đó.
- Cách thức khởi chạy (Xác định hạ tầng sẽ chạy)
- Phương thức kết nối mạng cho các container.
- Cấu hình log cho task.
- Các hướng xử lý khi chạy task.
- Các lệnh sẽ thực thi khi khởi chạy task.
- Xác định các volume sẽ sử dụng.
- IAM role được sử dụng để thực thi task.

#### Amazon ECS Services

Trong Amazon ECS, **Service** là một cấu hình cho phép chạy một hoặc nhiều các task liên tiếp nhau trong cluster và tự động duy trì chúng. Các task và các dịch vụ có thể được chạy trên các hạ tầng serverless (quản lý bởi AWS Fargate) hoặc thông quan hạ tầng do bạn quản lý như EC2 cluster.

#### Amazon ECS Cluster

Một **Amazon ECS Cluster** là một đơn vị quản lý tài nguyên sử dụng để triển khai container trong AWS ECS. Khi bạn định nghĩa đầy đủ task definitions và services cho ECS Cluster, ECS Cluster sẽ tạo tài nguyên cần thiết để triển khai container.
Một ECS cluster là một nhóm (hoặc một) máy ảo chứa các container.

#### Cluster Scaling và Service Scaling

Trong ECS, một **Cluster** là một nhóm các tài nguyên (instance EC2 hoặc Fargate) được sử dụng để chạy các container. Cluster Scaling là quá trình tăng hoặc giảm số lượng tài nguyên trong cluster dựa trên yêu cầu của workload. Điều này có thể được thực hiện thủ công hoặc tự động bằng cách sử dụng Auto Scaling. Với Auto Scaling, cluster sẽ tự động thêm hoặc xóa các instance dựa trên số lượng task, sử dụng CPU, hoặc RAM, giúp tối ưu hóa tài nguyên.

**Service Scaling** trong ECS là việc điều chỉnh số lượng task (container) mà một service đang chạy. ECS hỗ trợ Auto Scaling cho service dựa trên các quy tắc cụ thể, chẳng hạn như mức sử dụng CPU hoặc Memory, số lượng request đến, hoặc các chỉ số khác được thu thập bởi Amazon CloudWatch.

#### Rolling và Blue/Green Deployment

**Rolling Deployment** là phương pháp cập nhật container của một service từng bước, nghĩa là các phiên bản mới của container sẽ được triển khai dần dần để thay thế các phiên bản cũ. ECS sẽ ngừng chạy các container cũ và tạo các container mới từ từ, đảm bảo có đủ tài nguyên và không gây gián đoạn dịch vụ. Rolling Deployment là cách triển khai an toàn, giúp giảm thiểu downtime, tuy nhiên có thể tốn nhiều thời gian hơn nếu có nhiều container.

**Blue/Green Deployment** là một chiến lược triển khai khác trong ECS, giúp giảm thiểu rủi ro khi cập nhật phần mềm. Trong phương pháp này:

- **Blue** là phiên bản hiện tại của ứng dụng đang chạy.
- **Green** là phiên bản mới của ứng dụng được triển khai song song với phiên bản Blue. Sau khi Green đã sẵn sàng và kiểm tra thành công, traffic sẽ được chuyển từ phiên bản Blue sang Green, thông qua Load Balancer. Nếu có bất kỳ vấn đề nào xảy ra với Green, traffic có thể được chuyển lại về Blue mà không có downtime. AWS CodeDeploy và Application Load Balancer thường được sử dụng để hỗ trợ Blue/Green Deployment.
