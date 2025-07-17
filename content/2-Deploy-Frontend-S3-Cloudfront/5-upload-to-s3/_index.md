---
title: "Upload Static Files to S3"
date: "2025-07-17"
weight: 5
chapter: false
pre: " <b> 2.5 </b> "
---

- **Upload using AWS Console**

  - Go to the [S3 Console](https://s3.console.aws.amazon.com/s3/)
  - Open your S3 bucket used for hosting
  - Click **Upload** → **Add files/folder** from your `build/` or `dist/` directory (depending on your framework)
  - Set the **Content-Type** for `.html`, `.js`, `.css`, `.json` files if needed
  - Click **Upload**

  ![upload-ui](/images/deploy_frontend/upload_files_ui.png)

---

- **Upload using AWS CLI**

  If you’ve installed the AWS CLI and configured credentials:

  ```bash
  aws s3 cp build/ s3://your-bucket-name/ --recursive
