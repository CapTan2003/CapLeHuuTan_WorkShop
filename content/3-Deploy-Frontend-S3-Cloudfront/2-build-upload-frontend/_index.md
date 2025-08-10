---
title: "Build & Upload Frontend App to S3"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 3.2 </b> "
---

- **Configure API endpoint using `/api`**

    - In the API client configuration file (e.g., `src/services/apiClient.ts`), set the `BASE_URL` to `/api`:

    ```ts
    const BASE_URL = "/api";
    ```

    - **Reason**:  
      When deploying with **CloudFront Behaviors**, both frontend and backend share the same CDN domain.  
      CloudFront routing rules will work as follows:
        - Requests starting with `/api` → forwarded to the backend (ECS/ALB).
        - All other requests → served from S3 static files.  

      This allows the frontend to call the backend without specifying a separate backend domain, avoiding CORS issues.

    ![image.png](/images/03/2/1.png)

- **Build the frontend**

    - Open terminal and run:
    ```bash
    npm run build
    ```
    ![image.png](/images/03/2/2.png)

- **Build complete**

    - After build, the `build` folder will contain all production-ready static files.
    ![image.png](/images/03/2/3.png)

- **Upload build to S3**

    - Use AWS CLI to sync the `build` folder to your S3 bucket:
    ```bash
    aws s3 sync ./build s3://your-bucket-name --delete
    ```
    - The `--delete` flag removes old files in the bucket that are not present in the new build.
    ![image.png](/images/03/2/4.png)

- **Upload complete**

    - All static assets of the application are now available in your S3 bucket.
    ![image.png](/images/03/2/5.png)
