---
title: "Tạo ECS Fargate Service và cấu hình Auto Scaling"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 1.3 </b> "
---

- **Mở ECS Cluster và chọn cluster cần triển khai**

    - Truy cập [Amazon ECS Console](https://console.aws.amazon.com/ecs)
    - Ở thanh bên trái, chọn **Clusters**
    - Chọn cluster bạn đã tạo trước đó (ví dụ: `production-cluster`)

    ![image.png](/images/deploy_backend_fargate/open_cluster.png)

- **Tạo Service mới từ Task Definition**

    - Trong cluster, chuyển sang tab **Services**
    - Nhấn **Create** → chọn loại khởi chạy là **FARGATE**
    - Chọn Task Definition (ví dụ: `springboot-backend-task`)
    - Phiên bản platform: chọn `LATEST`
    - Đặt tên Service (ví dụ: `backend-service`)

    ![image.png](/images/deploy_backend_fargate/create_service_step1.png)

- **Thiết lập số lượng task và bật Auto Scaling**

    - Số lượng task mong muốn (Desired tasks): `1` hoặc nhiều hơn tùy tải
    - Bật tính năng **Service Auto Scaling**
    - Cấu hình min = 1, max = 3 task
    - Chính sách scale: sử dụng target CPU là `50%`

    ![image.png](/images/deploy_backend_fargate/auto_scaling.png)

- **Chọn VPC và subnet để triển khai**

    - Chọn đúng **VPC** và **Subnets** đã tạo sẵn
    - Bật **Enable public IP** nếu muốn truy cập công khai hoặc test

    ![image.png](/images/deploy_backend_fargate/networking.png)

- **Gắn với Load Balancer (ALB) đã có**

    - Chọn **Application Load Balancer**
    - Chọn ALB hiện tại (ví dụ: `backend-alb`)
    - Chọn listener port `80` hoặc `443`
    - Thêm target group mới hoặc chọn group sẵn có
    - Thiết lập pattern: `/api/*` (tuỳ định tuyến)

    ![image.png](/images/deploy_backend_fargate/attach_alb.png)

- **Xem lại và tạo Service**

    - Nhấn **Next** và sau đó **Create Service**
    - Chờ vài phút để ECS khởi tạo task và chuyển sang trạng thái **RUNNING**

    ![image.png](/images/deploy_backend_fargate/confirm_running.png)
