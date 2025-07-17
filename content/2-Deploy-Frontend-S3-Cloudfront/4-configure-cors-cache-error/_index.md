---
title: "Configure CORS, Cache-Control and Error Handling"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

- **Set up CORS for S3 Bucket**

  - Go to the **S3 Console** → select the bucket used to host your frontend
  - Navigate to the **Permissions** tab → scroll down to **Cross-origin resource sharing (CORS)**
  - Click **Edit** and paste the following JSON:

    ```json
    [
      {
        "AllowedHeaders": ["*"],
        "AllowedMethods": ["GET", "HEAD"],
        "AllowedOrigins": ["*"],
        "ExposeHeaders": [],
        "MaxAgeSeconds": 3000
      }
    ]
    ```

    > You can replace `"*"` in `AllowedOrigins` with a specific domain for better security.

  ![image.png](/images/deploy_frontend/configure_cors.png)

---

- **Configure Cache-Control for static files**

  - On your local machine, after building the project (e.g., `npm run build`), you’ll have static files in a folder like `build/` or `dist/`
  - Before uploading to S3, set the `Cache-Control` header for better performance using AWS CLI or the S3 Console

  Example with AWS CLI:

  ```bash
  aws s3 cp build/ s3://your-bucket-name/ --recursive \
    --cache-control "max-age=86400"
