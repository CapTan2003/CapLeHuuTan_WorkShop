---
title: "Build ứng dụng frontend ở chế độ production"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

- **Chuyển vào thư mục frontend của dự án (nếu có)**

    ```bash
    cd frontend
    ```

- **Cài đặt các dependencies cần thiết**

    - Nếu bạn chưa cài, chạy:

    ```bash
    npm install
    ```

- **Build ứng dụng ở chế độ production**

    - Sử dụng lệnh sau để build frontend (React, Vue, v.v):

    ```bash
    npm run build
    ```

    - Thư mục đầu ra thường là `build/` (React) hoặc `dist/` (Vue, Vite)

    - Kết quả là một tập hợp các file HTML, JS, CSS đã được đóng gói sẵn sàng để upload lên S3

    ![image.png](/images/deploy_frontend/build_output.png)

- **Kiểm tra thư mục build**

    - Kiểm tra thư mục đầu ra sau khi build có chứa các file như `index.html`, `main.js`, `style.css`, v.v:

    ```bash
    ls build
    ```

    hoặc

    ```bash
    ls dist
    ```

    - Nếu có đầy đủ file, bạn đã sẵn sàng để chuyển sang bước tiếp theo: upload lên S3 và phân phối qua CloudFront
