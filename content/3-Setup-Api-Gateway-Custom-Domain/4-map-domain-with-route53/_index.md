---
title: "Set up Route 53 Record for Custom Domain"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 3.4 </b> "
---

- **Open Route 53 Console**

    - Go to [Route 53 Console](https://console.aws.amazon.com/route53/)
    - Click on **Hosted zones**
    - Select the hosted zone for your domain (e.g. `example.com`)

- **Create a new record**

    - Click **Create record**
    - Set the record name: `app` (if you want `app.example.com`)
    - Choose **Record type**: `A – IPv4 address`
    - Select **Alias**: Yes
    - Choose **Alias to: Application Load Balancer (ALB)** or **CloudFront**, depending on usage
    - Select the region and the correct ALB or CloudFront distribution

- **Save the record**

    - Click **Create records**
    - Wait for DNS propagation (can take a few minutes)

    ![route53_record.png](/images/api_gateway/route53_record.png)

- **You can now access your app at your custom domain!**
