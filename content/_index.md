---
title: "Home"
date: "2025-07-17"
weight: 1
chapter: false
---

# Deploying a Decoupled Web Application on AWS  
## Frontend + Backend Architecture with Best Practices

#### Overview

This workshop guides you through deploying a modern decoupled web application on AWS, following best practices in cloud architecture.  
The system includes a frontend (**React SPA hosted on S3 and delivered via CloudFront**) and a containerized backend (**Spring Boot running on ECS Fargate behind an ALB**).  
**Amazon API Gateway** handles request routing, and the backend connects to a managed **MySQL database on Amazon RDS**.  
We also integrate CI/CD pipelines and monitoring with CloudWatch.

#### Technology Used

This project includes both frontend and backend components:

- **Frontend**: React SPA  
  - Hosted on **Amazon S3**  
  - Delivered via **Amazon CloudFront**

- **Backend**: Java Spring Boot API  
  - Containerized with **Docker**  
  - Deployed on **ECS Fargate** behind an **Application Load Balancer**

- **Database**: Amazon RDS (MySQL)

- **Infrastructure Tools**:  
  - AWS CLI, IAM, VPC, Route53, Certificate Manager  
  - GitHub Actions for automated deployment  
  - CloudWatch for logging and alerting

---

#### Modules

1. **Deploy Backend with ECS Fargate**
   - Create ECR repo and push backend image
   - Create ECS Task Definition and Fargate Service
   - Set up Application Load Balancer
   - Configure RDS or use MySQL container

2. **Deploy Frontend with S3 and CloudFront**
   - Build the React application
   - Upload to S3 bucket
   - Create CloudFront distribution
   - Configure cache settings and CORS policy

3. **Configure API Gateway and Custom Domain**
   - Create HTTP API in API Gateway
   - Route traffic to backend via ALB
   - Set up SSL with ACM and Route53

4. **CI/CD and Monitoring**
   - Configure GitHub Actions for frontend/backend
   - Automate build and deployment steps
   - Enable CloudWatch logging and alarms

---

#### Content

1. [1. Deploy Backend with ECS Fargate](1-deploy-backend-ecs-fargate/)
2. [2. Deploy Frontend with S3 and CloudFront](2-deploy-frontend-s3-cloudfront/)
3. [3. Configure API Gateway and Domain](3-setup-api-gateway-custom-domain/)
4. [4. CI/CD and Monitoring](4-ci-cd-and-monitoring/)
