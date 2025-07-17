---
title: "Configure VPC, Subnets, and Security Groups for ECS"
date: "2025-07-17"
weight: 6
chapter: false
pre: " <b> 1.6 </b> "
---

- **Create VPC and Subnets**
    - Go to the [VPC Console](https://console.aws.amazon.com/vpc/)
    - Select **Your VPCs** → **Create VPC**
    - Choose **VPC and more** to auto-create VPC, subnets, and other components
    - Configuration:
        - VPC Name: `workshop-vpc`
        - CIDR block: `10.0.0.0/16`
        - Create at least 2 subnets in different AZs
        - Enable **Auto-assign public IPv4**

    ![image.png](/images/configure_vpc/vpc_create.png)

- **Create Internet Gateway and Attach to VPC**
    - In left menu, go to **Internet Gateways**
    - Click **Create Internet Gateway** and name it
    - Click **Attach to VPC** and select `workshop-vpc`

    ![image.png](/images/configure_vpc/internet_gateway.png)

- **Create Route Table and Associate with Subnets**
    - Go to **Route Tables** → **Create route table**
    - Select VPC: `workshop-vpc`
    - After creation, edit routes:
        - Destination: `0.0.0.0/0`
        - Target: Internet Gateway
    - Then associate it with the subnets

    ![image.png](/images/configure_vpc/route_table.png)

- **Create Security Group for ECS Backend**
    - Go to **Security Groups** → **Create security group**
    - Name: `ecs-backend-sg`
    - VPC: `workshop-vpc`
    - Inbound Rules:
        - Allow HTTP (port 80), or HTTPS (443)
        - Allow port `8080` for backend
        - Allow port `3306` for MySQL if needed
    - Outbound: leave default (allow all)

    ![image.png](/images/configure_vpc/security_group.png)

- **Attach VPC and Security Group to ECS Service**
    - During ECS Service creation, select `workshop-vpc`
    - Choose the subnets in different AZs
    - Attach the security group `ecs-backend-sg`

- **Verify**
    - Ensure all components are properly configured and attached
    - ECS tasks should have internet access via public subnet or NAT

    ![image.png](/images/configure_vpc/ecs_network_complete.png)
