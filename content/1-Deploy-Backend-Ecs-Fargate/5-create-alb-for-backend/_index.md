---
title: "Set up Application Load Balancer for routing"
date: "2025-07-17"
weight: 5
chapter: false
pre: " <b> 1.5 </b> "
---

- **Go to EC2 Console to create ALB**
    - Navigate to [EC2 Console](https://console.aws.amazon.com/ec2)
    - On the left menu, under **Load Balancing**, click **Load Balancers**
    - Click **Create Load Balancer**
    - Select **Application Load Balancer**, then click **Create**

    ![image.png](/images/deploy_backend_alb/alb_step1.png)

- **Configure Load Balancer settings**
    - Name: `backend-alb`
    - Scheme: **Internet-facing** (or internal if private)
    - IP address type: **IPv4**
    - Listeners: Add HTTP (port 80), or HTTPS (port 443) if using SSL
    - Select your **VPC** and **Subnets** (minimum 2 in different AZs)

    ![image.png](/images/deploy_backend_alb/alb_step2.png)

- **Configure security group for ALB**
    - Select or create a Security Group that allows inbound access on port `80` and/or `443`
    - Example: allow `0.0.0.0/0` for HTTP (testing only)

    ![image.png](/images/deploy_backend_alb/alb_step3.png)

- **Set up Target Group**
    - Choose **New target group**
    - Target type: `IP` (for Fargate)
    - Name: `backend-target-group`
    - Protocol: HTTP, Port: `8080`
    - Health check path: `/actuator/health` or `/` if none

    ![image.png](/images/deploy_backend_alb/target_group.png)

- **Register targets later**
    - You don’t need to register tasks here — ECS will handle it when you create the service
    - Click **Next**, review configuration, and **Create Load Balancer**

    ![image.png](/images/deploy_backend_alb/confirm_alb.png)

- **Done**
    - ALB is now ready to route traffic to your ECS backend service
    - You can test it by hitting the ALB DNS name (e.g., `backend-alb-123456.elb.amazonaws.com`)
