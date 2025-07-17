---
title: "Cấu hình bản ghi Route 53 cho tên miền tùy chỉnh"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 3.4 </b> "
---

- **Truy cập bảng điều khiển Route 53**

    - Mở [Route 53 Console](https://console.aws.amazon.com/route53/)
    - Nhấp vào **Hosted zones**
    - Chọn hosted zone cho tên miền của bạn (ví dụ: `example.com`)

- **Tạo bản ghi mới**

    - Nhấn **Create record**
    - Nhập tên bản ghi: `app` (nếu bạn muốn `app.example.com`)
    - Chọn **Record type**: `A – IPv4 address`
    - Chọn **Alias**: Yes
    - Chọn **Alias to: Application Load Balancer (ALB)** hoặc **CloudFront** tùy theo cách sử dụng
    - Chọn đúng vùng và ALB hoặc CloudFront tương ứng

- **Lưu bản ghi**

    - Nhấn **Create records**
    - Chờ quá trình cập nhật DNS hoàn tất (mất vài phút)

    ![route53_record.png](/images/api_gateway/route53_record.png)

- **Giờ bạn đã có thể truy cập ứng dụng bằng tên miền riêng rồi!**
