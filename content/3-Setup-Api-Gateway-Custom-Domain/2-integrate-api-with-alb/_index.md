---
title: "Integrate API Gateway with Application Load Balancer (ALB)"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 3.2 </b> "
---

- **Go to your HTTP API in API Gateway**

    - Open [Amazon API Gateway Console](https://console.aws.amazon.com/apigateway/)
    - Choose the HTTP API you created (e.g. `web-app-api`)
    - Navigate to the **Integrations** tab

- **Add new integration for ALB**

    - Click **Manage integrations** → **Add integration**
    - Integration target: **Application Load Balancer (ALB)**
    - Choose your **ALB ARN** and listener
    - Click **Add**

    ![image.png](/images/api_gateway/integrate_alb_step1.png)

- **Add route to forward traffic**

    - Go to **Routes** tab
    - Click **Create route**
    - Enter path: `/api/{proxy+}`
    - Method: `ANY`
    - Select the ALB integration created
    - Click **Create**

    ![image.png](/images/api_gateway/integrate_alb_route.png)

- **Deploy changes**

    - Go to **Deployments**
    - Choose your stage (e.g. `prod`)
    - Click **Deploy**

    ![image.png](/images/api_gateway/integrate_alb_deploy.png)

- **Test routing**

    ```bash
    curl https://<your-api-id>.execute-api.<region>.amazonaws.com/prod/api/health
    ```
