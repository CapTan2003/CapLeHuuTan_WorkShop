---
title: "Create and Configure S3 Bucket for Hosting"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

- **Go to the [Amazon S3 Console](https://s3.console.aws.amazon.com/s3)**

- **Create a new bucket for your frontend**

    - Click **Create bucket**
    - Set a globally unique bucket name (e.g., `my-frontend-app`)
    - Choose the correct AWS Region
    - Uncheck **Block all public access** (important for hosting)
    - Acknowledge the warning checkbox
    - Click **Create bucket**

    ![image.png](/images/deploy_frontend/create_s3_bucket.png)

- **Enable static website hosting**

    - Go to the bucket → Click the **Properties** tab
    - Scroll to **Static website hosting**
    - Click **Edit**
    - Enable static website hosting
    - Set **Index document**: `index.html`
    - Set **Error document**: `index.html` (for SPA routing)
    - Save changes

    ![image.png](/images/deploy_frontend/enable_static_hosting.png)

- **Make the bucket public**

    - Go to the **Permissions** tab
    - Scroll to **Bucket policy**
    - Click **Edit**
    - Paste the following policy (replace `my-frontend-app` with your bucket name):

    ```json
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Sid": "PublicReadGetObject",
          "Effect": "Allow",
          "Principal": "*",
          "Action": "s3:GetObject",
          "Resource": "arn:aws:s3:::my-frontend-app/*"
        }
      ]
    }
    ```

    - Save the policy

    ![image.png](/images/deploy_frontend/set_bucket_policy.png)

- **Confirm public access**

    - Go back to **Objects** tab
    - You should now be able to access files from the public endpoint like:

    ```
    http://my-frontend-app.s3-website-ap-northeast-1.amazonaws.com
    ```

---

Let me know when you're ready for step 3: Set up CloudFront Distribution.
