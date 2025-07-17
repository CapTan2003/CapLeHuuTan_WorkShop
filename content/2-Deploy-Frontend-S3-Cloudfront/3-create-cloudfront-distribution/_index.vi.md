---
title: "Tạo CloudFront Distribution"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

- **Truy cập [Amazon CloudFront Console](https://console.aws.amazon.com/cloudfront)**

- **Nhấn “Create Distribution” để bắt đầu**

  - Trong mục **Origin domain**, chọn endpoint của S3 dạng static website (kết thúc bằng `.s3-website-<region>.amazonaws.com`)
  - Để trống **Origin path**
  - Đặt tên cho **Origin name**, ví dụ: `frontend-s3-origin`
  - Chọn **Viewer protocol policy** là **Redirect HTTP to HTTPS**

  ![image.png](/images/deploy_frontend/create_cloudfront_step1.png)

- **Cấu hình cache behavior**

  - Allowed HTTP methods: `GET, HEAD`
  - Cache policy: chọn **CachingOptimized**
  - Bật tùy chọn **Compress objects automatically**
  - Tiếp tục đặt **Viewer protocol policy** là `Redirect HTTP to HTTPS`

  ![image.png](/images/deploy_frontend/cloudfront_cache_behavior.png)

- **Thiết lập trang mặc định (Default root object)**

  - Cuộn xuống phần **Default root object**
  - Nhập `index.html` để CloudFront tự load trang chủ mặc định

  ![image.png](/images/deploy_frontend/cloudfront_root_object.png)

- **Kiểm tra và khởi tạo**

  - Nhấn **Create distribution**
  - Đợi vài phút để trạng thái chuyển từ **In Progress** sang **Deployed**
  - Khi hoàn tất, sao chép **Distribution domain name** (ví dụ: `d123abc.cloudfront.net`) — sẽ dùng để truy cập thử hoặc cấu hình domain riêng

  ![image.png](/images/deploy_frontend/cloudfront_success.png)
