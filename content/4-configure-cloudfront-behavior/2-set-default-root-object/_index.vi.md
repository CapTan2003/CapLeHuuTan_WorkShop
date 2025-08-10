---
title: "Cấu hình Default Root Object & Kiểm tra"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

- **Vào tab General**
    - Chọn **Edit**.
    - Trường **Default root object**: nhập `index.html`.
    - Giữ nguyên các thiết lập khác.
    - Nhấn **Save changes**.

    ![image.png](/images/04/2/1.png)
    ![image.png](/images/04/2/2.png)

- **Xác nhận cập nhật thành công**
    - Màn hình hiển thị thông báo màu xanh **Successfully updated distribution settings**.
    - **Default root object** đã được set thành `index.html`.

    ![image.png](/images/04/2/3.png)

- **Kiểm tra truy cập Frontend**
    - Mở **Distribution domain name** của CloudFront.
    - Giao diện web FE được hiển thị.

    ![image.png](/images/04/2/4.png)

- **Kiểm tra các trang khác**
    - Truy cập các trang FE khác (ví dụ: `/lesson/readings`) để đảm bảo SPA load đúng.

    ![image.png](/images/04/2/5.png)
