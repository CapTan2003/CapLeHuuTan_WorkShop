---
title: "Tạo CloudFront Distribution & Cấu hình Origins"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

## Tạo CloudFront Distribution & Cấu hình Origins

---

### **1) Mở CloudFront**
- Vào **Amazon CloudFront** trong AWS Console.
- Nhấn **Create a CloudFront distribution**.

![image.png](/images/03/3/1.png)

---

### **2) Khởi tạo phân phối**
- Nhập **Distribution name**: `H2T`.
- Chọn **Single website or app**.
- (Không cấu hình custom domain ở bước này.)
- Nhấn **Next**.

![image.png](/images/03/3/2.png)

---

### **3) Chọn S3 làm Frontend Origin**
- **Origin type**: chọn **Amazon S3**.
- **S3 origin**: chọn bucket FE của bạn.
- **Origin path**: để trống.

![image.png](/images/03/3/3.png)

---

### **4) Cho phép CloudFront truy cập S3 & dùng cấu hình mặc định**
- Tick **Allow private S3 bucket access to CloudFront**.
- **Origin settings**: chọn **Use recommended origin settings**.
- Nhấn **Next**.

![image.png](/images/03/3/4.png)

---

### **5) Bỏ WAF**
- Chọn **Do not enable security protections**.
- Nhấn **Next**.

![image.png](/images/03/3/5.png)

---

### **6) Review & tạo phân phối**
- Kiểm tra phần **Origin** và **Cache settings**.
- Nhấn **Create distribution**.

![image.png](/images/03/3/6.png)

---

### **7) Mở tab Origins của phân phối vừa tạo**
- Vào **Distributions → Origins**.
- Nhấn **Create origin**.

![image.png](/images/03/3/7.png)

---

### **8) Thêm Backend Origin (ALB) – dùng HTTP**
- **Origin domain**: dán **ALB DNS**.
- **Protocol**: chọn **HTTP only**.
- **HTTP port**: `80`.
- **Origin path**: để trống.
- **Name**: đặt tên (ví dụ: `backend-alb`).

![image.png](/images/03/3/8.png)

---

### **9) Giữ HTTP – Không cấu hình TLS**
- Không chọn HTTPS, giữ nguyên HTTP.
- **Origin path**: để trống.
- **Enable Origin Shield**: để **No**.

![image.png](/images/03/3/9.png)

---

### **10) Hoàn tất phần Origins**
- Xác nhận danh sách có **2 origins**:
  - **S3** (frontend).
  - **ALB HTTP** (backend).
- Tiếp theo sẽ cấu hình **Behaviors**:
  - `/api/*` → **ALB (backend)**.
  - Mặc định → **S3 (frontend)**.

![image.png](/images/03/3/10.png)
