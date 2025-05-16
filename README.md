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
   git clone https://github.com/Prospeerous/Kubernetes-hackathon.git
   cd Kubernetes-hackathon
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
   - Part 6:
     ```bash
      kubectl apply -f part-6/monitoring
      kubectl apply -f part-6/ingress-controller -f part-6/widgetario
      files\grafana-dashboard.json
      kubectl apply -f part-6/logging
      files\kibana-dashboard.ndjson
     ```
   - Part 7
     ```bash
     kubectl scale deploy/products-api deploy/stock-api deploy/web sts/products-db --replicas 0
      helm install widg-uat -n widg-uat --create-namespace -f files/helm/uat.yaml part-7/helm/widgetario
      kubectl get all -n widg-uat
     
      # On Windows (run as Admin)
      ./scripts/add-to-hosts.ps1 widgetario.uat 127.0.0.1
      ./scripts/add-to-hosts.ps1 api.widgetario.uat 127.0.0.1

      # OR on Linux/macOS
      ./scripts/add-to-hosts.sh widgetario.uat 127.0.0.1
      ./scripts/add-to-hosts.sh api.widgetario.uat 127.0.0.1

      curl -k https://api.widgetario.uat/products

      kubectl apply -f part-7/infrastructure
      git remote add . http://localhost:30031/kiamol/kiamol.git
      git push main

      kubectl -n infra create secret docker-registry registry-creds --docker-server=$REGISTRY_SERVER --docker-username=$REGISTRY_USER --docker-password=$REGISTRY_PASSWORD
      kubectl -n infra create configmap build-config --from-literal=REGISTRY=docker.io  --from-literal=REPOSITORY=$REGISTRY_USER

      kubectl rollout restart deploy/jenkins -n infra
     
      # On Windows (run as Admin)
      ./scripts/add-to-hosts.ps1 widgetario.smoke 127.0.0.1
      ./scripts/add-to-hosts.ps1 api.widgetario.smoke 127.0.0.1
      
      # OR on Linux/macOS
      ./scripts/add-to-hosts.sh widgetario.smoke 127.0.0.1
      ./scripts/add-to-hosts.sh api.widgetario.smoke 127.0.0.1

      curl -k https://api.widgetario.smoke/products ## test app at http://widgetario.smoke
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

 **Screenshots:**
   Here are screenshots of the various sections we took from our hackathon exercise,you can access them at **Kubernetes-lab Images** folder.

---

## 🔐 Repository Access

- ✅ This repository is **public**
- If you face access issues, please contact me directly or use the GitHub username: `(https://github.com/Prospeerous/Kubernetes-hackathon/tree/main)`

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

