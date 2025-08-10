---
title: "Create CloudFront Distribution & Set up Origins"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 3.3 </b> "
---

- **Open CloudFront**

    - Go to **Amazon CloudFront** in AWS Console.
    - Click **Create a CloudFront distribution**.

    ![image.png](/images/03/3/1.png)

- **Start distribution setup**

    - Enter **Distribution name**: `H2T`.
    - Select **Single website or app**.
    - (No custom domain configured at this step.)
    - Click **Next**.

    ![image.png](/images/03/3/2.png)

- **Choose S3 as Frontend Origin**

    - **Origin type**: select **Amazon S3**.
    - **S3 origin**: choose your frontend S3 bucket.
    - **Origin path**: leave blank.

    ![image.png](/images/03/3/3.png)

- **Allow CloudFront to access S3 & use default settings**

    - Tick **Allow private S3 bucket access to CloudFront**.
    - **Origin settings**: choose **Use recommended origin settings**.
    - Click **Next**.

    ![image.png](/images/03/3/4.png)

- **Skip WAF**

    - Select **Do not enable security protections**.
    - Click **Next**.

    ![image.png](/images/03/3/5.png)

- **Review & create distribution**

    - Check **Origin** and **Cache settings**.
    - Click **Create distribution**.

    ![image.png](/images/03/3/6.png)

- **Open Origins tab of the created distribution**

    - Go to **Distributions → Origins**.
    - Click **Create origin**.

    ![image.png](/images/03/3/7.png)

- **Add Backend Origin (ALB) – HTTP**

    - **Origin domain**: paste your **ALB DNS**.
    - **Protocol**: select **HTTP only**.
    - **HTTP port**: `80`.
    - **Origin path**: leave blank.
    - **Name**: set a name (e.g., `backend-alb`).

    ![image.png](/images/03/3/8.png)

- **Keep HTTP – No TLS configuration**

    - Do not choose HTTPS, keep HTTP.
    - **Origin path**: leave blank.
    - **Enable Origin Shield**: set to **No**.

    ![image.png](/images/03/3/9.png)

- **Complete Origins setup**

    - Confirm there are **2 origins**:
        - **S3** (frontend).
        - **ALB HTTP** (backend).
    - Next step is to configure **Behaviors**:
        - `/api/*` → **ALB (backend)**.
        - Default → **S3 (frontend)**.

    ![image.png](/images/03/3/10.png)
