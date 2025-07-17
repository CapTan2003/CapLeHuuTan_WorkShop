title: "Enable CloudWatch Logs for ECS and API Gateway"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 4.3 </b> "
---

- **Enable CloudWatch Logs for ECS Task**

    - During ECS Task Definition setup:
      - Open the **Log configuration** section.
      - Choose **awslogs** as the log driver.
      - Fill in:
        - **Log group**: `/ecs/springboot-backend`
        - **Region**: `ap-northeast-1`
        - **Stream prefix**: `ecs`
    - ECS will automatically send container logs to CloudWatch.

    ![image.png](/images/ci_cd/enable_logs_ecs.png)

---

- **Enable CloudWatch Logs for API Gateway**

    - In the **API Gateway Console**, select your API.
    - Go to **Stages** → select your stage (e.g., `prod`).
    - Click on the **Logs/Tracing** tab:
        - Enable **CloudWatch Logs**.
        - Set **Log level** to `INFO` or `ERROR`.
        - Optionally check **Log full requests/responses data**.

    ![image.png](/images/ci_cd/enable_logs_apigw.png)

---

- **View logs in CloudWatch**

    - Go to [CloudWatch Console](https://console.aws.amazon.com/cloudwatch/home).
    - Navigate to **Log groups** → search for the log group.
    - Click to view real-time log entries.
