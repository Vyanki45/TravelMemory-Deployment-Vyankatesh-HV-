# TravelMemory-Deployment-Vyankatesh-HV-
HeroVired assignment

# Project Submission: AWS Highly Available Full-Stack Deployment
**Student Name:** Vyankatesh HV
**Project Name:** TravelMemory MERN Application Scaling & Deployment

---

## 🔗 Project Deliverables
* **GitHub Repository:** https://github.com/Vyanki45/TravelMemory-Deployment-Vyankatesh-HV-
* **Live Application URL (Frontend ALB):** http://travelmemory-frontend-alb-1677502466.us-east-1.elb.amazonaws.com

---

## 🏗️ Architecture & Deployment Summary

This deployment transitions a monolithic MERN application into a production-grade, decoupled, and horizontally scaled multi-instance cluster deployed across multiple Availability Zones (AZs) within AWS.

### 1. Compute Tier & High Availability
* **Decoupled Architecture:** Completely separated the React frontend and Node.js backend layers onto dedicated EC2 web and app instances.
* **Horizontal Scaling:** Established a 4-instance cluster (2 Frontends, 2 Backends) distributed across independent AWS Availability Zones to guarantee high availability and fault tolerance.

### 2. Network Traffic Management & Load Balancing
* **Backend Tier Isolation:** Grouped backend API nodes into a dedicated target group routed through a Backend Application Load Balancer (`travelmemory-backend-alb`). 
* **Frontend Ingress:** Created a Frontend Application Load Balancer (`travelmemory-frontend-alb`) acting as the public-facing gateway to handle client requests and balance ingress traffic seamlessly across the web servers.
* **Environment Synchronization:** Updated the frontend source configuration (`src/urls.js`) on all web servers to route API requests natively through the Backend ALB DNS name, followed by clean production compilation (`npm run build`).

### 3. Phase 4: DNS & Cloudflare Routing Strategy (Documentation Note)
To transition this architecture to a custom production domain using Cloudflare, a root or subdomain CNAME record would be provisioned within the Cloudflare DNS dashboard. This CNAME record maps the custom domain directly to the public-facing Frontend Application Load Balancer DNS name (`travelmemory-frontend-alb-1677502466.us-east-1.elb.amazonaws.com`) with Cloudflare proxying enabled. 

While a traditional standalone deployment might utilize a standard A record to map an individual EC2 public IP, utilizing a CNAME pointing to the Application Load Balancer preserves the high-availability distribution and multi-AZ resilience established in the scaling phase of this project.

---

## 📁 Repository Contents
The attached GitHub repository contains:
1. The modified frontend build configurations.
2. Comprehensive deployment step documentation.
3. The infrastructure deployment diagram mapped via draw.io.
