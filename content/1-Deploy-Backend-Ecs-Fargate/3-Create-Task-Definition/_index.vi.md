---
title: "Tạo Task Definition cho ứng dụng Backend"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 1.3 </b> "
---

- **Truy cập giao diện Amazon ECS**

    - Vào [ECS Console](https://console.aws.amazon.com/ecs).
    - Ở menu bên trái, chọn **Task Definitions** → nhấn **Create new Task Definition**.

    ![image.png](/images/deploy_backend_taskdef/open_ecs_task_definitions.png)

- **Chọn loại khởi chạy (launch type)**

    - Ở bước đầu tiên, chọn **FARGATE** làm launch type.
    - Nhấn **Next step** để tiếp tục.

    ![image.png](/images/deploy_backend_taskdef/select_fargate.png)

- **Thiết lập thông tin cho Task**

    - **Task Definition Name**: nhập tên định danh (ví dụ: `springboot-backend-task`)
    - **Task Role**: chọn `ecsTaskExecutionRole`  
      Nếu chưa có, nhấn “Create new role” và dùng mặc định.
    - **Operating system**: để mặc định là **Linux**
    - **CPU**: chọn `512 (.5 vCPU)` hoặc `1024 (1 vCPU)` tùy mức tải
    - **Memory**: chọn `1024 (1 GB)` trở lên
    - **Network mode**: để là **awsvpc**

    ![image.png](/images/deploy_backend_taskdef/task_settings.png)

- **Thêm container cho ứng dụng**

    - Kéo xuống phần **Container definitions**, nhấn **Add container**
    - Nhập các thông tin sau:
        - **Container name**: `springboot-container`
        - **Image URI**: nhập địa chỉ image từ ECR  
          (ví dụ: `<aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com/springboot-backend:latest`)
        - **Port mappings**: đặt **Container port** là `8080`

    ![image.png](/images/deploy_backend_taskdef/add_container.png)

- **Cấu hình logging**

    - Trong phần cấu hình container, bật mục **Log configuration**:
        - Log driver: chọn **awslogs**
        - **Log group**: `/ecs/springboot-backend` (hoặc tạo mới trong CloudWatch)
        - **Region**: `ap-northeast-1`
        - **Stream prefix**: `springboot`

    ![image.png](/images/deploy_backend_taskdef/logging_config.png)

- **Xác nhận và tạo mới**

    - Nhấn **Next step** để xem lại cấu hình
    - Cuối cùng nhấn **Create** để tạo Task Definition

    ![image.png](/images/deploy_backend_taskdef/review_create_task.png)

- **Hoàn tất**

    - Khi tạo thành công, Task Definition sẽ hiển thị trong danh sách của ECS
    - Task này sẽ được dùng để tạo Fargate Service ở bước kế tiếp

    ![image.png](/images/deploy_backend_taskdef/task_definition_created.png)
