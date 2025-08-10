---
title: "Create & Configure S3 Bucket for Hosting"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 3.1 </b> "
---

- **Open Amazon S3 service**

    - Go to the [Amazon S3 dashboard](https://s3.console.aws.amazon.com/s3/home).
    - Click **Create bucket**.

    ![image.png](/images/03/1/1.png)

- **General configuration**

    - **AWS Region**: Select your preferred region (e.g., `Asia Pacific (Sydney) ap-southeast-2`).
    - **Bucket name**: Enter a unique bucket name (e.g., `h2t`).

    ![image.png](/images/03/1/2.png)

- **Object Ownership**

    - Choose **ACLs disabled (recommended)** to enforce bucket owner control.

    ![image.png](/images/03/1/3.png)

- **Block Public Access settings**

    - Uncheck **Block all public access** so the bucket can be used for static website hosting.
    - Acknowledge the warning about making the bucket public.

    ![image.png](/images/03/1/4.png)

- **Default encryption**

    - Keep the default **Server-side encryption with Amazon S3 managed keys (SSE-S3)**.

    ![image.png](/images/03/1/5.png)

- **Create bucket**

    - Click **Create bucket** to finish setup.

- **Edit Bucket Permissions**

    - Go to the **Permissions** tab.
    - Under **Block public access (bucket settings)**, make sure it is **Off**.
    - In **Bucket policy**, click **Edit** and add the following policy:

    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::h2t/*"
        }
      ]
    }
    ```

    ![image.png](/images/03/1/6.png)

- **Save changes**

    - Click **Save changes** to apply the bucket policy.

    ![image.png](/images/03/1/7.png)
