---
title: "Create ECS Fargate Service and enable Auto Scaling"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 1.4 </b> "
---

- **Open ECS Cluster and select your target cluster**
    - Go to the [Amazon ECS Console](https://console.aws.amazon.com/ecs)
    - In the sidebar, click **Clusters**
    - Choose the cluster you created (e.g., `production-cluster`)

    ![image.png](/images/deploy_backend_fargate/open_cluster.png)

- **Create a new Service from Task Definition**
    - Inside your cluster, go to the **Services** tab
    - Click **Create** → select **FARGATE** as launch type
    - Choose your Task Definition (e.g., `springboot-backend-task`)
    - Set platform version: `LATEST`
    - Enter a Service name (e.g., `backend-service`)

    ![image.png](/images/deploy_backend_fargate/create_service_step1.png)

- **Configure number of tasks and Auto Scaling**
    - Desired tasks: `1` or more depending on load
    - Enable **Service Auto Scaling**
    - Set min = 1, max = 3
    - Scaling policy: target CPU utilization `50%`

    ![image.png](/images/deploy_backend_fargate/auto_scaling.png)

- **Select VPC and subnets**
    - Choose the appropriate **VPC** and **Subnets** for deployment
    - Check **Enable public IP** (for testing/public access)

    ![image.png](/images/deploy_backend_fargate/networking.png)

- **Attach to existing Load Balancer (ALB)**
    - Select **Application Load Balancer**
    - Choose your existing ALB (e.g., `backend-alb`)
    - Select listener port `80` or `443`
    - Add new target group or select existing one
    - Path pattern: `/api/*`

    ![image.png](/images/deploy_backend_fargate/attach_alb.png)

- **Review and Create Service**
    - Click **Next** and **Create Service**
    - Wait for service to deploy and desired task to reach RUNNING status

    ![image.png](/images/deploy_backend_fargate/confirm_running.png)
