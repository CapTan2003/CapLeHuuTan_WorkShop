title: "Automate Docker Build and Deployment to ECS"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

- **Create `.github/workflows/docker-ecs-deploy.yml` in backend repository**

    - This workflow automates Docker image build and ECS deployment on every push to `main`.

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

          - name: Build and push Docker image to ECR
            run: |
              docker build -t ${{ secrets.ECR_REPO }} .
              docker tag ${{ secrets.ECR_REPO }}:latest ${{ secrets.ECR_URI }}
              docker push ${{ secrets.ECR_URI }}

          - name: Deploy new image to ECS
            uses: aws-actions/amazon-ecs-deploy-task-definition@v1
            with:
              task-definition: ecs-task-def.json
              service: your-ecs-service
              cluster: your-ecs-cluster
              wait-for-service-stability: true
    ```

    ![image.png](/images/ci_cd/docker_ecs_pipeline.png)

---

- **Required GitHub Secrets**

    - `ECR_REPO`  
    - `ECR_URI`  
    - `AWS_ACCESS_KEY_ID`  
    - `AWS_SECRET_ACCESS_KEY`  
    - And any other environment variables used in the workflow

    ![image.png](/images/ci_cd/github_secrets.png)
