title: "Bật CloudWatch Logs cho ECS và API Gateway"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 4.3 </b> "
---

- **Bật CloudWatch Logs cho ECS Task**

    - Trong quá trình tạo ECS Task Definition:
      - Mở phần **Log configuration**.
      - Chọn **awslogs** làm log driver.
      - Nhập:
        - **Log group**: `/ecs/springboot-backend`
        - **Region**: `ap-northeast-1`
        - **Stream prefix**: `ecs`
    - ECS sẽ tự động gửi log của container lên CloudWatch.

    ![image.png](/images/ci_cd/enable_logs_ecs.png)

---

- **Bật CloudWatch Logs cho API Gateway**

    - Truy cập **API Gateway Console**, chọn API bạn đã tạo.
    - Vào mục **Stages** → chọn stage đang sử dụng (ví dụ: `prod`).
    - Vào tab **Logs/Tracing**:
        - Bật **CloudWatch Logs**.
        - Chọn **Log level** là `INFO` hoặc `ERROR`.
        - Có thể bật thêm **Log full requests/responses data** để log chi tiết hơn.

    ![image.png](/images/ci_cd/enable_logs_apigw.png)

---

- **Xem log trong CloudWatch**

    - Truy cập [CloudWatch Console](https://console.aws.amazon.com/cloudwatch/home).
    - Vào **Log groups** → tìm theo tên log group đã tạo.
    - Click để xem log theo thời gian thực.
