---
title: "Thiết lập GitHub Actions cho Frontend và Backend"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 4.1 </b> "
---

- **Tạo workflow GitHub Actions cho Frontend (S3)**

    - Truy cập vào repository frontend của bạn.
    - Tạo file mới tại `.github/workflows/deploy-frontend.yml`.

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

          - name: Cài đặt dependencies và build
            run: |
              npm ci
              npm run build

          - name: Đồng bộ lên S3
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

- **Tạo workflow GitHub Actions cho Backend (ECS Fargate)**

    - Trong repository backend, tạo file `.github/workflows/deploy-backend.yml`.

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

          - name: Đăng nhập vào Amazon ECR
            uses: aws-actions/amazon-ecr-login@v1

          - name: Build và đẩy Docker image
            run: |
              docker build -t ${{ secrets.ECR_REPO }} .
              docker tag ${{ secrets.ECR_REPO }}:latest ${{ secrets.ECR_URI }}
              docker push ${{ secrets.ECR_URI }}

          - name: Triển khai lên ECS
            uses: aws-actions/amazon-ecs-deploy-task-definition@v1
            with:
              task-definition: ecs-task-def.json
              service: your-ecs-service
              cluster: your-ecs-cluster
              wait-for-service-stability: true
    ```

    ![image.png](/images/ci_cd/setup_backend_actions.png)

---

- **Đảm bảo đã tạo các biến GitHub Secrets cần thiết:**

    - `AWS_ACCESS_KEY_ID`  
    - `AWS_SECRET_ACCESS_KEY`  
    - `AWS_S3_BUCKET`  
    - `ECR_REPO`  
    - `ECR_URI`  
    - Các biến môi trường khác nếu có

    ![image.png](/images/ci_cd/github_secrets.png)
