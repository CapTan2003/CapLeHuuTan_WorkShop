---
title: "Create Behavior for backend"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

- **Open Behaviors tab**
    - Go to the CloudFront distribution you created.
    - Select the **Behaviors** tab.
    - By default, there is a **Default behavior** pointing to S3.
    - Click **Create behavior** to add a new rule.

    ![image.png](/images/04/1/1.png)

- **Enter Behavior details**
    - **Path pattern**: `/api/*` (to route API requests).
    - **Origin or origin groups**: select **backend origin (ALB)**.
    - **Compress objects automatically**: choose **Yes**.
    - **Viewer protocol policy**: **Redirect HTTP to HTTPS**.
    - **Allowed HTTP methods**: **GET, HEAD, OPTIONS, PUT, POST, PATCH, DELETE**.

    ![image.png](/images/04/1/2.png)

- **Configure policy**
    - **Origin request policy**: choose `AllViewer` (to forward all request headers/params/body).
    - No **Response headers policy** configuration at this step.
    - Leave **Function associations** empty.

    ![image.png](/images/04/1/3.png)

- **Create Behavior**
    - Click **Create behavior** to save.
    - The `/api/*` behavior is now added and will take priority over the Default behavior.
