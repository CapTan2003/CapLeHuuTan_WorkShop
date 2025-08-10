---
title: "Tạo ECS Task Definition cho Backend Container"
date: "2025-08-10"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

- **Mở dịch vụ Amazon ECS**

    - Truy cập [Amazon ECS Console](https://console.aws.amazon.com/ecs).
    - Ở trang chính, nhấn **Get started** để bắt đầu triển khai ứng dụng container.

    ![image.png](/images/02/3/1.png)

- **Mở trang Task Definitions**

    - Trong menu bên trái, chọn **Task definitions**.
    - Nhấn **Create new task definition** để tạo mới.

    ![image.png](/images/02/3/2.png)

- **Cấu hình Task Definition**

    - **Task definition family**: `h2t-backend-task`.
    - **Launch type**: Chọn **AWS Fargate**.
    - **Operating system/Architecture**: `Linux/X86_64`.
    - **Network mode**: `awsvpc`.

    ![image.png](/images/02/3/3.png)

- **Cấu hình tài nguyên và quyền**

    - **CPU**: `1 vCPU`.
    - **Memory**: `3 GB`.
    - **Task role**: Để trống.
    - **Task execution role**: Chọn **Create new role**.

    ![image.png](/images/02/3/4.png)

- **Cấu hình Container**

    - **Name**: `h2t-backend`.
    - **Image URI**:  
      ```
      740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend:latest
      ```
    - **Container port**: `8080`.
    - **Protocol**: `TCP`.
    - **App protocol**: `HTTP`.

    ![image.png](/images/02/3/5.png)

- **Cấu hình lưu trữ & giám sát (tùy chọn)**

    - **Volumes**: Thêm volume nếu cần.
    - **Monitoring**: Có thể bật AWS Distro for OpenTelemetry.
    - **Tags**: Thêm tag để quản lý.
    - Nhấn **Create** để hoàn tất.

    ![image.png](/images/02/3/6.png)

- **Xác nhận tạo thành công**

    - Thông báo màu xanh: *Task definition successfully created*.
    - Task `h2t-backend-task:1` đã được tạo.
    - **ARN**:  
      ```
      arn:aws:ecs:ap-southeast-2:740994884477:task-definition/h2t-backend-task:1
      ```
    - **Status**: `ACTIVE`.
    - **Launch type**: `Fargate`.
    - **Network mode**: `awsvpc`.

    ![image.png](/images/02/3/7.png)
