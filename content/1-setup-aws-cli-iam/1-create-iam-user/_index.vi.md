---
title: "Tạo IAM User cho S3 & ECR"
date: "2025-07-17"
weight: 1 
chapter: false
pre: " <b> 1.1 </b> "
---

- **Mở trang IAM Users**

    - Truy cập [IAM dashboard](https://console.aws.amazon.com/iamv2/home).
    - Trong menu bên trái, dưới mục **Access management**, chọn **Users**.
    - Nhấn **Create user**.

    ![image.png](/images/01/1/1.png)

- **Nhập thông tin người dùng**

    - Ở mục **User name**, nhập: `dev-h2t`.
    - Không tick chọn *Provide user access to the AWS Management Console* (chỉ cần quyền truy cập programmatic).
    - Nhấn **Next**.

    ![image.png](/images/01/1/2.png)

- **Gán quyền – AmazonS3FullAccess**

    - Chọn **Attach policies directly**.
    - Tìm và chọn quyền: **AmazonS3FullAccess**.

    ![image.png](/images/01/1/3.png)

- **Gán quyền – AmazonEC2ContainerRegistryFullAccess**

    - Tiếp tục tìm và chọn quyền: **AmazonEC2ContainerRegistryFullAccess**.
    - Nhấn **Next**.

    ![image.png](/images/01/1/4.png)

- **Xác nhận và tạo**

    - Kiểm tra lại thông tin:
        - **User name**: `dev-h2t`
        - **Permissions**: AmazonS3FullAccess, AmazonEC2ContainerRegistryFullAccess
    - Nhấn **Create user**.

    ![image.png](/images/01/1/5.png)
