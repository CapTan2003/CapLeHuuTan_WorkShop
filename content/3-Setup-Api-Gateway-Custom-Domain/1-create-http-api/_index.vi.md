---
title: "Tạo HTTP API trong API Gateway"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 3.1 </b> "
---

- **Mở API Gateway Console**

    - Truy cập [Amazon API Gateway](https://console.aws.amazon.com/apigateway/)
    - Nhấn **Create API** → chọn **HTTP API**
    - Nhấn **Build**

    ![image.png](/images/api_gateway/create_http_api.png)

- **Cấu hình thông tin cơ bản**

    - Tên API: `web-app-api`
    - Mô tả: Không bắt buộc
    - Chọn endpoint type: **Regional**

    ![image.png](/images/api_gateway/configure_http_api.png)

- **Cấu hình route**

    - Nhấn **Add integration**
    - Chọn loại tích hợp: **ALB**
    - Chọn ALB và listener đã tạo trước đó
    - Đường dẫn: `/api/*` → method: `ANY`

    ![image.png](/images/api_gateway/add_route.png)

- **Triển khai API**

    - Stage name: `prod`
    - Nhấn **Create**

    ![image.png](/images/api_gateway/deploy_api.png)

- **Kiểm tra HTTP API**

    - Sao chép đường dẫn **invoke URL**
    - Kiểm tra bằng `curl` hoặc frontend

    ```bash
    curl https://<your-api-id>.execute-api.<region>.amazonaws.com/prod/api/health
    ```
