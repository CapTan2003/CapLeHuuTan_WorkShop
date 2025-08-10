---
title: "Create ECS Fargate Service (with ALB, Target Group, Auto Scaling)"
date: "2025-08-10"
weight: 5
chapter: false
pre: " <b> 2.5 </b> "
---

- **Open ECS Cluster**

    - Go to the [Amazon ECS dashboard](https://console.aws.amazon.com/ecs).
    - Select the cluster **`h2t-backend-cluster`**.
    - In the **Services** tab, click **Create** to add a new service.

    ![image.png](/images/02/5/1.png)

- **Configure Service Details**

    - **Task definition family**: `h2t-backend-task`.
    - **Revision**: `LATEST` (or specific revision if required).
    - **Service name**: `h2t-backend-task-service` (1–255 chars, a–z, A–Z, 0–9, hyphen, underscore).
    - The service manages running tasks from the selected task definition.

    ![image.png](/images/02/5/2.png)

- **Compute Configuration (Advanced)**

    - Expand **Compute configuration (advanced)**.
    - **Capacity provider strategy**: **FARGATE**, Base: `0`, Weight: `1`.
    - **Platform version**: `LATEST`.

    ![image.png](/images/02/5/3.png)

- **Deployment Settings**

    - **Scheduling strategy**: `Replica`.
    - **Desired tasks**: `1`.
    - Enable **Availability Zone rebalancing**.
    - **Health check grace period**: `0`.
    - Enable **Deployment circuit breaker** + **Rollback on failures**.

    ![image.png](/images/02/5/4.png)

- **Networking**

    - **VPC**: `vpc-024c455ec8b36b307`.
    - **Subnets**:
        - `subnet-04c44f964ca628aab` (ap-southeast-2b)
        - `subnet-07a217da887113ba` (ap-southeast-2a)
        - `subnet-03b1929fb918c9e69` (ap-southeast-2c)
    - **Security group**: `sg-03aedb5f21ba82193` (h2t-backend-security).
    - **Public IP**: `ON` (if internet access required).

    ![image.png](/images/02/5/5.png)

- **Load Balancing**

    - Enable **Use load balancing** → **Application Load Balancer**.
    - **Container**: `h2t-backend 8080:8080`.
    - **Load balancer name**: `h2t-backend-lb`.
    - **Listener**: Port `80`, Protocol `HTTP`.

    ![image.png](/images/02/5/6.png)

- **Target Group**

    - Create new target group:
        - **Name**: `h2t-backend-target-group`
        - **Protocol**: `HTTP`, **Port**: `8080`
        - **Deregistration delay**: `300` seconds
        - **Health check path**: `/`

    ![image.png](/images/02/5/7.png)

- **Service Auto Scaling**

    - Enable **Service auto scaling**.
    - **Min tasks**: `1`, **Max tasks**: `3`.
    - **Policy type**: Target tracking (`cpu-tracking`).
    - **Metric**: `ECSServiceAverageCPUUtilization`, Target: `70%`.
    - **Cooldown**: `300s` scale-out / `300s` scale-in.

    ![image.png](/images/02/5/8.png)

- **Review & Create**

    - Confirm all settings.
    - Click **Create** to deploy the service.

    ![image.png](/images/02/5/9.png)

- **Verify Service**

    - In cluster overview:
        - **Services**: 1 Active
        - **Tasks**: 1 Running
    - Status: `Active`, Strategy: `Replica`, Auto scaling enabled.

    ![image.png](/images/02/5/10.png)

