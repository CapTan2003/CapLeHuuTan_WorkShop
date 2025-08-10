---
title: "Build & Upload Frontend App to S3"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 3.2 </b> "
---

- **Cấu hình API endpoint sử dụng `/api`**

    - Trong file cấu hình API client (ví dụ: `src/services/apiClient.ts`), đặt `BASE_URL` thành `/api`:

    ```ts
    const BASE_URL = "/api";
    ```

    - **Lý do**:  
      Khi triển khai với **CloudFront Behaviors**, frontend và backend sẽ dùng chung một domain CDN.  
      CloudFront sẽ định tuyến như sau:
        - Các request bắt đầu bằng `/api` → chuyển tiếp đến backend (ECS/ALB).
        - Các request khác → trả về file tĩnh từ S3.  

      Cách này giúp frontend gọi backend mà không cần domain riêng, đồng thời tránh lỗi CORS.

    ![image.png](/images/02/1/1.png)

- **Build ứng dụng frontend**

    - Mở terminal và chạy:
    ```bash
    npm run build
    ```
    ![image.png](/images/02/1/2.png)

- **Hoàn tất build**

    - Sau khi build, thư mục `build` sẽ chứa toàn bộ file tĩnh sẵn sàng cho môi trường production.
    ![image.png](/images/02/1/3.png)

- **Upload build lên S3**

    - Sử dụng AWS CLI để đồng bộ thư mục `build` với bucket S3:
    ```bash
    aws s3 sync ./build s3://your-bucket-name --delete
    ```
    - Tham số `--delete` giúp xóa các file cũ trong bucket không còn trong bản build mới.
    ![image.png](/images/02/1/4.png)

- **Upload hoàn tất**

    - Tất cả file tĩnh của ứng dụng đã được lưu trữ trên S3 bucket.
    ![image.png](/images/02/1/5.png)
