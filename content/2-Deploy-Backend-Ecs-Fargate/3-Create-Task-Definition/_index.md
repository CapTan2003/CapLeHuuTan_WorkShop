---
title: "Create ECS Task Definition for Backend Container"
date: "2025-08-10"
weight: 3
chapter: false
pre: " <b> 2.3 </b> "
---

- **Open Amazon ECS service**

    - Go to the [Amazon ECS dashboard](https://console.aws.amazon.com/ecs).
    - On the main page, click **Get started** to begin deploying a containerized application.

    ![image.png](/images/02/3/1.png)

- **Access Task Definitions**

    - In the left menu, select **Task definitions**.
    - Click **Create new task definition** to start.

    ![image.png](/images/02/3/2.png)

- **Configure Task Definition**

    - **Task definition family**: `h2t-backend-task`.
    - **Launch type**: Select **AWS Fargate**.
    - **Operating system/Architecture**: `Linux/X86_64`.
    - **Network mode**: `awsvpc`.

    ![image.png](/images/02/3/3.png)

- **Set Task Size and Roles**

    - **CPU**: `1 vCPU`.
    - **Memory**: `3 GB`.
    - **Task role**: Leave blank.
    - **Task execution role**: Select **Create new role**.

    ![image.png](/images/02/3/4.png)

- **Configure Container Details**

    - **Name**: `h2t-backend`.
    - **Image URI**:  
      ```
      740994884477.dkr.ecr.ap-southeast-2.amazonaws.com/h2t/backend:latest
      ```
    - **Container port**: `8080`.
    - **Protocol**: `TCP`.
    - **App protocol**: `HTTP`.

    ![image.png](/images/02/3/5.png)

- **Configure Storage & Monitoring (optional)**

    - **Volumes**: Add volumes if needed.
    - **Monitoring**: Optionally enable AWS Distro for OpenTelemetry.
    - **Tags**: Add tags to organize resources.
    - Click **Create** to finish.

    ![image.png](/images/02/3/6.png)

- **Verify Task Definition Creation**

    - Green notification: *Task definition successfully created*.
    - Task `h2t-backend-task:1` has been created.
    - **ARN**:  
      ```
      arn:aws:ecs:ap-southeast-2:740994884477:task-definition/h2t-backend-task:1
      ```
    - **Status**: `ACTIVE`.
    - **Launch type**: `Fargate`.
    - **Network mode**: `awsvpc`.

    ![image.png](/images/02/3/7.png)
