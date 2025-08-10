---
title: "Tạo Behavior cho backend"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

- **Mở tab Behaviors**
    - Vào phân phối CloudFront vừa tạo.
    - Chọn tab **Behaviors**.
    - Mặc định đã có **Default behavior** trỏ về S3.
    - Nhấn **Create behavior** để thêm rule mới.

    ![image.png](/images/04/1/1.png)

- **Nhập thông tin Behavior**
    - **Path pattern**: `/api/*` (để định tuyến các request API).
    - **Origin or origin groups**: chọn **origin backend (ALB)**.
    - **Compress objects automatically**: chọn **Yes**.
    - **Viewer protocol policy**: **Redirect HTTP to HTTPS**.
    - **Allowed HTTP methods**: **GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE**.

    ![image.png](/images/04/1/2.png)

- **Cấu hình policy**
    - **Origin request policy**: chọn `AllViewer` (để forward toàn bộ request headers/params/body).
    - Không cấu hình **Response headers policy** ở bước này.
    - Để trống phần **Function associations**.

    ![image.png](/images/04/1/3.png)

- **Tạo Behavior**
    - Nhấn **Create behavior** để lưu.
    - Behavior `/api/*` đã được thêm, sẽ ưu tiên match trước Default behavior.
