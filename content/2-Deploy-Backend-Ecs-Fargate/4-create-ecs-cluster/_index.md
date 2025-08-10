---
title: "Create ECS Cluster for Backend Container"
date: "2025-08-10"
weight: 4
chapter: false
pre: " <b> 2.4 </b> "
---

- **Open Amazon ECS service**

    - Go to the [Amazon ECS dashboard](https://console.aws.amazon.com/ecs).
    - In the left menu, select **Clusters**.
    - Click **Create cluster** to start a new cluster.

    ![image.png](/images/02/4/1.png)

- **Configure cluster basic settings**

    - **Cluster name**: `h2t-backend-cluster`.
    - Name must be 1–255 characters; allowed: a–z, A–Z, 0–9, hyphen (-), underscore (_).
    - Optionally expand **Service Connect defaults** for service-to-service communication.

    ![image.png](/images/02/4/2.png)

- **Select infrastructure settings**

    - **Infrastructure**: Default is **AWS Fargate (serverless)** with **Fargate** and **Fargate Spot** capacity providers.
    - **AWS Fargate**: Pay-as-you-go, no infrastructure management.
    - **Amazon EC2 instances**: Optional, for persistent workloads.
    - **External instances (ECS Anywhere)**: Optional, can be registered later.

    ![image.png](/images/02/4/3.png)

- **Configure monitoring & optional settings**

    - **Monitoring**:
        - **Container Insights (enhanced)**: Recommended for detailed performance metrics.
        - **Container Insights**: Basic aggregated metrics.
        - **Turned off**: Only default CloudWatch metrics.
    - **Encryption**: Optionally select KMS key for data encryption.
    - **Tags**: Add tags to organize resources.
    - Click **Create** to finish.

    ![image.png](/images/02/4/4.png)

- **Verify cluster creation**

    - Success message: *Cluster h2t-backend-cluster has been created successfully*.
    - Click **View cluster** to see details:
        - **Services**: 0
        - **Tasks**: 0
        - **Container instances**: 0 (using Fargate)
        - **Monitoring**: Container Insights enabled

    ![image.png](/images/02/4/5.png)

- **Summary**

    - ECS cluster created with Fargate serverless configuration.
    - Container Insights enabled for monitoring.
    - Ready to deploy ECS services and run tasks using the created task definitions.
