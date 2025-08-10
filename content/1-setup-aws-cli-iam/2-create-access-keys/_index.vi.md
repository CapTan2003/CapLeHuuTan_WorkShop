---
title: "Tạo Access Key cho IAM User"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 1.2 </b> "
---

- **Mở trang IAM Users**

    - Truy cập [IAM dashboard](https://console.aws.amazon.com/iamv2/home).
    - Trong menu bên trái, chọn **Users**.
    - Chọn user vừa tạo (ví dụ: `dev-h2t`).

    ![image.png](/images/01/2/1.png)

- **Tạo Access Key**

    - Trong trang chi tiết user, chọn tab **Security credentials**.
    - Ở mục **Access keys**, bấm **Create access key**.

    ![image.png](/images/01/2/2.png)

- **Chọn loại Access Key**

    - Chọn **Command Line Interface (CLI)**.
    - Tích vào ô xác nhận: *I understand the above recommendation…*
    - Bấm **Next**.

    ![image.png](/images/01/2/3.png)

- **Tạo và lưu Access Key**

    - Bấm **Create access key**.
    - Sao chép **Access key** và **Secret access key** vào file `.csv` hoặc lưu ở nơi an toàn.
    - **Lưu ý:** Sau khi đóng cửa sổ, bạn **sẽ không thể xem lại** Secret access key.

    ![image.png](/images/01/2/4.png)
