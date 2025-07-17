title: "Tạo CloudWatch Alarm để Giám sát"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 4.4 </b> "
---

Chúng tôi đã thiết lập các cảnh báo CloudWatch để giám sát tình trạng hệ thống, tập trung vào hiệu năng ECS và lỗi từ API Gateway.

---

- **Giám sát ECS Service (CPU & Bộ nhớ)**

    - Truy cập [CloudWatch Console](https://console.aws.amazon.com/cloudwatch/home).
    - Vào **Alarms → Create Alarm**.
    - Chọn **ECS Metrics**, sau đó chọn `CPUUtilization` và `MemoryUtilization` cho service backend.
    - Thiết lập các điều kiện sau:
        - Ngưỡng: `>= 70%`
        - Thời gian: `5 phút`
        - Số lần liên tiếp: `3`
    - Thêm hành động thông báo qua SNS.

    ![image.png](/images/ci_cd/alarm_ecs_cpu.png)

---

- **Giám sát lỗi API Gateway**

    - Chọn các metric `5XXError` và `Latency` trong mục **API Gateway Metrics**.
    - Đặt ngưỡng cảnh báo (ví dụ: hơn 10 lỗi trong 5 phút).
    - Thêm tên cảnh báo và kênh thông báo qua SNS.

    ![image.png](/images/ci_cd/alarm_apigw_errors.png)

---

Các cảnh báo đã được tạo và kiểm tra thành công. Hệ thống hiện sẽ gửi thông báo khi xảy ra lỗi hoặc vượt ngưỡng hiệu suất cho phép.
