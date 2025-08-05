---
title: "Tạo repository ECR và đẩy Docker image"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 1.2 </b> "
---

- **Tạo repository trên ECR bằng giao diện AWS Console**

    - Truy cập [ECR dashboard](https://console.aws.amazon.com/ecr/repositories).
    - Nhấn **Create repository**.
    - Chọn loại **Private**, đặt tên repository (ví dụ: `springboot-backend`) và giữ các thiết lập mặc định.
    - Nhấn **Create** để hoàn tất.

    ![image.png](/images/deploy_backend_ecr/create_repo.png)

- **Lấy lệnh push từ giao diện ECR**

    - Sau khi tạo xong, nhấn vào tên repository bạn vừa tạo.
    - Ở góc trên bên phải, chọn **View push commands**.
    - Giao diện sẽ hiển thị các lệnh CLI để:
        - Đăng nhập Docker vào ECR
        - Build Docker image
        - Tag image
        - Push image lên ECR

    ![image.png](/images/deploy_backend_ecr/view_push_cmd.png)

- **Đăng nhập vào ECR bằng Docker CLI**

    - Copy lệnh đăng nhập từ bước trên và chạy trên terminal:

    ```bash
    aws ecr get-login-password \
      --region ap-northeast-1 \
      | docker login \
      --username AWS \
      --password-stdin <aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com
    ```

    ![image.png](/images/deploy_backend_ecr/login_ecr.png)

- **Build Docker image từ mã nguồn local**

    - Mở terminal tại thư mục chứa Dockerfile, sau đó chạy:

    ```bash
    docker build -t springboot-backend .
    ```

    ![image.png](/images/deploy_backend_ecr/build_image.png)

- **Gán tag cho image theo định dạng ECR**

    ```bash
    docker tag springboot-backend:latest \
      <aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com/springboot-backend:latest
    ```

    ![image.png](/images/deploy_backend_ecr/tag_image.png)

- **Push Docker image lên ECR**

    ```bash
    docker push \
      <aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com/springboot-backend:latest
    ```

    ![image.png](/images/deploy_backend_ecr/push_image.png)

- **Kiểm tra hình ảnh đã đẩy lên ECR**

    - Quay lại repository trong AWS Console.
    - Mở tab **Images**.
    - Bạn sẽ thấy image kèm theo tag và thời gian push.

    ![image.png](/images/deploy_backend_ecr/ecr_result.png)
