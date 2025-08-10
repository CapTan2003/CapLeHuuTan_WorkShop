---
title: "Tạo ECS Cluster cho Backend Container"
date: "2025-08-10"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

## 1. Mở dịch vụ Amazon ECS

- Truy cập [bảng điều khiển Amazon ECS](https://console.aws.amazon.com/ecs).
- Trong menu bên trái, chọn **Clusters**.
- Nhấn **Create cluster** để bắt đầu tạo một cluster mới.

![image.png](/images/02/4/1.png)

---

## 2. Cấu hình thông tin cơ bản của cluster

- **Tên cluster**: `h2t-backend-cluster`.
- Tên phải dài từ 1–255 ký tự; ký tự hợp lệ gồm: a–z, A–Z, 0–9, dấu gạch ngang (-), dấu gạch dưới (_).
- (Tùy chọn) Mở rộng **Service Connect defaults** để cấu hình giao tiếp giữa các service.

![image.png](/images/02/4/2.png)

---

## 3. Chọn cấu hình hạ tầng

- **Hạ tầng**: Mặc định là **AWS Fargate (serverless)** với hai capacity provider **Fargate** và **Fargate Spot**.
- **AWS Fargate**: Mô hình trả phí theo mức sử dụng, không cần quản lý hạ tầng.
- **Amazon EC2 instances**: Tùy chọn, dành cho workload chạy liên tục.
- **External instances (ECS Anywhere)**: Tùy chọn, có thể đăng ký sau.

![image.png](/images/02/4/3.png)

---

## 4. Cấu hình giám sát và các tùy chọn khác

- **Giám sát (Monitoring)**:
    - **Container Insights (enhanced)**: Khuyến nghị, cung cấp số liệu hiệu suất chi tiết.
    - **Container Insights**: Cung cấp số liệu tổng hợp cơ bản.
    - **Turned off**: Chỉ dùng số liệu mặc định từ CloudWatch.
- **Mã hóa (Encryption)**: Tùy chọn, chọn KMS key để mã hóa dữ liệu.
- **Thẻ (Tags)**: Thêm thẻ để tổ chức tài nguyên.
- Nhấn **Create** để hoàn tất.

![image.png](/images/02/4/4.png)

---

## 5. Xác minh tạo cluster thành công

- Thông báo thành công: *Cluster h2t-backend-cluster has been created successfully*.
- Nhấn **View cluster** để xem chi tiết:
    - **Services**: 0
    - **Tasks**: 0
    - **Container instances**: 0 (sử dụng Fargate)
    - **Giám sát**: Đã bật Container Insights

![image.png](/images/02/4/5.png)

---

## 6. Tóm tắt

- ECS cluster đã được tạo với cấu hình Fargate serverless.
- Đã bật Container Insights để giám sát.
- Sẵn sàng triển khai ECS services và chạy task bằng các task definition đã tạo.
