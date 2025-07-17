---
title: "Set up SSL using AWS Certificate Manager (ACM)"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 3.3 </b> "
---

- **Go to AWS Certificate Manager (ACM)**

    - Open [ACM Console](https://console.aws.amazon.com/acm/)
    - Click **Request a certificate**
    - Choose **Request a public certificate**
    - Click **Next**

- **Enter domain name**

    - Type in your domain (e.g. `app.example.com`)
    - Optionally, add `www.app.example.com` as an alternate name
    - Click **Next**

- **Choose validation method**

    - Select **DNS validation** (recommended)
    - Click **Next**, then **Confirm and request**

- **Add DNS record to Route 53**

    - Click **Create record in Route 53** (if hosted zone is managed by Route 53)
    - Wait a few minutes until status becomes **"Issued"**

    ![acm_issued.png](/images/api_gateway/acm_issued.png)

- **Note: ACM certificates must be in region `us-east-1` for CloudFront.**
