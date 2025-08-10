---
title: "Set Default Root Object & Test"
date: "2025-07-17"
weight: 2
chapter: false
pre: " <b> 4.2 </b> "
---

- **Go to General tab**
    - Click **Edit**.
    - In **Default root object** field, enter `index.html`.
    - Keep other settings unchanged.
    - Click **Save changes**.

    ![image.png](/images/04/2/1.png)
    ![image.png](/images/04/2/2.png)

- **Confirm update success**
    - A green notification appears: **Successfully updated distribution settings**.
    - **Default root object** is now set to `index.html`.

    ![image.png](/images/04/2/3.png)

- **Test frontend access**
    - Open the **Distribution domain name** of CloudFront.
    - The frontend web interface is displayed.

    ![image.png](/images/04/2/4.png)

- **Test other pages**
    - Access other frontend pages (e.g., `/lesson/readings`) to ensure SPA loads correctly.

    ![image.png](/images/04/2/5.png)
