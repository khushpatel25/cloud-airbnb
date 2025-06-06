# 🏡 Airbnb-Clone on AWS — Scalable Cloud Architecture

## 📌 Overview
This project deploys a full-stack open-source Airbnb-clone web application using a highly available, secure, and cost-optimized architecture on AWS. The application is based on React (frontend) and Node.js/Express (backend), with MongoDB as the database. Infrastructure provisioning is managed via AWS CloudFormation.

---

## 🚀 Key Features
- ✅ Frontend and backend hosted on separate EC2 instances
- ✅ Backend Auto Scaling group with Elastic Load Balancer
- ✅ Secure self-hosted MongoDB with EBS
- ✅ Infrastructure as Code using AWS CloudFormation
- ✅ Secrets managed via AWS Secrets Manager
- ✅ Follows AWS Well-Architected Framework (Security, Reliability, Performance, Cost, Ops)

---

## 🧱 Architecture

## 🖼️ Architecture Diagrams

### 🔸 Architecture Diagram
![Architecture Diagram](/images/Architecture.png)

### 🔸 VPC and Subnet Overview
![VPC Overview](/images//vpc.png)

### 🔸 Application Load Balancer (ALB)
![ALB Setup](/images/ALB.png)
![ALB Config](/images/ALB-config.png)

### 🔸 Backend Auto Scaling Group (ASG)
![Auto Scaling Group](/images/ASG.png)

### AWS Services Used:

| Category     | Services                                          |
|--------------|---------------------------------------------------|
| Compute      | EC2, EC2 Auto Scaling                             |
| Storage      | Elastic Block Store (EBS)                         |
| Networking   | VPC, Internet Gateway, NAT Gateway, ELB           |
| Database     | Self-hosted MongoDB on EC2                        |
| Management   | AWS CloudFormation                                |
| Security     | AWS Secrets Manager, Security Groups              |

---

## 🔄 Application Flow

1. **User Access**: Users interact with the frontend hosted on a public EC2 instance.
2. **Frontend to Backend**: Requests route through an Application Load Balancer to backend EC2 instances (auto-scaled).
3. **Data Handling**: Backend interacts with a MongoDB instance hosted on a private EC2 with persistent EBS volume.
4. **Secrets Management**: Sensitive configurations like API keys are securely retrieved from AWS Secrets Manager.
5. **Backend Internet Access**: NAT Gateway enables backend EC2s in private subnets to access the internet for package updates.

---

## 🧰 Infrastructure as Code (IaC)

Provisioned using a single CloudFormation template that includes:

- VPC with public and private subnets
- Internet and NAT gateways
- Security groups for different components
- EC2 Launch Configuration and Auto Scaling Group
- Application Load Balancer and Target Group
- MongoDB EC2 instance with EBS volume
- Scripts to automate Docker container deployments

---

## 🛡️ Well-Architected Framework Alignment

### 🔐 Security
- Private subnets for backend and database
- Secrets stored securely in AWS Secrets Manager
- Security groups restrict traffic based on role

### 💡 Reliability
- Multi-AZ setup with Auto Scaling ensures high availability
- Health checks and failover support through ALB

### ⚡ Performance Efficiency
- Optimized EC2 instance types
- Localized communication within private subnets

### 💸 Cost Optimization
- On-demand and scalable infrastructure
- Infrastructure automation reduces manual ops overhead

### 📈 Operational Excellence
- Fully automated provisioning using CloudFormation
- Docker-based microservices simplify deployment and rollback

---

## 📦 Deployment

1. Clone the project:
   ```bash
   git clone https://github.com/khushpatel25/cloud-airbnb
   ```

2. Launch CloudFormation template:
   - Deploy the infrastructure using the `cloudFormation.yaml` file.
   - It includes VPC, subnets, EC2 setup, ALB, Auto Scaling, and Secrets Manager integration.

3. SSH into frontend/backend EC2 instances (if needed) and verify Docker containers are running:
   ```bash
   docker ps
   ```

4. Access the application via frontend public IP.

---

## 📎 References

- [AWS EC2 Docs](https://docs.aws.amazon.com/ec2/)
- [AWS CloudFormation Docs](https://docs.aws.amazon.com/cloudformation/)
- [Secrets Manager](https://docs.aws.amazon.com/secretsmanager/)
- [MongoDB on EC2](https://medium.com/@pnle/install-standalone-mongodb-community-edition-on-aws-ec2-c3ced446370b)

