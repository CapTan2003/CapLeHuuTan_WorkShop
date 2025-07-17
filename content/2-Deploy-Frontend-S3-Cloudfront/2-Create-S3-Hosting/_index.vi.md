---
title: "Tạo và cấu hình S3 Bucket để hosting"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

- **Truy cập [Amazon S3 Console](https://s3.console.aws.amazon.com/s3)**

- **Tạo bucket mới để chứa frontend**

    - Nhấn **Create bucket**
    - Đặt tên bucket duy nhất toàn cục (ví dụ: `my-frontend-app`)
    - Chọn vùng AWS phù hợp
    - **Bỏ chọn** mục **Block all public access** (để website có thể truy cập công khai)
    - Tích chọn xác nhận cảnh báo
    - Nhấn **Create bucket**

    ![image.png](/images/deploy_frontend/create_s3_bucket.png)

- **Bật tính năng Static Website Hosting**

    - Vào bucket → chọn tab **Properties**
    - Cuộn xuống phần **Static website hosting**
    - Nhấn **Edit**
    - Bật **Enable static website hosting**
    - Điền **Index document**: `index.html`
    - Điền **Error document**: `index.html` (cho SPA routing)
    - Nhấn **Save changes**

    ![image.png](/images/deploy_frontend/enable_static_hosting.png)

- **Cấu hình quyền truy cập công khai cho bucket**

    - Vào tab **Permissions**
    - Cuộn xuống phần **Bucket policy**
    - Nhấn **Edit**
    - Dán đoạn policy sau (thay `my-frontend-app` bằng tên bucket của bạn):

    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::my-frontend-app/*"
        }
      ]
    }
    ```

    - Nhấn **Save**

    ![image.png](/images/deploy_frontend/set_bucket_policy.png)

- **Xác nhận bucket đã công khai**

    - Quay lại tab **Objects**
    - Bạn có thể truy cập tệp qua URL công khai như sau:

    ```
    http://my-frontend-app.s3-website-ap-northeast-1.amazonaws.com
    ```

---

Khi bạn sẵn sàng, mình sẽ viết tiếp bước 3: Thiết lập CloudFront để phân phối nội dung tĩnh.
