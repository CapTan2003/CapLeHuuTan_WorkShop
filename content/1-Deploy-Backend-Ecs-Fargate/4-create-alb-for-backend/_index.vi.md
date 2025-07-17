---
title: "Tạo Application Load Balancer để định tuyến"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 1.4 </b> "
---

- **Truy cập EC2 Console để tạo ALB**

    - Truy cập [EC2 Console](https://console.aws.amazon.com/ec2)
    - Ở menu bên trái, trong mục **Load Balancing**, chọn **Load Balancers**
    - Nhấn **Create Load Balancer**
    - Chọn loại **Application Load Balancer**, sau đó nhấn **Create**

    ![image.png](/images/deploy_backend_alb/alb_step1.png)

- **Cấu hình thông tin cho Load Balancer**

    - Tên: `backend-alb`
    - Scheme: chọn **Internet-facing** (nếu public) hoặc Internal (nếu private)
    - IP address type: **IPv4**
    - Listener: thêm HTTP (port 80), hoặc HTTPS (port 443) nếu bạn có SSL
    - Chọn **VPC** và **Subnets** (tối thiểu 2 subnet khác AZ)

    ![image.png](/images/deploy_backend_alb/alb_step2.png)

- **Cấu hình Security Group cho ALB**

    - Chọn hoặc tạo mới Security Group cho phép truy cập vào port `80` và/hoặc `443`
    - Ví dụ: cho phép `0.0.0.0/0` vào port 80 để test

    ![image.png](/images/deploy_backend_alb/alb_step3.png)

- **Thiết lập Target Group**

    - Chọn **New target group**
    - Target type: chọn `IP` (phù hợp với Fargate)
    - Tên: `backend-target-group`
    - Protocol: HTTP, Port: `8080`
    - Health check path: `/actuator/health` hoặc `/` nếu không có endpoint kiểm tra

    ![image.png](/images/deploy_backend_alb/target_group.png)

- **Bỏ qua phần đăng ký Target**

    - Bạn không cần đăng ký task ECS ở đây, vì ECS sẽ tự động gán khi tạo Service
    - Nhấn **Next**, kiểm tra lại cấu hình và nhấn **Create Load Balancer**

    ![image.png](/images/deploy_backend_alb/confirm_alb.png)

- **Hoàn tất**

    - ALB đã sẵn sàng để định tuyến traffic đến backend của ECS
    - Bạn có thể kiểm tra bằng cách truy cập vào DNS name của ALB  
      (ví dụ: `backend-alb-123456.elb.amazonaws.com`)
