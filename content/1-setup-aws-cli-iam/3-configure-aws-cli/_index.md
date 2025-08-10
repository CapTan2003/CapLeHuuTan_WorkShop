---
title: "Configure AWS CLI on your machine"
date: "2025-07-17"
weight: 3
chapter: false
pre: " <b> 1.3 </b> "
---

- **Install AWS CLI (if not already installed)**

    - Download and install AWS CLI from the [official installation guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).
    - Verify installation by running:
      ```bash
      aws --version
      ```
    - Ensure the version output confirms AWS CLI is installed.

    ![image.png](/images/01/3/1.png)

- **Open Terminal and run AWS Configure**

    - Open **Terminal** (macOS/Linux) or **Command Prompt** (Windows).
    - Run the following command:
      ```bash
      aws configure
      ```

    ![image.png](/images/01/3/2.png)

- **Enter your AWS credentials**

    - **AWS Access Key ID**: Enter the Access Key ID from the previous step.
    - **AWS Secret Access Key**: Enter the Secret Access Key you saved.
    - **Default region name**: Enter your preferred region (e.g., `ap-southeast-2`).
    - **Default output format**: Enter `json` (recommended).

    ![image.png](/images/01/3/3.png)

- **Verify AWS CLI configuration**

    - Test your configuration by running:
      ```bash
      aws sts get-caller-identity
      ```
    - You should see output showing your **UserID**, **Account**, and **ARN**.
    - This confirms AWS CLI is properly configured and authenticated.

    ![image.png](/images/01/3/4.png)
