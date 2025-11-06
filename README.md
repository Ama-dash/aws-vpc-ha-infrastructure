# Highly Available VPC Architecture on AWS

This project demonstrates the deployment of a secure, scalable, and highly available Virtual Private Cloud (VPC) environment on AWS. The architecture is designed for production-grade workloads and follows AWS best practices for network segmentation and resiliency.

## 🏗 Architecture Overview 

- Multi-AZ VPC setup
- Public and Private Subnets
- Application Load Balancer for traffic distribution
- Auto Scaling Group for elastic compute scaling
- NAT Gateways for secure outbound internet access
- Security Groups & NACLs for layered protection

## ✨ Key Components

| Component | Purpose |
|---|---|
| VPC | Isolated network environment |
| Subnets (Public & Private) | Organize resources & control exposure |
| Internet Gateway | Enables public access for ALB |
| NAT Gateway (Multi-AZ) | Secure outbound connectivity from private instances |
| Auto Scaling Group | Automatically scales EC2 capacity |
| Application Load Balancer | Balances traffic across instances |

## 🎯 The 4 TOs

- **TO Scale:** Auto Scaling adapts to traffic
![1111](https://github.com/user-attachments/assets/77c7fc5d-19b6-435c-8b19-1b73be40f538)

- **TO Secure:** Workloads run in private subnets
- **TO Balance:** ALB improves performance and uptime
- **TO Connect:** NAT Gateways enable controlled outbound access
  ![21](https://github.com/user-attachments/assets/8b459762-1be5-4974-87fd-ba9025e474e6)


## 📦 Technologies Used

- AWS VPC
- EC2
- NAT Gateway
- Application Load Balancer
- Auto Scaling
- IAM
- Route Tables & Security Groups

## 🖼 Architecture Diagram
(Insert architecture diagram if you have one — you can ask me to create it.)

---

## 🚀 How to Deploy
(You can add Terraform or AWS CLI commands here if you automate later.)

