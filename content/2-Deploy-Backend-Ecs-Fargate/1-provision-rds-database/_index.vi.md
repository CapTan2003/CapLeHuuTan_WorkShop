---
title: "Tạo Cơ Sở Dữ Liệu RDS (MySQL)"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

- **Mở dịch vụ Amazon RDS**

    - Truy cập [Amazon RDS dashboard](https://console.aws.amazon.com/rds/home).
    - Nhấn **Create database** để bắt đầu tạo cơ sở dữ liệu.

    ![image.png](/images/02/1/1.png)

- **Chọn phương thức tạo và loại cơ sở dữ liệu**

    - **Database creation method**: Chọn **Easy create** (tạo nhanh).
    - **Engine type**: Chọn **MySQL**.

    ![image.png](/images/02/1/2.png)

- **Đặt tên cơ sở dữ liệu và tài khoản quản trị**

    - **DB instance size**: Chọn **Free tier** (db.t4g.micro).
    - **DB instance identifier**: `study-english`.
    - **Master username**: `admin`.

    ![image.png](/images/02/1/3.png)

- **Cấu hình mật khẩu và kết nối**

    - **Credentials management**: Chọn **Self managed**.
    - Bật **Auto generate password** để AWS tự tạo mật khẩu.
    - **EC2 connection**: Chọn **Don't connect to an EC2 compute resource**.

    ![image.png](/images/02/1/4.png)

- **Xem lại cấu hình mặc định và tạo cơ sở dữ liệu**

    - Giữ nguyên các thiết lập mặc định của Easy create.
    - Nhấn **Create database**.

    ![image.png](/images/02/1/5.png)

- **Lưu thông tin đăng nhập**

    - Sao chép và lưu mật khẩu quản trị (đây là lần duy nhất có thể xem lại).

    ![image.png](/images/02/1/6.png)

- **Chờ cơ sở dữ liệu được khởi tạo**

    - Trạng thái sẽ hiển thị **Creating** trong vài phút.

    ![image.png](/images/02/1/7.png)

- **Lấy endpoint của RDS**

    - Chuyển sang tab **Connectivity & security**.
    - Sao chép **Endpoint** và ghi lại **Port** (3306).

    ![image.png](/images/02/1/8.png)

- **Kiểm tra Security Group**

    - Trong mục **VPC security groups**, nhấn vào liên kết của security group đang dùng.

    ![image.png](/images/02/1/9.png)

- **Xem quy tắc inbound**

    - Đảm bảo port 3306 đã được mở cho inbound traffic.

    ![image.png](/images/02/1/10.png)

- **Chỉnh sửa quy tắc inbound**

    - Thêm một quy tắc mới:
        - **Type**: Custom TCP
        - **Port range**: 3306
        - **Source**: 0.0.0.0/0 (dùng cho thử nghiệm; cần giới hạn IP khi triển khai thật)
    - Nhấn **Save rules**.

    ![image.png](/images/02/1/11.png)

- **Kết nối tới RDS bằng MySQL Workbench**

    - **Connection Name**: RDS study-english
    - **Hostname**: endpoint của RDS
    - **Port**: 3306
    - **Username**: admin
    - **Password**: mật khẩu đã lưu ở bước trước

    ![image.png](/images/02/1/12.png)

- **Xác nhận kết nối và quản lý cơ sở dữ liệu**

    - Sau khi kết nối thành công, bạn có thể tạo bảng, thêm dữ liệu và chạy truy vấn.

    ![image.png](/images/02/1/13.png)
