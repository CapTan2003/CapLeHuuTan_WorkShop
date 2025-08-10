---
title: "Cấu hình AWS CLI trên máy của bạn"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 1.3 </b> "
---

- **Cài đặt AWS CLI (nếu chưa có)**

    - Tải và cài đặt AWS CLI từ [hướng dẫn cài đặt chính thức](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
    - Kiểm tra cài đặt bằng cách chạy:
      ```bash
      aws --version
      ```

    ![image.png](/images/01/3/1.png)

- **Mở Terminal và chạy AWS Configure**

    - Mở **Terminal** (macOS/Linux) hoặc **Command Prompt** (Windows).
    - Chạy lệnh:
      ```bash
      aws configure
      ```

    ![image.png](/images/01/3/2.png)

- **Nhập thông tin xác thực AWS**

    - **AWS Access Key ID**: Nhập Access Key ID từ bước trước.
    - **AWS Secret Access Key**: Nhập Secret Access Key đã lưu.
    - **Default region name**: Nhập region ưa thích (ví dụ: `ap-southeast-2`).
    - **Default output format**: Nhập `json` (khuyến nghị).

    ![image.png](/images/01/3/3.png)

- **Xác minh cấu hình AWS CLI**

    - Kiểm tra cấu hình bằng cách chạy:
      ```bash
      aws sts get-caller-identity
      ```
    - Bạn sẽ thấy kết quả hiển thị **UserID**, **Account** và **ARN**.
    - Điều này xác nhận AWS CLI đã được cấu hình và xác thực thành công.

    ![image.png](/images/01/3/4.png)
