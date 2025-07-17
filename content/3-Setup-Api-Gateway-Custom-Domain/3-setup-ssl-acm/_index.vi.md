---
title: "Cài đặt SSL bằng AWS Certificate Manager (ACM)"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 3.3 </b> "
---

- **Truy cập AWS Certificate Manager (ACM)**

    - Mở [ACM Console](https://console.aws.amazon.com/acm/)
    - Nhấn **Request a certificate**
    - Chọn **Request a public certificate**
    - Nhấn **Next**

- **Nhập tên miền**

    - Gõ tên miền của bạn (ví dụ: `app.example.com`)
    - Có thể thêm `www.app.example.com` nếu cần
    - Nhấn **Next**

- **Chọn phương thức xác minh**

    - Chọn **DNS validation** (khuyên dùng)
    - Nhấn **Next**, sau đó **Confirm and request**

- **Thêm bản ghi DNS vào Route 53**

    - Nếu dùng Route 53, nhấn **Create record in Route 53**
    - Đợi vài phút đến khi trạng thái chuyển thành **"Issued"**

    ![acm_issued.png](/images/api_gateway/acm_issued.png)

- **Lưu ý: Chứng chỉ ACM phải được tạo ở vùng `us-east-1` nếu dùng cho CloudFront.**
