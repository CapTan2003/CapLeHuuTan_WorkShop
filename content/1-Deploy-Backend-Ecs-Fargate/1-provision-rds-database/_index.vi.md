---
title: "Tạo Cơ Sở Dữ Liệu RDS (MySQL)"
date: "2025-07-17"
weight: 1 
chapter: false
pre: " <b> 1.1 </b> "
---

- **Tạo CSDL RDS bằng AWS Console**

    - Truy cập [bảng điều khiển Amazon RDS](https://console.aws.amazon.com/rds/home).
    - Chọn **Databases** → nhấn **Create database**.
    - Ở phần **Database creation method**, chọn **Standard Create**.

    ![image.png](/images/deploy_backend_rds/create_db_step1.png)

- **Chọn engine và phiên bản**

    - Engine type: **MySQL**  
    - Version: chọn phiên bản ổn định, ví dụ: **MySQL 8.0.x**

    ![image.png](/images/deploy_backend_rds/select_engine.png)

- **Thiết lập thông tin đăng nhập**

    - DB instance identifier: `study-english`
    - Master username: `admin`
    - Master password: đặt mật khẩu bảo mật và ghi nhớ

    ![image.png](/images/deploy_backend_rds/set_credentials.png)

- **Cấu hình phần cứng và dung lượng**

    - DB instance class: chọn loại tiết kiệm như `db.t3.micro` (Free Tier)
    - Storage: giữ mặc định 20 GiB (có thể bật auto-scaling nếu cần)

    ![image.png](/images/deploy_backend_rds/instance_storage.png)

- **Cấu hình kết nối mạng**

    - Virtual Private Cloud (VPC): chọn VPC mà ECS sẽ sử dụng
    - Subnet group: giữ mặc định hoặc chọn nhóm phù hợp
    - Public access: **Yes** (nếu cần test từ máy local)  
      👉 Sau khi triển khai xong nên đổi thành **No** để bảo mật
    - Security Group: mở cổng **TCP 3306**

    ![image.png](/images/deploy_backend_rds/network_settings.png)

- **Cấu hình bổ sung**

    - Initial database name: `study-english`
    - Backup và Monitoring: có thể tắt nếu chỉ dùng để phát triển/test
    - Nhấn **Create database** để tạo

    ![image.png](/images/deploy_backend_rds/final_create_db.png)

- **Chờ RDS được tạo xong**

    - Trạng thái sẽ là `Creating...` trong vài phút.
    - Khi chuyển sang `Available`, nhấn vào tên DB để xem chi tiết.

    ![image.png](/images/deploy_backend_rds/db_available.png)

- **Sao chép Endpoint để cấu hình**

    - Trong tab **Connectivity & security**, tìm trường **Endpoint**
    - Ví dụ: `study-english.c9d2gkxxxxx.ap-northeast-1.rds.amazonaws.com`

    ![image.png](/images/deploy_backend_rds/rds_endpoint.png)

- **(Tuỳ chọn) Kiểm tra kết nối từ máy local**

    ```bash
    mysql -h study-english.<region>.rds.amazonaws.com -u admin -p
    ```

    - Đảm bảo:
        - RDS cho phép public access (nếu test)
        - Cổng 3306 đã được mở trong Security Group
