---
title: "Create HTTP API in API Gateway"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 3.1 </b> "
---

- **Open API Gateway Console**

    - Go to the [Amazon API Gateway](https://console.aws.amazon.com/apigateway/)
    - Click **Create API** → Choose **HTTP API**
    - Click **Build**

    ![image.png](/images/api_gateway/create_http_api.png)

- **Configure basic settings**

    - API name: `web-app-api`
    - Description: Optional
    - Select **Regional** endpoint type

    ![image.png](/images/api_gateway/configure_http_api.png)

- **Configure routes**

    - Click **Add integration**
    - Integration type: **ALB**
    - Choose your existing ALB + listener
    - Path: `/api/*` → method: `ANY`

    ![image.png](/images/api_gateway/add_route.png)

- **Deploy the API**

    - Stage name: `prod`
    - Click **Create**

    ![image.png](/images/api_gateway/deploy_api.png)

- **Test your HTTP API**

    - Copy the **invoke URL**
    - Test with `curl` or your frontend

    ```bash
    curl https://<your-api-id>.execute-api.<region>.amazonaws.com/prod/api/health
    ```
