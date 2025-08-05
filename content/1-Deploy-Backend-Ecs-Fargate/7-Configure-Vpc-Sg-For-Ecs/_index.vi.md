---
title: "Cấu hình VPC, Subnet và Security Group cho ECS"
date: "2025-07-17"
weight: 7
chapter: false
pre: " <b> 1.7 </b> "
---

- **Tạo VPC và Subnet**
    - Truy cập [VPC Console](https://console.aws.amazon.com/vpc/)
    - Chọn **Your VPCs** → **Create VPC**
    - Chọn **VPC and more** để tự động tạo VPC, Subnet, Internet Gateway,...
    - Cấu hình:
        - Tên VPC: `workshop-vpc`
        - CIDR block: `10.0.0.0/16`
        - Tạo ít nhất 2 subnet ở các Availability Zones khác nhau
        - Bật **Auto-assign public IPv4**

    ![image.png](/images/configure_vpc/vpc_create.png)

- **Tạo Internet Gateway và gán vào VPC**
    - Trong menu trái, chọn **Internet Gateways**
    - Nhấn **Create Internet Gateway**, đặt tên
    - Nhấn **Attach to VPC** và chọn VPC vừa tạo (`workshop-vpc`)

    ![image.png](/images/configure_vpc/internet_gateway.png)

- **Tạo Route Table và liên kết với Subnet**
    - Vào **Route Tables** → **Create route table**
    - Chọn VPC: `workshop-vpc`
    - Sau khi tạo, chỉnh **Routes**:
        - Destination: `0.0.0.0/0`
        - Target: Internet Gateway
    - Sau đó liên kết với các Subnet đã tạo

    ![image.png](/images/configure_vpc/route_table.png)

- **Tạo Security Group cho ECS backend**
    - Vào **Security Groups** → **Create security group**
    - Tên: `ecs-backend-sg`
    - VPC: chọn `workshop-vpc`
    - Inbound rules:
        - Cho phép HTTP (port 80), HTTPS (443) nếu có
        - Cho phép port `8080` cho backend
        - Cho phép port `3306` nếu kết nối RDS hoặc MySQL container
    - Outbound: giữ mặc định (cho phép tất cả)

    ![image.png](/images/configure_vpc/security_group.png)

- **Kết nối VPC và Security Group với ECS**
    - Khi tạo ECS Service, chọn VPC `workshop-vpc`
    - Chọn các subnet thuộc AZ khác nhau
    - Gán Security Group `ecs-backend-sg`

- **Xác nhận**
    - Đảm bảo các thành phần được cấu hình và liên kết chính xác
    - ECS task có thể truy cập internet nếu dùng subnet công cộng hoặc NAT Gateway

    ![image.png](/images/configure_vpc/ecs_network_complete.png)
