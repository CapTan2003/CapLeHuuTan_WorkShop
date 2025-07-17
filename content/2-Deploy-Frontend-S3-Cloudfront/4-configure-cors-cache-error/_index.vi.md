---
title: "Cấu hình CORS, Cache-Control và xử lý lỗi"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

- **Cấu hình CORS cho S3 Bucket**

  - Truy cập **S3 Console** → chọn bucket bạn đã tạo để host frontend
  - Chọn tab **Permissions** → kéo xuống **Cross-origin resource sharing (CORS)**
  - Nhấn **Edit** và dán đoạn JSON sau:

    ```json
    [
      {
        "AllowedHeaders": ["*"],
        "AllowedMethods": ["GET", "HEAD"],
        "AllowedOrigins": ["*"],
        "ExposeHeaders": [],
        "MaxAgeSeconds": 3000
      }
    ]
    ```

    > Bạn có thể thay `"*"` trong `AllowedOrigins` bằng domain cụ thể để bảo mật hơn.

  ![image.png](/images/deploy_frontend/configure_cors.png)

---

- **Cấu hình Cache-Control cho file tĩnh**

  - Trên máy local, khi bạn build project (ví dụ `npm run build`), các file sẽ được tạo trong thư mục `build/` hoặc `dist/`
  - Trước khi upload lên S3, bạn có thể cấu hình header `Cache-Control` cho từng file bằng AWS CLI hoặc trong giao diện S3

  Ví dụ nếu dùng AWS CLI:

  ```bash
  aws s3 cp build/ s3://your-bucket-name/ --recursive \
    --cache-control "max-age=86400"
