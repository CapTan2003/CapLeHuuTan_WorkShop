---
title: "Build frontend application for production"
date: "2025-07-17"
weight: 1
chapter: false
pre: " <b> 2.1 </b> "
---

- **Navigate to the frontend project directory (if applicable)**

    ```bash
    cd frontend
    ```

- **Install required dependencies**

    - If not installed yet, run:

    ```bash
    npm install
    ```

- **Build the application for production**

    - Run the following command to build your frontend (React, Vue, etc.):

    ```bash
    npm run build
    ```

    - The output folder is usually `build/` (React) or `dist/` (Vue, Vite)

    - The result will be a set of optimized HTML, JS, and CSS files ready to upload to S3

    ![image.png](/images/deploy_frontend/build_output.png)

- **Check the build output folder**

    - Verify that it contains files like `index.html`, `main.js`, `style.css`, etc.:

    ```bash
    ls build
    ```

    or

    ```bash
    ls dist
    ```

    - If the files are present, you're ready to move to the next step: upload to S3 and serve via CloudFront
