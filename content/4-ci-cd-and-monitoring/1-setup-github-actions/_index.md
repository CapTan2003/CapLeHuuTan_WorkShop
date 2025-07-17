---
title: "Setup GitHub Actions for Frontend and Backend"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

- **Create GitHub Actions workflow for Frontend (S3)**

    - Go to your frontend repository.
    - Create a new file at `.github/workflows/deploy-frontend.yml`.

    ```yaml
    name: Deploy Frontend to S3

    on:
      push:
        branches: [main]

    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
          - name: Checkout code
            uses: actions/checkout@v3

          - name: Setup Node.js
            uses: actions/setup-node@v3
            with:
              node-version: 18

          - name: Install dependencies & build
            run: |
              npm ci
              npm run build

          - name: Sync to S3
            uses: jakejarvis/s3-sync-action@master
            with:
              args: --acl public-read --delete
            env:
              AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
              AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
              AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
              AWS_REGION: "ap-northeast-1"
              SOURCE_DIR: "dist"
    ```

    ![image.png](/images/ci_cd/setup_frontend_actions.png)

---

- **Create GitHub Actions workflow for Backend (ECS Fargate)**

    - In your backend repository, create `.github/workflows/deploy-backend.yml`.

    ```yaml
    name: Deploy Backend to ECS

    on:
      push:
        branches: [main]

    jobs:
      deploy:
        runs-on: ubuntu-latest
        steps:
          - name: Checkout code
            uses: actions/checkout@v3

          - name: Setup Docker
            uses: docker/setup-buildx-action@v2

          - name: Login to Amazon ECR
            uses: aws-actions/amazon-ecr-login@v1

          - name: Build and Push Docker image
            run: |
              docker build -t ${{ secrets.ECR_REPO }} .
              docker tag ${{ secrets.ECR_REPO }}:latest ${{ secrets.ECR_URI }}
              docker push ${{ secrets.ECR_URI }}

          - name: Deploy to ECS
            uses: aws-actions/amazon-ecs-deploy-task-definition@v1
            with:
              task-definition: ecs-task-def.json
              service: your-ecs-service
              cluster: your-ecs-cluster
              wait-for-service-stability: true
    ```

    ![image.png](/images/ci_cd/setup_backend_actions.png)

---

- **Make sure to add necessary GitHub Secrets**

    - AWS_ACCESS_KEY_ID  
    - AWS_SECRET_ACCESS_KEY  
    - AWS_S3_BUCKET  
    - ECR_REPO  
    - ECR_URI  
    - Any other variables used in the workflows

    ![image.png](/images/ci_cd/github_secrets.png)
