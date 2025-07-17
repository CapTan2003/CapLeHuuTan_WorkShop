---
title: "Trang chủ"
date: "2025-07-17"
weight: 1
chapter: false
---

# Triển khai ứng dụng web tách biệt trên AWS  
## Frontend + Backend với các thực hành tốt nhất

#### Tổng quan

Workshop này hướng dẫn bạn triển khai một ứng dụng web hiện đại theo kiến trúc tách biệt (decoupled) trên AWS, tuân theo các thực hành tốt nhất trong kiến trúc điện toán đám mây.  
Hệ thống gồm frontend (**React SPA lưu trữ trên S3 và phân phối qua CloudFront**) và backend container hóa (**Spring Boot chạy trên ECS Fargate sau ALB**).  
**Amazon API Gateway** điều phối luồng yêu cầu, backend kết nối đến cơ sở dữ liệu **MySQL được quản lý bởi Amazon RDS**.  
Chúng ta cũng tích hợp CI/CD pipelines và giám sát với CloudWatch.

#### Công nghệ sử dụng

Dự án bao gồm cả phần frontend và backend:

- **Frontend**: React SPA  
  - Lưu trữ trên **Amazon S3**  
  - Phân phối qua **Amazon CloudFront**

- **Backend**: Java Spring Boot API  
  - Container hóa bằng **Docker**  
  - Chạy trên **ECS Fargate** phía sau **Application Load Balancer**

- **Cơ sở dữ liệu**: Amazon RDS (MySQL)

- **Công cụ hạ tầng**:  
  - AWS CLI, IAM, VPC, Route53, Certificate Manager  
  - GitHub Actions để triển khai tự động  
  - CloudWatch để ghi log và thiết lập cảnh báo

---

#### Các module

1. **Triển khai Backend với ECS Fargate**
   - Tạo repo ECR và push image backend
   - Khai báo ECS Task Definition và Fargate Service
   - Thiết lập Application Load Balancer
   - Kết nối đến RDS hoặc dùng container MySQL

2. **Triển khai Frontend với S3 và CloudFront**
   - Build ứng dụng React
   - Upload vào S3 bucket
   - Tạo phân phối CloudFront
   - Cấu hình cache và chính sách CORS

3. **Cấu hình API Gateway và domain tùy chỉnh**
   - Tạo HTTP API với Amazon API Gateway
   - Điều hướng traffic đến ALB backend
   - Cài đặt SSL với ACM và ánh xạ tên miền với Route53

4. **CI/CD và giám sát**
   - Cấu hình GitHub Actions cho frontend và backend
   - Tự động build và triển khai
   - Bật logging và cảnh báo với CloudWatch

---

#### Nội dung chính

1. [1. Triển khai Backend với ECS Fargate](1-deploy-backend-ecs-fargate/)
2. [2. Triển khai Frontend với S3 và CloudFront](2-deploy-frontend-s3-cloudfront/)
3. [3. Cấu hình API Gateway và domain tùy chỉnh](3-setup-api-gateway-custom-domain/)
4. [4. CI/CD và giám sát](4-ci-cd-and-monitoring/)
