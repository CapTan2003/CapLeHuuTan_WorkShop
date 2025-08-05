---
title: "Triển khai Backend với ECS Fargate"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

Để triển khai backend bằng ECS Fargate, hãy làm theo từng bước hướng dẫn dưới đây:

- [Tạo CSDL trên Amazon RDS (MySQL/PostgreSQL)](1-provision-rds-database)
- [Tạo repository ECR và đẩy Docker image](2-create-ecr-push-image)
- [Khai báo ECS Task Definition cho ứng dụng Spring Boot](3-create-task-definition)
- [Tạo ECS Fargate Service và bật Auto Scaling](4-create-fargate-service)
- [Thiết lập Application Load Balancer để định tuyến](5-create-alb-for-backend)
- [Kết nối Backend đến RDS](6-connect-backend-to-rds)
- [Cấu hình VPC, Subnet và Security Group](7-configure-vpc-sg-for-ecs)
