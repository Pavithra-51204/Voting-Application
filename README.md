# CI/CD Pipeline Implementation for Voting Application

## Overview
This project demonstrates the deployment of a **Voting Application** using a **CI/CD pipeline** built with **Azure Pipelines, Docker, Kubernetes, and Argo CD**. The implementation ensures high availability, automated deployments, and efficient resource utilization.

## Tech Stack
- **Azure Pipelines** - CI/CD automation
- **Docker** - Containerization of application services
- **Kubernetes (AKS)** - Orchestration and deployment
- **Argo CD** - GitOps-based continuous deployment

## Architecture
The application consists of the following microservices:
1. **Vote Service** - Frontend (React/Angular)
2. **Result Service** - Backend (Node.js/Python)
3. **Worker Service** - Background worker (Redis-based processing)

## CI/CD Workflow
### **Continuous Integration (CI)**
1. **Code Commit:** Developers push code to GitHub/ Azure Repos.
2. **Build Process:** Azure Pipelines triggers:
   - Linting & Unit Tests
   - Docker Image Build
   - Push to Container Registry (ACR/DockerHub)

### **Continuous Deployment (CD)**
3. **Kubernetes Deployment:**
   - Argo CD syncs the latest image from the registry.
   - Updates the Kubernetes cluster (AKS) with the new deployment.

## Prerequisites
- Azure DevOps account
- Kubernetes cluster (AKS)
- Argo CD installed and configured
- Docker installed and configured

## Deployment Steps
1. **Clone the Repository:**
   ```sh
   git clone <repo-url>
   cd voting-app
   ```
2. **Build and Push Docker Images:**
   ```sh
   docker build -t <container-registry>/vote-app:latest .
   docker push <container-registry>/vote-app:latest
   ```
3. **Apply Kubernetes Manifests:**
   ```sh
   kubectl apply -f k8s/
   ```
4. **Set Up Argo CD Sync:**
   ```sh
   argocd app sync voting-app
   ```

## Monitoring & Logging
- **Azure Monitor** - Logs & Metrics
- **kubectl logs -f <pod-name>** - Real-time logs
- **Argo CD Dashboard** - Deployment status visualization

## Future Enhancements
- Implement **Helm charts** for better Kubernetes management
- Add **Prometheus & Grafana** for monitoring
- Improve security with **RBAC & Network Policies**

## Conclusion
This CI/CD pipeline ensures seamless, automated deployment of the voting application, optimizing resource usage and maintaining high availability through containerization and GitOps practices.


