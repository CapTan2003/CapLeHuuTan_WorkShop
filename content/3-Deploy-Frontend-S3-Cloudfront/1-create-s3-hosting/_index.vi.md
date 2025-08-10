---
title: "Tạo & Cấu hình S3 Bucket để Hosting"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 3.1 </b> "
---

- **Mở dịch vụ Amazon S3**

    - Truy cập [Amazon S3 dashboard](https://s3.console.aws.amazon.com/s3/home).
    - Nhấn **Create bucket**.

    ![image.png](/images/03/1/1.png)

- **Cấu hình chung (General configuration)**

    - **AWS Region**: Chọn vùng triển khai (ví dụ: `Asia Pacific (Sydney) ap-southeast-2`).
    - **Bucket name**: Nhập tên bucket duy nhất (ví dụ: `h2t`).

    ![image.png](/images/03/1/2.png)

- **Quyền sở hữu đối tượng (Object Ownership)**

    - Chọn **ACLs disabled (recommended)** để đảm bảo tất cả các đối tượng thuộc quyền sở hữu của chủ bucket.

    ![image.png](/images/03/1/3.png)

- **Cài đặt chặn truy cập công khai (Block Public Access settings)**

    - Bỏ chọn **Block all public access** để cho phép bucket dùng làm static website hosting.
    - Tick xác nhận **I acknowledge...** để chấp nhận cảnh báo bucket sẽ public.

    ![image.png](/images/03/1/4.png)

- **Mã hóa mặc định (Default encryption)**

    - Giữ nguyên mặc định **Server-side encryption with Amazon S3 managed keys (SSE-S3)**.

    ![image.png](/images/03/1/5.png)

- **Tạo bucket**

    - Nhấn **Create bucket** để hoàn tất.

- **Chỉnh sửa quyền bucket (Edit Bucket Permissions)**

    - Vào tab **Permissions**.
    - Trong phần **Block public access (bucket settings)**, đảm bảo trạng thái là **Off**.
    - Tại **Bucket policy**, nhấn **Edit** và thêm đoạn policy sau:

    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::h2t/*"
        }
      ]
    }
    ```

    ![image.png](/images/03/1/6.png)

- **Lưu thay đổi**

    - Nhấn **Save changes** để áp dụng policy cho bucket.

    ![image.png](/images/03/1/7.png)
