# 🚀 HTML App CI/CD Pipeline using GitHub Actions & AWS EC2

This project demonstrates a complete **CI/CD pipeline** for deploying a **static HTML application** onto an **AWS EC2 instance** using **GitHub Actions** and **Nginx** as the web server.

---

## 🧩 Project Overview

- **Frontend:** Static HTML  
- **Web Server:** Nginx  
- **CI/CD Tool:** GitHub Actions  
- **Hosting:** AWS EC2 (Ubuntu)  
- **Deployment Type:** Continuous Deployment on code push to the `main` branch  

The pipeline automates the entire process — from fetching the latest code, packaging it, securely transferring files to EC2, and restarting the Nginx server.

---

## 🧠 Workflow Overview

### CI/CD Workflow Trigger
- **On Push:** Triggered automatically when changes are pushed to the `main` branch.  
- **Manual Trigger:** Can also be manually dispatched from the Actions tab in GitHub.

### Workflow Stages
| Stage | Description |
|--------|-------------|
| **Checkout Code** | Uses `actions/checkout` to clone the repository. |
| **Build** | Validates the HTML app (optional for static apps). |
| **Deploy to EC2** | Copies the build files to the EC2 instance using `appleboy/scp-action`. |

---

## 🔐 Secrets Configuration

| Secret Name | Description                                   |
| ----------- | --------------------------------------------- |
| `EC2_HOST`  | Public IP or DNS of your EC2 instance         |
| `EC2_USER`  | SSH username (usually `ubuntu` or `ec2-user`) |
| `SSH_KEY`   | Private SSH key for EC2 access                |

> 💡 Set these under **Settings → Secrets and variables → Actions** in your GitHub repository.

---

## 🖥️ EC2 Setup Guide

1. **Launch an Ubuntu EC2 instance**

   * Install Nginx:

     ```bash
     sudo apt update && sudo apt install nginx -y
     sudo systemctl enable nginx
     ```

2. **Configure permissions**

   * Ensure `/var/www/html` is writable by the EC2 user:

     ```bash
     sudo chown -R ubuntu:ubuntu /var/www/html
     ```

3. **Allow HTTP traffic**

   * Open inbound port 80 in your EC2 security group.

4. **Test manually**

   * Visit `http://<EC2-Public-IP>` to confirm Nginx is serving content.

---

## 🧾 Sample Screenshots

📸

![Nginx service running on EC2](https://github.com/aviral31/Github-Actions/blob/ce10fd657d808aab0d898be4b6813ebad741a0ae/ss.png)

---

## 🚀 Deployment Validation

After a successful workflow run:

* Visit **`http://<your-ec2-public-ip>`**
* You should see your **HTML application** served via **Nginx**

---

---


---

> 🏁 *“Automate the boring stuff — Deploy with confidence!”*

```

---
