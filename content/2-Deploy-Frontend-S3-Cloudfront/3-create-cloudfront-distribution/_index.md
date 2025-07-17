---
title: "Create CloudFront Distribution"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

- **Go to the [Amazon CloudFront Console](https://console.aws.amazon.com/cloudfront)**

- **Click “Create Distribution” to begin**

  - In **Origin domain**, select your S3 static website endpoint (ending with `.s3-website-<region>.amazonaws.com`)
  - Leave **Origin path** empty
  - For **Origin name**, enter something like `frontend-s3-origin`
  - Set **Viewer protocol policy** to **Redirect HTTP to HTTPS**

  ![image.png](/images/deploy_frontend/create_cloudfront_step1.png)

- **Configure cache behavior settings**

  - Allowed HTTP methods: `GET, HEAD`
  - Cache policy: choose **CachingOptimized**
  - Enable **Compress objects automatically**
  - Set **Viewer protocol policy** to `Redirect HTTP to HTTPS`

  ![image.png](/images/deploy_frontend/cloudfront_cache_behavior.png)

- **Specify default root object**

  - Scroll to **Default root object**
  - Enter `index.html` to load the homepage by default

  ![image.png](/images/deploy_frontend/cloudfront_root_object.png)

- **Review and deploy**

  - Click **Create distribution**
  - Wait a few minutes for status to change from **In Progress** to **Deployed**
  - Once deployed, copy the **Distribution domain name** (e.g., `d123abc.cloudfront.net`) — you’ll use this in custom domain or testing

  ![image.png](/images/deploy_frontend/cloudfront_success.png)
