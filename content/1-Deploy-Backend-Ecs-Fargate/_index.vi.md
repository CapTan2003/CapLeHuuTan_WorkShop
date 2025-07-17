---
title: "Triển khai Backend với ECS Fargate"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

Để triển khai backend bằng ECS Fargate, hãy làm theo từng bước hướng dẫn dưới đây:

- [Tạo repository ECR và đẩy Docker image](1-create-ecr-push-image)
- [Khai báo ECS Task Definition cho ứng dụng Spring Boot](2-create-task-definition)
- [Tạo ECS Fargate Service và bật Auto Scaling](3-create-fargate-service)
- [Thiết lập Application Load Balancer để định tuyến](4-create-alb-for-backend)
- [Kết nối đến RDS hoặc container MySQL](5-connect-rds-or-container)
- [Cấu hình VPC, Subnet và Security Group](6-configure-vpc-sg-for-ecs)
