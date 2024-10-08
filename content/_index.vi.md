+++
title = "Deploy Application on Docker"
date = 2024
weight = 1
chapter = false
+++

# Deploy Application on Docker

#### Tổng quan
Trong bài lab đầu tiên này, bạn sẽ tạo mới **tài khoản AWS** đầu tiên của mình, tạo **MFA** (Multi-factor Authentication) để gia tăng bảo mật tài khoản của bạn. Bước tiếp theo bạn sẽ tạo **Admin Group**, **Admin User** để quản lý quyền truy cập vào các tài nguyên trong tài khoản của mình thay vì sử dụng user root.\
Cuối cùng, nếu quá trình xác thực tài khoản của bạn có vấn đề, bạn sẽ được hướng dẫn hỗ trợ xác thực tài khoản với **AWS Support**.

#### Tài khoản AWS (AWS Account)
**Tài khoản AWS** là phương tiện để bạn có thể truy cập và sử dụng những tài nguyên và dịch vụ của AWS. Theo mặc định, mỗi tài khoản AWS sẽ có một *root user*. *Root user* có toàn quyền với tài khoản AWS của bạn, và quyền hạn của root user không thể bị giới hạn. Nếu bạn mới sử dụng tài khoản AWS lần đầu tiên, bạn sẽ truy cập vào tài khoản dưới danh nghĩa của *root user*.

{{% notice note %}}
Chính vì quyền hạn của **root user** không thể bị giới hạn, AWS khuyên bạn không nên sử dụng trực tiếp *root user* cho bất kỳ công tác nào. Thay vào đó, bạn nên tạo ra một *IAM User* và trao quyền quản trị cho *IAM User* đó để dễ dàng quản lý và giảm thiểu rủi ro.
{{% /notice %}}




#### Nội dung chính

1. [Giới thiệu](1-introduction/)
2. [Triển khai ở Local](2-deploy-local/)
3. [Các bước chuẩn bị](3-preparation/)
4. [Cấu hình RDS](4-configure-rds/)
5. [Cấu hình EC2 Instance](5-configure-ec2/)
6. [Triển khai bằng Docker image](6-docker-image/)
7. [Triển khai bằng Docker compose](7-docker-compose/)
8. [Đẩy image](8-push-image/)
9. [Dọn dẹp tài nguyên](9-clean-up/)