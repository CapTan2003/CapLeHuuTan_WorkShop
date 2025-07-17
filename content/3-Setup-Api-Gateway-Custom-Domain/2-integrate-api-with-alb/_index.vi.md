---
title: "Tích hợp API Gateway với Application Load Balancer (ALB)"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 3.2 </b> "
---

- **Truy cập HTTP API bạn đã tạo**

    - Mở [Amazon API Gateway Console](https://console.aws.amazon.com/apigateway/)
    - Chọn API (ví dụ: `web-app-api`)
    - Chuyển đến tab **Integrations**

- **Thêm tích hợp với ALB**

    - Nhấn **Manage integrations** → **Add integration**
    - Loại tích hợp: **Application Load Balancer (ALB)**
    - Chọn **ARN của ALB** và listener tương ứng
    - Nhấn **Add**

    ![image.png](/images/api_gateway/integrate_alb_step1.png)

- **Thêm route chuyển tiếp traffic**

    - Chuyển sang tab **Routes**
    - Nhấn **Create route**
    - Nhập đường dẫn: `/api/{proxy+}`
    - Phương thức: `ANY`
    - Chọn tích hợp ALB vừa tạo
    - Nhấn **Create**

    ![image.png](/images/api_gateway/integrate_alb_route.png)

- **Triển khai thay đổi**

    - Chuyển sang tab **Deployments**
    - Chọn stage (ví dụ: `prod`)
    - Nhấn **Deploy**

    ![image.png](/images/api_gateway/integrate_alb_deploy.png)

- **Kiểm tra định tuyến**

    ```bash
    curl https://<your-api-id>.execute-api.<region>.amazonaws.com/prod/api/health
    ```
