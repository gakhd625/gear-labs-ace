# 🌐 Application Load Balancer Deployment on Google Cloud

## 📌 Project Overview

This project demonstrates the deployment and configuration of a **Layer 7 Application Load Balancer (L7)** using Google Cloud Compute Engine. Unlike Layer 4, this load balancer understands HTTP(S) traffic and can make smarter routing decisions.

The system distributes incoming web traffic across multiple backend virtual machines to ensure:

- High availability ✅  
- Scalability 📈  
- Fault tolerance 🛡️  

This was implemented through a hands-on lab to understand modern cloud architecture design.

---

## 🏗️ Architecture Summary

The system consists of:

- **Compute Engine VMs (Manual Setup)**: `www1`, `www2`, `www3`
- **Instance Template**: `lb-backend-template` (server blueprint)
- **Managed Instance Group (MIG)**: `lb-backend-group` (2 instances)
- **Web Server**: Apache HTTP Server
- **Health Check**: HTTP-based monitoring
- **Backend Service**: Connects instance group to load balancer
- **URL Map**: Routes incoming requests
- **Target HTTP Proxy**: Handles HTTP traffic
- **Global Static IP**: Public entry point
- **Forwarding Rule**: Routes traffic to proxy on port 80

---

## 🔄 System Flow

```text
Client Request
    ↓
Global Static IP (Load Balancer Entry Point)
    ↓
Forwarding Rule (Port 80)
    ↓
Target HTTP Proxy
    ↓
URL Map (Routing Rules)
    ↓
Backend Service
    ↓
Managed Instance Group (2 VMs)
    ↓
Healthy Backend Instances
```
## ⚙️ Key Implementations

### 1. Virtual Machine Deployment (Manual)
- Created 3 VMs (www1–www3) for testing  
- Installed Apache using startup scripts  
- Each VM serves a unique webpage  

### 2. Instance Template
- Defined a reusable VM configuration  
- Includes:  
  - Debian 11 OS  
  - Apache installation  
  - Startup automation  
- Acts as a blueprint for backend servers  

### 3. Managed Instance Group (MIG)
- Created a group of 2 identical VMs  
- Automatically managed by Google Cloud  

**Features:**
- Auto-healing  
- Consistent configuration  
- Scalability support  

### 4. Application Load Balancer
- Configured an L7 HTTP Load Balancer  
- Routes traffic intelligently based on requests  
- Uses Google’s global infrastructure  

### 5. Health Checks
- Configured HTTP health checks  
- Ensures only healthy instances receive traffic  
- Automatically removes unhealthy VMs  

### 6. Traffic Routing Components
- **Backend Service**: Defines where traffic goes  
- **URL Map**: Determines routing rules  
- **Target Proxy**: Receives and forwards requests  
- **Forwarding Rule**: Connects public IP to system  


## 🧮 Total Infrastructure

| Resource Type              | Count |
|---------------------------|------:|
| Manual VMs (www1–www3)    | 3     |
| MIG Instances             | 2     |
| **Total VMs Created**     | 5     |


## ⚠️ Note
- Only the 2 MIG instances are used by the load balancer  
- The 3 manual VMs are for demonstration and learning  


## 🍔 Analogy: Smart Restaurant System

### Step 1: Practice Setup
You first created 3 cooks:
- www1, www2, www3  
👉 To understand how serving works  

### Step 2: Recipe (Template)
You wrote a perfect recipe:  
👉 This ensures every cook makes the same food  

### Step 3: Professional Team (MIG)
You hired 2 trained cooks using that recipe:  
👉 They work consistently and can be replaced if needed  

### Step 4: Manager (Load Balancer)
You added a manager:  
👉 “Send customers to whichever cook is available and working.”  

**Result:**
- Faster service ⚡  
- No single point of failure 🛡️  
- Smooth operation even if one cook fails  


## 🧠 Key Learnings
- Difference between Layer 4 vs Layer 7 load balancing  
- Importance of instance templates for consistency  
- Benefits of Managed Instance Groups  
- Role of health checks in reliability  
- How cloud systems separate responsibilities into components  


## 🚧 Challenges Faced
- Understanding the difference between:  
  - Templates vs Instances  
  - MIG vs manual VMs  
- Keeping track of multiple components in L7 setup  
- Debugging connectivity and health check issues  
- Learning the flow of traffic across components  


## 🛠 Problem-Solving Approach
- Broke down each command step-by-step  
- Verified resources using `gcloud` commands  
- Tested endpoints using `curl` and browser  
- Focused on understanding architecture, not just commands  


## 💼 Real-World Relevance

This architecture is similar to systems used in:
- Web applications (e.g., SaaS platforms)  
- Scalable APIs  
- E-commerce systems  
- Global web services  

**Skills demonstrated:**
- Cloud infrastructure design  
- Load balancing concepts  
- Distributed system thinking  
- CLI-based cloud management  


## 🚀 Future Improvements
- Enable autoscaling in MIG  
- Add HTTPS (SSL/TLS)  
- Implement path-based routing  
- Integrate monitoring and logging  
- Deploy using Infrastructure as Code (Terraform)  


## 🧾 Summary

This project demonstrated how to move from a single-server setup to a scalable, load-balanced architecture.

**Key takeaway:**
Modern applications don’t rely on one server
they rely on multiple coordinated systems working together.
