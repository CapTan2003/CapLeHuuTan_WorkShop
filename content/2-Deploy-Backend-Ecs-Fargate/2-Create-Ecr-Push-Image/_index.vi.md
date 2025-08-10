---
title: "Tạo ECR Repository và Push Docker Image"
date: "2025-08-10"
weight: 1
chapter: false
pre: " <b> 2.2 </b> "
---

- **Mở dịch vụ Amazon ECR**

    - Truy cập [Amazon ECR dashboard](https://console.aws.amazon.com/ecr/repositories).
    - Nhấp **Create repository**.

    ![image.png](/images/02/2/1.png)

- **Cấu hình repository**

    - **Visibility settings**: Chọn **Private**.
    - **Repository name**: `h2t/backend`.
    - **Tag immutability**: Chọn **Mutable**.

    ![image.png](/images/02/2/2.png)

- **Cấu hình mã hóa**

    - **Encryption type**: AES-256 (mặc định).
    - Nếu cần quản lý khóa tùy chỉnh, chọn **AWS KMS**.

    ![image.png](/images/02/2/3.png)

- **Tạo repository**

    - Nhấp **Create repository**.
    - Sau khi tạo, lưu lại **Repository URI**:
      ```
      740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend
      ```

    ![image.png](/images/02/2/4.png)

- **Xem lệnh Push**

    - Trong trang chi tiết repository, nhấp **View push commands**.
    - AWS sẽ hiển thị các lệnh bao gồm:
        1. Xác thực
        2. Build Docker image
        3. Tag image
        4. Push image

    ![image.png](/images/02/2/5.png)

- **Xác thực Docker với ECR**

    ```bash
    aws ecr get-login-password --region ap-southeast-2 \
    | docker login --username AWS \
    --password-stdin 740994884477.dkr.ecr.ap-southeast-2.amazonaws.com
    ```

    ![image.png](/images/02/2/6.png)

- **Build Docker image**

    ```bash
    docker build -t h2t/backend .
    ```

    ![image.png](/images/02/2/7.png)

- **Tag Docker image**

    ```bash
    docker tag h2t/backend:latest \
    740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend:latest
    ```

- **Push Docker image lên ECR**

    ```bash
    docker push 740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend:latest
    ```

    ![image.png](/images/02/2/8.png)

