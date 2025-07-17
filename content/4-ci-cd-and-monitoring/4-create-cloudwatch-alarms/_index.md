title: "Create CloudWatch Alarms for Monitoring"
date: "2025-07-17"
weight: 4
chapter: false
pre: " <b> 4.4 </b> "
---

We created CloudWatch alarms to monitor system health, focusing on ECS service performance and API Gateway errors.

---

- **ECS Service (CPU & Memory) Monitoring**

    - Accessed [CloudWatch Console](https://console.aws.amazon.com/cloudwatch/home).
    - Chose **Alarms → Create Alarm**.
    - Selected **ECS Metrics**, then picked `CPUUtilization` and `MemoryUtilization` for the backend service.
    - Set the following conditions:
        - Threshold: `>= 70%`
        - Period: `5 minutes`
        - Consecutive evaluations: `3`
    - Added notification action via SNS.

    ![image.png](/images/ci_cd/alarm_ecs_cpu.png)

---

- **API Gateway Error Monitoring**

    - Chose metric `5XXError` and `Latency` under **API Gateway Metrics**.
    - Set thresholds (e.g., more than 10 errors in 5 minutes).
    - Added alarm name and SNS notification target.

    ![image.png](/images/ci_cd/alarm_apigw_errors.png)

---

These alarms were deployed and tested successfully. We now receive alerts if the system exceeds performance thresholds or API errors occur.
