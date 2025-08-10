---
title: "Create access keys for the IAM user"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 1.2 </b> "
---

## Create access keys for the IAM user

Follow the steps below to create access keys for the IAM user you created in the previous step.

---

### **1. Open IAM Users page**

- Go to the [IAM dashboard](https://console.aws.amazon.com/iamv2/home).
- In the left menu, click **Users**.
- Select the user you created (e.g., `dev-h2t`).

![image.png](/images/01/2/1.png)

---

### **2. Create an Access Key**

- In the user details page, go to the **Security credentials** tab.
- In the **Access keys** section, click **Create access key**.

![image.png](/images/01/2/2.png)

---

### **3. Choose access key type**

- Select **Command Line Interface (CLI)**.
- Check the confirmation box: *I understand the above recommendation…*
- Click **Next**.

![image.png](/images/01/2/3.png)

---

### **4. Generate and save Access Key**

- Click **Create access key**.
- Copy the **Access key** and **Secret access key** to a `.csv` file or save securely.
- **Note:** Once you close the window, you **cannot view** the Secret access key again.

![image.png](/images/01/2/4.png)
