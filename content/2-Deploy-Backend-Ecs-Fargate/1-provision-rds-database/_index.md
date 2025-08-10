---
title: "Provision RDS Database (MySQL)"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

- **Open Amazon RDS service**

    - Go to the [Amazon RDS dashboard](https://console.aws.amazon.com/rds/home).
    - Click **Create database**.

    ![image.png](/images/02/1/1.png)

- **Choose database creation method and engine**

    - **Database creation method**: Select **Easy create**.
    - **Engine type**: Select **MySQL**.

    ![image.png](/images/02/1/2.png)

- **Set DB instance identifier and username**

    - **DB instance size**: Select **Free tier** (db.t4g.micro).
    - **DB instance identifier**: `study-english`.
    - **Master username**: `admin`.

    ![image.png](/images/02/1/3.png)

- **Configure password and connection**

    - **Credentials management**: Choose **Self managed**.
    - Enable **Auto generate password**.
    - EC2 connection: Choose **Don't connect to an EC2 compute resource**.

    ![image.png](/images/02/1/4.png)

- **Review default settings and create database**

    - Keep default settings for Easy create.
    - Click **Create database**.

    ![image.png](/images/02/1/5.png)

- **Save connection credentials**

    - Copy and save the generated master password (this is the only time you can view it).

    ![image.png](/images/02/1/6.png)

- **Wait for database creation**

    - Status will show **Creating** for a few minutes.

    ![image.png](/images/02/1/7.png)

- **Get RDS endpoint**

    - Go to **Connectivity & security** tab.
    - Copy the **Endpoint** and note the **Port** (3306).

    ![image.png](/images/02/1/8.png)

- **Check security group**

    - In the **VPC security groups** section, click the linked security group.

    ![image.png](/images/02/1/9.png)

- **View inbound rules**

    - Ensure port 3306 is allowed for inbound traffic.

    ![image.png](/images/02/1/10.png)

- **Edit inbound rules**

    - Add a new rule:
        - **Type**: Custom TCP
        - **Port range**: 3306
        - **Source**: 0.0.0.0/0 (for testing; restrict for production)
    - Click **Save rules**.

    ![image.png](/images/02/1/11.png)

- **Connect to RDS using MySQL Workbench**

    - **Connection Name**: RDS study-english
    - **Hostname**: RDS endpoint
    - **Port**: 3306
    - **Username**: admin
    - **Password**: your saved master password

    ![image.png](/images/02/1/12.png)

- **Verify connection and manage database**

    - Once connected, you can create tables, insert data, and run queries.

    ![image.png](/images/02/1/13.png)
