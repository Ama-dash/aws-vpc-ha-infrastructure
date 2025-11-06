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
- ![fff](https://github.com/user-attachments/assets/b76aa9ef-4889-4f00-a71d-855d4f1014ba)

- ![sssss](https://github.com/user-attachments/assets/6b47eba2-c425-4706-a37c-2e145ea72b42)


  
- **TO Balance:** ALB improves performance and uptime
   ![target](https://github.com/user-attachments/assets/912f1fa2-f760-497a-b815-972c40fa3adf)

   ![load](https://github.com/user-attachments/assets/32cfc412-dfdf-4533-9334-645254aae7f7)

- **TO Connect:** NAT Gateways enable controlled outbound access
  ![21](https://github.com/user-attachments/assets/8b459762-1be5-4974-87fd-ba9025e474e6)
![31](https://github.com/user-attachments/assets/fad20d05-3229-4d08-a2af-c1cdbf9c20a6)


## 📦 Technologies Used

- AWS VPC
- EC2
- NAT Gateway
- Application Load Balancer
- Auto Scaling
- IAM
- Route Tables & Security Groups

## 🖼 Architecture Diagram
<img width="253" height="199" alt="image" src="https://github.com/user-attachments/assets/7d2d4e78-9e1b-4cc2-a57e-72d9ab1a7097" />


## 🚀 Deployment Steps (Manual Deployment)

```bash


# 1. Launch an EC2 Instance
# - Select Amazon Linux / Ubuntu
# - Choose t2.micro (Free tier eligible)
# - Create/Select Key Pair and Security Group (Allow SSH + HTTP)

# 2. Connect to Your EC2 Instance
ssh -i your-key.pem ubuntu@your-ec2-public-ip

# 3. Install Required Packages
sudo apt update -y
sudo apt install -y python3 python3-pip

# 4. Upload Your Project Files (From Local Machine)
scp -i your-key.pem -r . ubuntu@your-ec2-public-ip:/home/ubuntu

# 5. Run the Web Server
python3 -m http.server 8000

# 6. Open Browser to Access Application
http://your-ec2-public-ip:8000


