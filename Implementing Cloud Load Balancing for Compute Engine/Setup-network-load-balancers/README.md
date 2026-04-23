# 🌐 Network Load Balancer Deployment on Google Cloud

## 📌 Project Overview

This project demonstrates the deployment and configuration of a **Layer 4 Network Load Balancer (NLB)** using Google Cloud Compute Engine. The architecture distributes incoming traffic across multiple backend virtual machine instances to ensure **high availability, scalability, and fault tolerance**.

This was implemented through a hands-on Google Cloud lab to gain practical experience with core cloud infrastructure and networking concepts.

---

## 🏗️ Architecture Summary

The system consists of:

- **Compute Engine VMs**: `www1`, `www2`, `www3`
- **Web Server**: Apache HTTP Server running on each VM
- **Target Pool**: Groups backend VM instances
- **Health Check**: Monitors instance availability via HTTP
- **Static External IP**: Single public entry point
- **Forwarding Rule**: Routes traffic to backend instances on port 80

---

## 🔄 System Flow

```text
Client Request
    ↓
Static External IP (Network Load Balancer)
    ↓
Forwarding Rule (Port 80)
    ↓
Target Pool (Backend Group)
    ↓
Healthy Compute Engine Instances (www1, www2, www3)
```

---

## ⚙️ Key Implementations

### 1. Virtual Machine Deployment
- Provisioned three Compute Engine instances in a single zone
- Installed Apache web server using startup scripts
- Verified web server accessibility via HTTP requests

### 2. Load Balancer Configuration
- Configured a **Network Load Balancer (Layer 4)**
- Enabled distribution of traffic across multiple backend VMs
- Exposed a single static IP as the entry point for clients

### 3. Backend Target Pool
- Grouped VM instances into a regional target pool
- Ensured all backend instances reside within the same region

### 4. Health Checks
- Configured HTTP health checks for backend monitoring
- Automatically removed unhealthy instances from traffic rotation

### 5. Traffic Routing
- Created forwarding rules for port 80 traffic
- Linked static IP address to backend target pool

---

## 🧠 Key Learnings

- Fundamentals of **Layer 4 load balancing**
- Difference between single-server and distributed architectures
- Importance of **high availability and fault tolerance**
- Role of **health checks in automated infrastructure**
- How a single static IP can represent multiple backend servers

---

## 🚧 Challenges Faced

- Correcting `gcloud` CLI syntax issues (instance list formatting)
- Handling missing zone specification during configuration
- Understanding deprecated flags in Cloud SDK commands
- Debugging backend instance grouping and connectivity issues

---

## 🛠 Problem-Solving Approach

- Verified infrastructure using `gcloud compute instances list`
- Fixed CLI errors by correcting formatting and flags
- Referenced official Google Cloud documentation when needed
- Tested each component step-by-step before proceeding

---

## 💼 Real-World Relevance

This architecture reflects production-grade cloud systems used in:

- E-commerce platforms
- SaaS applications
- Social media platforms
- Scalable API backends

It demonstrates foundational knowledge required for:

- Cloud Engineering roles
- DevOps Engineering roles
- Backend Infrastructure Engineering

---

## 🚀 Future Improvements

- Implement Auto Scaling Groups
- Transition to modern Backend Services-based load balancing
- Explore Kubernetes (GKE) deployments
- Add CI/CD pipeline automation
- Integrate monitoring and alerting (Cloud Monitoring)

---

## 🧾 Summary

This project provided hands-on experience with deploying and managing scalable cloud infrastructure on Google Cloud. It strengthened my understanding of distributed systems, load balancing, and production-grade backend architecture design.
