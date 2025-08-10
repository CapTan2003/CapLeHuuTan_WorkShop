---
title: "Trang chủ"
date: "2025-07-17"
weight: 1
chapter: false
---

# Triển khai ứng dụng web tách biệt trên AWS  
## Frontend + Backend sử dụng CDN Behavior

#### Tổng quan

Workshop này hướng dẫn triển khai một ứng dụng web hiện đại theo kiến trúc tách biệt (**Decoupled Architecture**) trên AWS.  
Hệ thống bao gồm **Frontend** (React SPA lưu trữ trên S3 và phân phối qua CloudFront) và **Backend** (Spring Boot container hóa chạy trên ECS Fargate sau Application Load Balancer, sử dụng MySQL trên Amazon RDS).  
Toàn bộ traffic được điều hướng qua **CloudFront Behavior** cho cả frontend và backend, không yêu cầu cài đặt chứng chỉ SSL riêng cho backend.

#### Công nghệ sử dụng

- **Frontend**  
  - React SPA  
  - Lưu trữ trên **Amazon S3**  
  - Phân phối qua **Amazon CloudFront**  

- **Backend**  
  - Java Spring Boot API  
  - Container hóa bằng **Docker**  
  - Chạy trên **ECS Fargate**  
  - Sau **Application Load Balancer**  
  - **Auto Scaling** dựa trên CPU/Memory  

- **Cơ sở dữ liệu**  
  - **Amazon RDS** (MySQL)

- **Công cụ hạ tầng**  
  - AWS CLI, IAM  
  - CloudWatch để giám sát và ghi log  

---

#### Các module

1. **Set up môi trường AWS CLI & IAM**
   - Tạo IAM user với quyền cần thiết
   - Cấu hình AWS CLI để đăng nhập vào tài khoản AWS

2. **Triển khai Backend với ECS Fargate**
   - Tạo Amazon RDS MySQL
   - Build Docker image backend và push lên ECR
   - Khai báo ECS Task Definition
   - Tạo ECS Cluster và Service (kèm ALB, Target Group, Auto Scaling)

3. **Triển khai Frontend với S3 và CloudFront**
   - Tạo & cấu hình S3 bucket để lưu trữ file build của dự án
   - Build dự án React (production) và upload build lên S3
   - Tạo CloudFront Distribution
   - Khởi tạo Origin cho:
     - Origin 1: Frontend (S3 Bucket)
     - Origin 2: Backend (Application Load Balancer)

4. **Cấu hình Behavior của CloudFront**
   - **Behavior cho từng origin**:
     - FE: `/`, `/static/*`, `/*.js`, `/*.css` → S3 origin
     - BE: `/api/*` → ALB origin
   - **Cấu hình CORS policy**:
     - Cho phép domain frontend truy cập API backend

---
### Kiến trúc hệ thống

![Kiến trúc hệ thống](/images/kientruc.png)

---

#### Nội dung chính

1. [1. Set up môi trường AWS CLI & IAM](1-setup-aws-cli-iam/)
2. [2. Triển khai Backend với ECS Fargate](2-deploy-backend-ecs-fargate/)
3. [3. Triển khai Frontend với S3 và CloudFront](3-deploy-frontend-s3-cloudfront/)
4. [4. Cấu hình Behavior của CloudFront](4-configure-cloudfront-behavior/)
