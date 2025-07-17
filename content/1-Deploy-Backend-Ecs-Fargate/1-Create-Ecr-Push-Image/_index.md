---
title: "Create ECR Repository and Push Docker Image"
date: "2025-07-17"
weight: 1 
chapter: false
pre: " <b> 1.1 </b> "
---

- **Create ECR repository using AWS Console**

    - Go to the [ECR dashboard](https://console.aws.amazon.com/ecr/repositories).
    - Click **Create repository**.
    - Choose **Private**, set repository name (e.g. `springboot-backend`) and leave other settings as default.
    - Click **Create** to finish.

    ![image.png](/images/deploy_backend_ecr/create_repo.png)

- **Get push commands from AWS Console**

    - After creating the repository, click on its name.
    - At the top right, click **View push commands**.
    - AWS will show CLI commands required to:
        - Authenticate Docker to ECR
        - Build the Docker image
        - Tag the image
        - Push to ECR

    ![image.png](/images/deploy_backend_ecr/view_push_cmd.png)

- **Login to ECR using Docker CLI**

    - Copy and run the login command from AWS Console.
    - The command looks like this:

    ```bash
    aws ecr get-login-password \
      --region ap-northeast-1 \
      | docker login \
      --username AWS \
      --password-stdin <aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com
    ```

    ![image.png](/images/deploy_backend_ecr/login_ecr.png)

- **Build Docker image from local project**

    - In the root of your Spring Boot project, run:

    ```bash
    docker build -t springboot-backend .
    ```

    ![image.png](/images/deploy_backend_ecr/build_image.png)

- **Tag the Docker image with ECR repository URI**

    ```bash
    docker tag springboot-backend:latest \
      <aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com/springboot-backend:latest
    ```

    ![image.png](/images/deploy_backend_ecr/tag_image.png)

- **Push Docker image to ECR**

    ```bash
    docker push \
      <aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com/springboot-backend:latest
    ```

    ![image.png](/images/deploy_backend_ecr/push_image.png)

- **Verify image pushed to ECR**

    - Go back to the repository on the AWS Console.
    - Click on the **Images** tab.
    - You should see the image with the correct tag and push time.

    ![image.png](/images/deploy_backend_ecr/ecr_result.png)
