---
title: "Create ECS Task Definition for Backend Application"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 1.2 </b> "
---

- **Open Amazon ECS Console**

    - Navigate to the [ECS Console](https://console.aws.amazon.com/ecs).
    - On the left panel, click **Task Definitions**, then select **Create new Task Definition**.

    ![image.png](/images/deploy_backend_taskdef/open_ecs_task_definitions.png)

- **Select launch type**

    - On the first screen, choose **FARGATE** as the launch type.
    - Click **Next step**.

    ![image.png](/images/deploy_backend_taskdef/select_fargate.png)

- **Define task settings**

    - **Task Definition Name**: enter a name (e.g., `springboot-backend-task`).
    - **Task Role**: choose `ecsTaskExecutionRole`. If it doesn’t exist, click "Create new role" and allow default permissions.
    - **Operating system family**: keep as **Linux**.
    - **CPU**: choose `512 (.5 vCPU)` or `1024 (1 vCPU)` depending on your needs.
    - **Memory**: choose `1024 (1 GB)` or higher.
    - **Network mode**: leave as **awsvpc**.

    ![image.png](/images/deploy_backend_taskdef/task_settings.png)

- **Add container definition**

    - Scroll to **Container definitions** and click **Add container**.
    - Fill in the following details:
        - **Container name**: `springboot-container`
        - **Image URI**: your ECR image URI  
          (e.g., `<aws_account_id>.dkr.ecr.ap-northeast-1.amazonaws.com/springboot-backend:latest`)
        - **Port mappings**: set **Container port** to `8080`

    ![image.png](/images/deploy_backend_taskdef/add_container.png)

- **Configure logging**

    - In the container section, enable **Log configuration**:
        - Select **awslogs** as the log driver
        - **Log group**: `/ecs/springboot-backend` (or create one in CloudWatch)
        - **Region**: `ap-northeast-1`
        - **Stream prefix**: `springboot`

    ![image.png](/images/deploy_backend_taskdef/logging_config.png)

- **Review and create**

    - Click **Next step** to review your configuration.
    - Click **Create** to finish creating the Task Definition.

    ![image.png](/images/deploy_backend_taskdef/review_create_task.png)

- **Confirmation**

    - Once created, your Task Definition will appear in the ECS Console.
    - You can now use it to create a Fargate Service in the next step.

    ![image.png](/images/deploy_backend_taskdef/task_definition_created.png)
