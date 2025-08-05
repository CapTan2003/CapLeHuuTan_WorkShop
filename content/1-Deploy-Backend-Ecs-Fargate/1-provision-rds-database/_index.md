---
title: "Provision RDS Database (MySQL)"
date: "2025-07-17"
weight: 1 
chapter: false
pre: " <b> 1.1 </b> "
---

- **Create RDS database using AWS Console**

    - Go to the [Amazon RDS dashboard](https://console.aws.amazon.com/rds/home).
    - Click **Databases** → then click **Create database**.
    - Under **Database creation method**, select **Standard Create**.

    ![image.png](/images/deploy_backend_rds/create_db_step1.png)

- **Configure engine and version**

    - Engine type: **MySQL**  
    - Version: Choose a stable version like **MySQL 8.0.x**

    ![image.png](/images/deploy_backend_rds/select_engine.png)

- **Set database credentials**

    - DB instance identifier: `study-english`
    - Master username: `admin`
    - Master password: set a secure password and note it down

    ![image.png](/images/deploy_backend_rds/set_credentials.png)

- **Configure instance type and storage**

    - DB instance class: choose a cost-effective option like `db.t3.micro` (Free Tier)
    - Storage: keep default 20 GiB (you may enable auto-scaling)

    ![image.png](/images/deploy_backend_rds/instance_storage.png)

- **Networking and connectivity**

    - VPC: choose the same VPC used for your ECS service
    - Subnet group: use default or appropriate one
    - Public access: **Yes** (for testing from local)  
      👉 For production, switch to **No** later
    - VPC security group: allow **TCP port 3306**

    ![image.png](/images/deploy_backend_rds/network_settings.png)

- **Additional configuration**

    - Initial database name: `study-english`
    - Backup, Monitoring: can be disabled for development/test environments
    - Click **Create database** to start provisioning

    ![image.png](/images/deploy_backend_rds/final_create_db.png)

- **Wait for the database to become available**

    - Status will be `Creating...` for a few minutes.
    - Once it becomes `Available`, click the DB name to view details.

    ![image.png](/images/deploy_backend_rds/db_available.png)

- **Copy the RDS endpoint**

    - Under **Connectivity & security**, find the **Endpoint** field
    - Example: `study-english.c9d2gkxxxxx.ap-northeast-1.rds.amazonaws.com`

    ![image.png](/images/deploy_backend_rds/rds_endpoint.png)

- **(Optional) Test RDS connection from local**

    ```bash
    mysql -h study-english.<region>.rds.amazonaws.com -u admin -p
    ```

    - Make sure:
        - RDS public access is enabled (for testing)
        - Port 3306 is open in the security group
