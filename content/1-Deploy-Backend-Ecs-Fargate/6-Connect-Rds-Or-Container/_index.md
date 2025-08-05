title: "Connect to Amazon RDS or MySQL container"
date: "2025-07-17"
weight: 6
chapter: false
pre: " <b> 1.6 </b> "
---

- **Option 1: Connect to Amazon RDS (Managed MySQL)**
    - Open the [Amazon RDS Console](https://console.aws.amazon.com/rds/)
    - Click **Create database** → choose **Standard Create**
    - Select Engine: **MySQL** (latest version)
    - Configure basic settings:
      - DB instance identifier: `my-rds-instance`
      - Master username & password
      - Enable **Public access**
      - Port: `3306`
    - In **Connectivity** section:
      - Select appropriate VPC & subnet group
      - Attach or create a **Security Group** allowing inbound traffic on port 3306

    ![image.png](/images/deploy_backend_fargate/rds_create.png)

- **Option 2: Use MySQL container in ECS Cluster**
    - Create a new Task Definition:
      - Image: `mysql:8`
      - Environment variables:
        - `MYSQL_ROOT_PASSWORD`
        - `MYSQL_DATABASE`
        - `MYSQL_USER`
        - `MYSQL_PASSWORD`
    - Run this task inside same VPC & subnet as backend
    - Use internal DNS name or service discovery to connect from backend

- **Update Backend Task Definition**
    - Set environment variables for datasource:
      - `SPRING_DATASOURCE_URL`
      - `SPRING_DATASOURCE_USERNAME`
      - `SPRING_DATASOURCE_PASSWORD`
    - For RDS: use endpoint from RDS console  
    - For MySQL container: use internal service name or IP
