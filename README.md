```markdown
# 🚀 Kubernetes Hello World Project

This is a simple "Hello World" project to help you understand the basics of deploying an application on **Kubernetes**. It uses the official **Nginx** Docker image and exposes it via a **NodePort Service**.

---

## 📁 Project Structure

```

k8s-hello-world/
├── deployment.yaml   # Defines the Nginx Deployment
├── service.yaml      # Exposes the Deployment using NodePort
└── index.html        # Sample HTML page (optional)

````

---

## 🔧 What It Does

- Deploys an Nginx pod to your Kubernetes cluster
- Exposes it on a browser-accessible URL using NodePort
- Displays a "Hello World" page

---

## 🚀 How to Run

### 1. Start Minikube
```bash
minikube start
````

### 2. Apply Deployment and Service

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### 3. Access the App

```bash
minikube service hello-service
```

This will open your browser with the Nginx "Hello World" page.

---

## 📦 Cleanup

To delete everything:

```bash
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
```

---

## 📘 Learnings

* What is a Kubernetes Deployment?
* What is a NodePort service?
* How to use `kubectl` to deploy and manage K8s resources
* How services expose pods in a cluster

---

## 🛠 Requirements

* [Minikube](https://minikube.sigs.k8s.io/)
* [kubectl](https://kubernetes.io/docs/tasks/tools/)
* Basic terminal knowledge

---

## 🌐 Author

**Vignesh Sadanki**
📬 [GitHub Profile](https://github.com/Sadanki)

---

## 📸 Screenshot 


```markdown
![image](https://github.com/user-attachments/assets/148153bb-9370-403b-b02c-e40bff4a6738)

```

---
Happy K8s-ing! 🐳☸️🚀

```

---

```
