Perfect! Below are the clean and well-explained `README.md` files for **both `k8s-phase1-kind`** and **`k8s-phase2-kind`** — tailored specifically to reflect that you’re using **Kind (Kubernetes in Docker)** instead of Minikube.

---

## ✅ `k8s-phase1-kind/README.md`

````markdown
# 🚀 Kubernetes Phase 1 with Kind

Welcome to **Phase 1** of Kubernetes learning using **Kind (Kubernetes IN Docker)**.

This phase covers **Kubernetes fundamentals** including Deployments, Services, ConfigMaps, and Secrets — all tested in a Kind-based cluster.

---

## 📁 Folder Structure

```text
k8s-phase1-kind/
├── configmap.yaml            # Environment variables for the app
├── deployment.yaml           # Deployment for the Hello App
├── index.html                # Custom HTML served via NGINX
├── NOTES.md                  # Deep explanation notes
├── README.md                 # You are here
├── secret.yaml               # Inject secrets into pods
├── service.yaml              # NodePort service to expose the app
├── test-deployment.yaml      # Optional test Deployment
└── test-service.yaml         # Optional test Service
````

---

## 🧱 Prerequisites

* ✅ Docker Desktop
* ✅ [Kind installed](https://kind.sigs.k8s.io/)
* ✅ kubectl configured

---

## 🧪 How to Run (Kind Cluster)

### 1️⃣ Create Cluster

```bash
kind create cluster --name k8s-phase-demo
```

### 2️⃣ Switch to the folder

```bash
cd k8s-phase1-kind/
```

### 3️⃣ Apply all resources

```bash
kubectl apply -f .
```

### 4️⃣ Access the App

Find the NodePort (e.g., 30011) from:

```bash
kubectl get svc
```

Then access via browser:

```
http://localhost:<nodePort>
```

---

## 🧹 Cleanup

```bash
kubectl delete -f .
kind delete cluster --name k8s-phase-demo
```

---

## ✍️ Author

**Vignesh Sadanki**
📌 [GitHub Profile](https://github.com/Sadanki)

---

Happy Learning with Kind & Kubernetes! ☸️🐳

````

---
