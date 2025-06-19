
---

### 📄 `README.md` for `k8s-phase1-complete`

```markdown
# ☸️ Kubernetes Phase 1 – Hello World App with ConfigMap, Secret, and HTML Override

This project is a beginner-friendly Kubernetes deployment that covers the **foundational building blocks of K8s**:

✅ Pods, ✅ Deployments, ✅ Services, ✅ Namespaces, ✅ ConfigMaps, ✅ Secrets, ✅ Environment Variables, ✅ HTML Override using ConfigMap

---

## 📚 What You'll Learn

This repository is built to help **new Kubernetes learners** understand and practice:

1. 🔧 How to deploy applications using `Deployment`
2. 🌐 How to expose your app with a `Service` (NodePort)
3. 🧪 How to create and switch between `Namespaces`
4. 🔐 How to store sensitive and non-sensitive data using `Secrets` and `ConfigMaps`
5. 🧬 How to inject configuration into pods using `env` variables
6. 🖥️ How to override the default Nginx `index.html` using a `ConfigMap`

---

## 📁 Folder Structure

```

k8s-phase1-complete/
├── deployment.yaml          # Basic Nginx deployment
├── service.yaml             # NodePort service to expose Nginx
├── env-deployment.yaml      # BusyBox app with ConfigMap & Secret
├── index.html               # Custom HTML for Nginx welcome page
├── README.md                # Project documentation (this file)

````

---

## ⚙️ Prerequisites

Make sure you have the following installed:

- [Minikube](https://minikube.sigs.k8s.io/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

---

## 🚀 How to Run This Project

### 🟢 Step 1: Start Minikube

```bash
minikube start
````

---

### 📦 Step 2: Create ConfigMap for HTML Page

```bash
kubectl create configmap nginx-html --from-file=index.html -n default
```

> This mounts your custom `index.html` into the Nginx container to replace the default welcome page.

---

### 🧱 Step 3: Deploy Nginx App with Custom HTML

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

---

### 🌐 Step 4: Access the Application

```bash
minikube service hello-service
```

> This will open your browser with a **styled Kubernetes-themed HTML page**!

---

## 🔐 Step 5: Create ConfigMap & Secret for Environment Demo

```bash
# ConfigMap
kubectl create configmap app-config --from-literal=WELCOME_MSG="Hello from default" -n default

# Secret
kubectl create secret generic app-secret --from-literal=DB_PASSWORD="DefaultSecret123" -n default
```

---

## 🧪 Step 6: Deploy BusyBox App with Environment Variables

```bash
kubectl apply -f env-deployment.yaml
```

Check the logs to verify the env variables are injected correctly:

```bash
kubectl get pods -n default -l app=env-demo
kubectl logs <pod-name> -n default
```

Expected output:

```
Welcome: Hello from default
DB Pass: DefaultSecret123
```

---

## 🧼 Cleanup Resources

```bash
kubectl delete -f deployment.yaml
kubectl delete -f service.yaml
kubectl delete -f env-deployment.yaml
kubectl delete configmap app-config -n default
kubectl delete secret app-secret -n default
kubectl delete configmap nginx-html -n default
```

---

## 🧠 Concepts Covered

| Concept        | Description                                                |
| -------------- | ---------------------------------------------------------- |
| `Deployment`   | Defines desired app state (like replicas, image, etc.)     |
| `Service`      | Exposes your app for external access                       |
| `NodePort`     | Opens a specific port on the node IP                       |
| `ConfigMap`    | Stores non-sensitive configuration (e.g., welcome message) |
| `Secret`       | Stores sensitive info (e.g., passwords)                    |
| `Namespace`    | Isolates environments (e.g., `default`, `demo`)            |
| `VolumeMount`  | Mounts config data inside a container                      |
| `kubectl logs` | Used to verify app output and env variables                |

---

## 🙌 Author

**Vignesh Sadanki**
📬 [GitHub Profile](https://github.com/Sadanki)

---

## 🎯 Recommended Next Steps

After mastering this phase, move on to:

* 🔍 Liveness & Readiness Probes
* 🗂️ Volume mounts (Persistent Volumes)
* 🚦 Rolling Updates & Rollbacks
* ⚖️ Horizontal Pod Autoscaler (HPA)
* 🌐 Ingress Controller
* 📦 Helm Charts
* 🔁 GitOps with Argo CD

---

**Happy K8s-ing!** 🐳☸️🚀

```

---

