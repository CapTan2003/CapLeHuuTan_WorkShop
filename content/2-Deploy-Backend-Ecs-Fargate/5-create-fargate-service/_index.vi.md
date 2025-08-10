---
title: "Create ECS Fargate Service (with ALB, Target Group, Auto Scaling)"
date: "2025-08-10"
weight: 5
chapter: false
pre: " <b> 2.5 </b> "
---

- **Access Service Creation**
    - Vào ECS cluster `h2t-backend-cluster` trong AWS Management Console.
    - Chọn tab **Services**, thấy "Services (0)" → chưa có service nào.
    - Click **Create** để tạo service mới.
    - Service giúp duy trì số lượng task mong muốn.
    ![image.png](/images/02/5/1.png)

- **Configure Service Details**
    - **Task definition family**: Chọn `h2t-backend-task`.
    - **Task definition revision**: Chọn **Latest** hoặc revision cụ thể.
    - **Service name**: `h2t-backend-task-service`.
    - Service name phải unique trong cluster.
    ![image.png](/images/02/5/2.png)

- **Configure Compute Configuration (Advanced)**
    - Mở **Compute configuration (advanced)**.
    - **Compute options**: Chọn **Capacity provider strategy**.
    - **Capacity provider**: `FARGATE`.
    - **Base**: `0`, **Weight**: `1`.
    - **Platform version**: `LATEST`.
    ![image.png](/images/02/5/3.png)

- **Configure Deployment Settings**
    - **Scheduling strategy**: `Replica`.
    - **Desired tasks**: `1`.
    - Bật **Availability Zone rebalancing**.
    - **Health check grace period**: `0` giây.
    - Bật **Amazon ECS deployment circuit breaker** + **Rollback on failures**.
    ![image.png](/images/02/5/4.png)

- **Configure Networking**
    - **VPC**: `vpc-024c455ec8b36b307`.
    - **Subnets**:
        - `subnet-04c44f964ca628aab` (ap-southeast-2b)
        - `subnet-07a217da887113ba` (ap-southeast-2a)
        - `subnet-03b1929fb918c9e69` (ap-southeast-2c)
    - **Security group**: `sg-03aedb5f21ba82193` (h2t-backend-security).
    - **Public IP**: Turned on.
    ![image.png](/images/02/5/5.png)

- **Configure Load Balancing**
    - Bật **Use load balancing**.
    - **Load balancer type**: Application Load Balancer.
    - **Container**: `h2t-backend 8080:8080`.
    - **Load balancer name**: `h2t-backend-lb`.
    - **Listener**: Port `80` (HTTP).
    ![image.png](/images/02/5/6.png)

- **Configure Target Group**
    - **Target group name**: `h2t-backend-target-group`.
    - **Protocol**: HTTP, **Port**: 8080.
    - **Deregistration delay**: 300 giây.
    - **Health check path**: `/`.
    ![image.png](/images/02/5/7.png)

- **Configure Service Auto Scaling**
    - Bật **Service auto scaling**.
    - **Min tasks**: 1, **Max tasks**: 3.
    - **Scaling policy type**: Target tracking.
    - **Policy name**: `cpu-tracking`.
    - **Metric**: ECSServiceAverageCPUUtilization.
    - **Target value**: 70%.
    - **Cooldown**: 300 giây cho scale-in và scale-out.
    ![image.png](/images/02/5/8.png)

- **Review and Create Service**
    - Xem lại toàn bộ cấu hình.
    - Click **Create** để triển khai service.
    ![image.png](/images/02/5/9.png)

- **Verify Service Creation**
    - Sau khi tạo thành công → quay lại cluster overview.
    - Services: 1 Active service, Tasks: 1 Running.
    - Service name: `h2t-backend-task-service`, Status: Active.
    ![image.png](/images/02/5/10.png)

