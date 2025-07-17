---
title: "Tải các file tĩnh lên S3"
date: "2025-07-17"
weight: 5
chapter: false
pre: " <b> 2.5 </b> "
---

- **Tải file lên bằng AWS Console**

  - Truy cập [S3 Console](https://s3.console.aws.amazon.com/s3/)
  - Mở bucket S3 bạn đã tạo để hosting frontend
  - Nhấn **Upload** → **Add files/folder**, chọn thư mục `build/` hoặc `dist/` (tuỳ framework)
  - Nếu cần, đặt thủ công `Content-Type` cho các file `.html`, `.js`, `.css`, `.json`
  - Nhấn **Upload**

  ![upload-ui](/images/deploy_frontend/upload_files_ui.png)

---

- **Tải file lên bằng AWS CLI**

  Nếu bạn đã cài AWS CLI và cấu hình credentials:

  ```bash
  aws s3 cp build/ s3://ten-bucket-cua-ban/ --recursive
