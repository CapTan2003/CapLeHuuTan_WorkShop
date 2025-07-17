title: "Tự động Build Docker và Triển khai lên ECS"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

- **Tạo file `.github/workflows/docker-ecs-deploy.yml` trong repository backend**

    - Workflow này sẽ tự động build image Docker và triển khai lên ECS mỗi khi có push lên nhánh `main`.

    ```yaml
    name: Docker Build & Deploy to ECS

    on:
      push:
        branches: [main]

    jobs:
      deploy:
        runs-on: ubuntu-latest

        steps:
          - name: Checkout code
            uses: actions/checkout@v3

          - name: Set up Docker Buildx
            uses: docker/setup-buildx-action@v2

          - name: Authenticate to Amazon ECR
            uses: aws-actions/amazon-ecr-login@v1

          - name: Build và push Docker image lên ECR
            run: |
              docker build -t ${{ secrets.ECR_REPO }} .
              docker tag ${{ secrets.ECR_REPO }}:latest ${{ secrets.ECR_URI }}
              docker push ${{ secrets.ECR_URI }}

          - name: Triển khai image mới lên ECS
            uses: aws-actions/amazon-ecs-deploy-task-definition@v1
            with:
              task-definition: ecs-task-def.json
              service: your-ecs-service
              cluster: your-ecs-cluster
              wait-for-service-stability: true
    ```

    ![image.png](/images/ci_cd/docker_ecs_pipeline.png)

---

- **Các GitHub Secrets cần thiết**

    - `ECR_REPO`  
    - `ECR_URI`  
    - `AWS_ACCESS_KEY_ID`  
    - `AWS_SECRET_ACCESS_KEY`  
    - Và các biến môi trường khác nếu có sử dụng trong workflow

    ![image.png](/images/ci_cd/github_secrets.png)
