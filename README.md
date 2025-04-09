 # Web Host on EC2 with Load Balancer and Auto Scaling

A highly available and scalable website hosted on AWS using EC2 instances, spread across multiple subnets in a single VPC. This setup ensures fault tolerance and automatic scaling through an Application Load Balancer and Auto Scaling Group.

---

## 📌 Project Overview

This project demonstrates:

- Hosting a website on two EC2 instances
- Deployment across **two public subnets**
- Access control using **security groups**
- **Application Load Balancer** for traffic distribution
- **Auto Scaling Group** for high availability and scalability

---

## ⚙️ Tech Stack

- **AWS EC2 (Amazon Linux 2)**
- **Amazon VPC** (with 2 public subnets)
- **Application Load Balancer (ALB)**
- **Auto Scaling Group (ASG)**
- **Apache HTTP Server**
- **Security Groups (SSH + HTTP)**

---

## 🧱 Architecture


![ChatGPT Image Apr 8, 2025, 04_58_56 PM](https://github.com/user-attachments/assets/30dd9493-dd7e-4cd6-8773-c67c1984255e)


---

## 🚀 Deployment Steps

### 1. VPC & Networking
- Create a custom VPC with two **public subnets**.
- Ensure each subnet is in a **different Availability Zone**.

### 2. Security Group
- Allow:
  - `SSH (Port 22)` – from your IP
  - `HTTP (Port 80)` – from anywhere (0.0.0.0/0)

### 3. EC2 Launch Template
- Amazon Linux 2 AMI
- Use **user data** script or custom script to install Apache:
  ```bash
  #!/bin/bash
  yum update -y
  yum install httpd -y
  systemctl start httpd
  systemctl enable httpd
  echo "<h1>Welcome to EC2 hosted website</h1>" > /var/www/html/index.html
