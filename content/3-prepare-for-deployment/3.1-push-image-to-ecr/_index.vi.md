+++
title = "Tải Docker image lên ECR"
date = 2024
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

#### Tải image lên ECR

Trước tiên, vào trong giao diện ECR Console

- Chọn image của Frontend
- Copy **URI**

**INSERT IMAGE HERE**

Vào lại EC2 mà chúng ta đã cấu hình trước đó

- Vào trong thư mục của dự án.
- Vào trong thư mục **frontend**.
- Dùng câu lệnh bên dưới và thay "image-uri" thành image uri tương ứng của bạn.

```bash
sudo docker build . -t "image-uri":latest -f Dockerfile.prod
```

**INSERT IMAGE HERE**

{{% notice note %}}
Ở trong thư mục **frontend** này, bạn có thể thấy có 2 docker file là **Dockerfile** và **Dockerfile.prod** và 2 file config của nginx là **default.conf** và **default.conf.template**. Với docker file, thì **Dockerfile.prod** nó khác biệt ở chỗ là Docker sẽ sao chép file **default.conf.template** sang thư mục **/etc/nginx/templates** để trong quá trình build thì có thể dùng lệnh `envsubst` để có thể thay thế các tham số **${BACKEND_HOST}** và **${BACKEND_PORT}** trong file **default.conf.template**. Sau khi được thay thế xong thì file template này sẽ được nginx dùng để cấu hình. Hai thông số này khi cấu hình về sau thì mình sẽ giải thích rõ hơn.
{{% /notice %}}

Sau khi build image xong, thì giờ chúng ta sẽ đổi sang Root User để có thể tải image lên trên ECR.

```bash
docker push "image-uri":latest
```

**INSERT IMAGE HERE**

Giờ thì mình sẽ vào lại trong ECR Console

- Vào trong frontend repository (tên là `fcjresbar-fe`)

**INSERT IMAGE HERE**

Ok vậy thì chúng ta đã có thể đẩy được image mới lên trên ECR. Trong bài này mình sẽ dùng `latest` để gắn nhãn cho Docker image, nhưng thực chất thì các bạn nên đánh số version cho mỗi tag mà các bạn thay đổi để quản lý version tốt hơn, có thể tham khảo hơn ở đây: [https://semver.org/](https://semver.org/)
