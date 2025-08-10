---
title: "Home"
date: "2025-07-17"
weight: 1
chapter: false
---

# Deploying a Decoupled Web Application on AWS  
## Frontend + Backend using CDN Behavior

#### Overview

This workshop demonstrates how to deploy a modern decoupled web application (**Decoupled Architecture**) on AWS.  
The system consists of a **Frontend** (React SPA hosted on S3 and delivered via CloudFront) and a **Backend** (Spring Boot container running on ECS Fargate behind an Application Load Balancer, using MySQL on Amazon RDS).  
All traffic is routed through **CloudFront Behaviors** for both frontend and backend, eliminating the need for a separate SSL certificate on the backend.

#### Technology Used

- **Frontend**  
  - React SPA  
  - Hosted on **Amazon S3**  
  - Delivered via **Amazon CloudFront**  

- **Backend**  
  - Java Spring Boot API  
  - Containerized with **Docker**  
  - Runs on **ECS Fargate**  
  - Behind **Application Load Balancer**  
  - **Auto Scaling** based on CPU/Memory usage  

- **Database**  
  - **Amazon RDS** (MySQL)  

- **Infrastructure Tools**  
  - AWS CLI, IAM  

---

#### Modules

1. **Set up AWS CLI & IAM**
   - Create an IAM user with necessary permissions
   - Configure AWS CLI to log in to your AWS account

2. **Deploy Backend with ECS Fargate**
   - Create Amazon RDS MySQL  
   - Build backend Docker image and push to ECR  
   - Define ECS Task Definition  
   - Create ECS Cluster and Service (with ALB, Target Group, Auto Scaling)  

3. **Deploy Frontend with S3 and CloudFront**
   - Create & configure S3 bucket for storing the project build files  
   - Build the React project (production) and upload build files to S3  
   - Create CloudFront Distribution  
   - Set up Origins:  
     - Origin 1: Frontend (S3 Bucket)  
     - Origin 2: Backend (Application Load Balancer)  

4. **Configure CloudFront Behavior**
   - **Behavior for each origin**:  
     - FE: `/`, `/static/*`, `/*.js`, `/*.css` → S3 origin  
     - BE: `/api/*` → ALB origin  
   - **CORS policy configuration**:  
     - Allow the frontend domain to access backend APIs  


---
### Architecture

![System Architecture](/images/kientruc.png)

---

#### Content

1. [1. Set up AWS CLI & IAM](1-setup-aws-cli-iam/)  
2. [2. Deploy Backend with ECS Fargate](2-deploy-backend-ecs-fargate/)  
3. [3. Deploy Frontend with S3 and CloudFront](3-deploy-frontend-s3-cloudfront/)  
4. [4. Configure CloudFront Behavior](4-configure-cloudfront-behavior/)  
