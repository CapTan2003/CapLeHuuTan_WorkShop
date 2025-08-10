---
title: "Create ECR Repository and Push Docker Image"
date: "2025-08-10"
weight: 1
chapter: false
pre: " <b> 2.2 </b> "
---

- **Open Amazon ECR service**

    - Go to the [Amazon ECR dashboard](https://console.aws.amazon.com/ecr/repositories).
    - Click **Create repository**.

    ![image.png](/images/02/2/1.png)

- **Configure repository settings**

    - **Visibility settings**: Select **Private**.
    - **Repository name**: `h2t/backend`.
    - **Tag immutability**: Select **Mutable**.

    ![image.png](/images/02/2/2.png)

- **Configure encryption settings**

    - **Encryption type**: AES-256 (default).
    - Optionally, select **AWS KMS** if you require a customer-managed key.

    ![image.png](/images/02/2/3.png)

- **Create repository**

    - Click **Create repository**.
    - After creation, note the repository URI:
      ```
      740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend
      ```

    ![image.png](/images/02/2/4.png)

- **View push commands**

    - In the repository detail page, click **View push commands**.
    - AWS will display the commands for:
        1. Authentication
        2. Building the Docker image
        3. Tagging the image
        4. Pushing the image

    ![image.png](/images/02/2/5.png)

- **Authenticate Docker to ECR**

    ```bash
    aws ecr get-login-password --region ap-southeast-2 \
    | docker login --username AWS \
    --password-stdin 740994884477.dkr.ecr.ap-southeast-2.amazonaws.com
    ```

    ![image.png](/images/02/2/6.png)

- **Build Docker image**

    ```bash
    docker build -t h2t/backend .
    ```

    ![image.png](/images/02/2/7.png)

- **Tag Docker image**

    ```bash
    docker tag h2t/backend:latest \
    740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend:latest
    ```

- **Push Docker image to ECR**

    ```bash
    docker push 740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend:latest
    ```

    ![image.png](/images/02/2/8.png)

