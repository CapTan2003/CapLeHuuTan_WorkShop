---
title: "Create access keys for the IAM user"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 1.2 </b> "
---

- **Open IAM Users page**

    - Go to the [IAM dashboard](https://console.aws.amazon.com/iamv2/home).
    - In the left menu, click **Users**.
    - Select the user you created (e.g., `dev-h2t`).

    ![image.png](/images/01/2/1.png)

- **Create an Access Key**

    - In the user details page, go to the **Security credentials** tab.
    - In the **Access keys** section, click **Create access key**.

    ![image.png](/images/01/2/2.png)

- **Choose access key type**

    - Select **Command Line Interface (CLI)**.
    - Check the confirmation box: *I understand the above recommendation…*
    - Click **Next**.

    ![image.png](/images/01/2/3.png)

- **Generate and save Access Key**

    - Click **Create access key**.
    - Copy the **Access key** and **Secret access key** to a `.csv` file or save securely.
    - **Note:** Once you close the window, you **cannot view** the Secret access key again.

    ![image.png](/images/01/2/4.png)
