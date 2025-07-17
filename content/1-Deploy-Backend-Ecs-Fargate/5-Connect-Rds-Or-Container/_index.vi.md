title: "Kết nối với Amazon RDS hoặc container MySQL"
date: "2025-07-17"
weight: 5
chapter: false
pre: " <b> 1.5 </b> "
---

- **Tùy chọn 1: Kết nối với Amazon RDS (MySQL được quản lý)**
    - Mở [Amazon RDS Console](https://console.aws.amazon.com/rds/)
    - Chọn **Create database** → chọn **Standard Create**
    - Engine: **MySQL** (phiên bản mới nhất)
    - Cấu hình cơ bản:
      - DB instance identifier: `my-rds-instance`
      - Tên đăng nhập & mật khẩu
      - Bật **Public access**
      - Cổng kết nối: `3306`
    - Trong phần **Connectivity**:
      - Chọn đúng VPC và subnet group
      - Thêm hoặc tạo mới **Security Group** cho phép truy cập cổng 3306

    ![image.png](/images/deploy_backend_fargate/rds_create.png)

- **Tùy chọn 2: Sử dụng container MySQL trong ECS Cluster**
    - Tạo mới một Task Definition:
      - Image: `mysql:8`
      - Environment variables:
        - `MYSQL_ROOT_PASSWORD`
        - `MYSQL_DATABASE`
        - `MYSQL_USER`
        - `MYSQL_PASSWORD`
    - Chạy task trong cùng VPC & subnet với backend
    - Kết nối thông qua tên dịch vụ nội bộ (DNS) hoặc IP nội bộ

- **Cập nhật Task Definition của Backend**
    - Thêm biến môi trường:
      - `SPRING_DATASOURCE_URL`
      - `SPRING_DATASOURCE_USERNAME`
      - `SPRING_DATASOURCE_PASSWORD`
    - Nếu dùng RDS: lấy endpoint từ RDS console  
    - Nếu dùng MySQL container: dùng tên service nội bộ hoặc IP
