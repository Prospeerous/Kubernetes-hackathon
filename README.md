# 🚀 Widgetario Kubernetes Hackathon Project

Welcome to our Hackathon submission! This project showcases a complete Kubernetes deployment of the **Widgetario** application, a fictional company selling gadgets. The app is containerized, configured, and deployed across multiple parts, each focusing on critical Kubernetes skills.

---


## 📖 Project Overview

**Widgetario** is a full-stack microservices application composed of:

- A PostgreSQL database (`products-db`)
- Backend APIs (`products-api` and `stock-api`)
- A frontend web application (`web`)

This project involves:

- Writing and applying Kubernetes manifests
- Using ConfigMaps and Secrets
- Setting up persistent volumes and caching
- Deploying stateful applications
- Managing DNS with Ingress controllers
- Applying security best practices for production

---

## ⚙️ Installation Instructions

To run this project on your local Kubernetes setup (e.g., Minikube or Docker Desktop):

1. **Clone the repository**  
   ```bash
   git clone https://github.com/your-username/widgetario-k8s-hackathon.git
   cd widgetario-k8s-hackathon
   ```

2. **Start your Kubernetes cluster**

3. **Apply manifests step-by-step:**
   - Part 1:
     ```bash
     kubectl apply -f hackathon/part-1/
     ```
   - Part 2:
     ```bash
     kubectl apply -f hackathon/part-2/
     ```
   - Part 3:
     ```bash
     kubectl delete deploy products-db
     kubectl delete svc products-db
     kubectl delete pvc -l app=products-db
     kubectl apply -f hackathon/part-3/
     kubectl rollout restart deploy/products-api deploy/stock-api
     ```
   - Part 4:
     ```bash
     kubectl apply -f hackathon/part-4/
     ./scripts/add-to-hosts.sh widgetario.local 127.0.0.1
     ./scripts/add-to-hosts.sh api.widgetario.local 127.0.0.1
     ```
   - Part 5:
     ```bash
     kubectl apply -f hackathon/part-5/
     ```

---

## 📦 Dependencies

- Kubernetes 1.21+
- Kubectl
- Minikube / Docker Desktop (or any local K8s cluster)
- Ingress Controller (NGINX recommended)
- Docker

---

## 🧪 Testing Instructions

Basic test cases to validate functionality are in the `solutions/` folder.

To test:

- Access the frontend at `http://widgetario.local`
- Check API at `http://api.widgetario.local/products`
- Inspect pod health with:
  ```bash
  kubectl get pods
  kubectl logs <pod-name>
  kubectl describe pod <pod-name>
  ```

---

## 📄 Code Documentation

The YAML files are well-commented to explain:

- Resource kinds and configurations
- Environment variables and secret mappings
- Persistent volume mounts
- Ingress rules
- Probes and security settings

Consistent naming conventions have been applied throughout for clarity.

---

## ☁️ Deployment Instructions

For cloud deployment (e.g., on GKE, AKS, EKS):

- Replace local hostnames with a real domain
- Use a cloud Ingress Controller and managed SSL (e.g., Let’s Encrypt)
- Apply manifests in order using CI/CD or manual steps
- Provision cloud storage volumes where needed
- Secure secrets with cloud-native tools (e.g., GCP Secret Manager)

---

## 📷 Media 

> **Screenshots:**

| Widgetario Architecture | Working App UI |
|-------------------------|----------------|
| ![](img/widgetario-architecture.png) | ![](img/widgetario-solution-2.png) |

---

## 🔐 Repository Access

- ✅ This repository is **public**
- If you face access issues, please contact me directly or use the GitHub username: `your-username`

---

## 🧠 Learnings & Reflections

This project deepened our understanding of:

- Kubernetes resource modeling
- Real-world app deployment strategies
- Debugging and troubleshooting live environments
- Secure handling of configuration and secrets
- Transitioning from development to production specs

---

## 🙌 Acknowledgments

Special thanks to the Widgetario hackathon materials that guided this comprehensive hands-on experience.

---

