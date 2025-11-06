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

🌐 Traffic Flow Summary
Client → ALB (Public Subnet) → EC2 Servers (Private Subnets)
                ↑
             NAT GW → Internet (for updates only)
                ↑
         Bastion Host (SSH access)


## 🚀 How to Deploy
🚀 How to Deploy
1️⃣ Create the Network

Create a VPC

Create 2 Public Subnets and 2 Private Subnets

Attach Internet Gateway

Create:

Public Route Table → Route to Internet Gateway

Private Route Table → Route to NAT Gateways

Deploy NAT Gateways (one per AZ for high availability)

2️⃣ Launch Bastion Host

Create EC2 instance in Public Subnet

Allow SSH only from your IP

Connect:

ssh -i aws_login.pem ubuntu@<BASTION_PUBLIC_IP>

3️⃣ Launch Private EC2 Instances

Launch into Private Subnets

No Public IP assigned

Security Group allows SSH only from Bastion SG

4️⃣ SSH into Private EC2 via Bastion

From local machine:

ssh -i aws_login.pem -o "ProxyJump ubuntu@<BASTION_PUBLIC_IP>" ubuntu@<PRIVATE_EC2_PRIVATE_IP>


Or from inside Bastion:

chmod 400 aws_login.pem
ssh -i aws_login.pem ubuntu@<PRIVATE_EC2_PRIVATE_IP>

5️⃣ Deploy Web Page
cd /var/www/html
sudo vim index.html


Example:

<h1>Hello from Private EC2!</h1>

6️⃣ Start Web Server
sudo apt update
sudo apt install nginx -y
sudo systemctl restart nginx


