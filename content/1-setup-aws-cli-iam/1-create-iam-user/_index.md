---
title: "Create IAM User for S3 & ECR Access"
date: "2025-07-17"
weight: 1 
chapter: false
pre: " <b> 1.1 </b> "
---

- **Open IAM Users page**

    - Go to the [IAM dashboard](https://console.aws.amazon.com/iamv2/home).
    - In the left menu, under **Access management**, click **Users**.
    - Click **Create user**.

    ![image.png](/images/01/1/1.png)

- **Specify user details**

    - In **User name**, enter: `dev-h2t`.
    - Do **not** check *Provide user access to the AWS Management Console* (only programmatic access is needed).
    - Click **Next**.

    ![image.png](/images/01/1/2.png)

- **Attach permissions – AmazonS3FullAccess**

    - Choose **Attach policies directly**.
    - Search and select the policy: **AmazonS3FullAccess**.

    ![image.png](/images/01/1/3.png)

- **Attach permissions – AmazonEC2ContainerRegistryFullAccess**

    - Continue searching and select the policy: **AmazonEC2ContainerRegistryFullAccess**.
    - Click **Next**.

    ![image.png](/images/01/1/4.png)

- **Review and create**

    - Verify the details:
        - **User name**: `dev-h2t`
        - **Permissions**: AmazonS3FullAccess, AmazonEC2ContainerRegistryFullAccess
    - Click **Create user**.

    ![image.png](/images/01/1/5.png)
