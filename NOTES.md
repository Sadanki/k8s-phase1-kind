
---

# 📘 Kubernetes Phase 1 – Full Learning Notes & Cheat Sheet

This project introduces the core Kubernetes concepts using an Nginx application. It helps you learn real-world configuration using:

✅ Pods
✅ Deployments
✅ Services
✅ Namespaces
✅ ConfigMaps
✅ Secrets
✅ Custom HTML via Volume Mount
✅ BusyBox + Env Vars

---

## 📁 Project Files & Their Purpose

| File                  | Purpose                                                                  |
| --------------------- | ------------------------------------------------------------------------ |
| `deployment.yaml`     | Deploys the Nginx container with 3 replicas                              |
| `service.yaml`        | Exposes the Nginx pods using NodePort                                    |
| `env-deployment.yaml` | Deploys BusyBox container using environment variables from config+secret |
| `index.html`          | Custom HTML page mounted into Nginx pod using ConfigMap                  |
| `README.md`           | Project guide                                                            |
| `NOTES.md`            | Beginner-level explanations and commands                                 |
| `screenshot.png`      | Output screenshot (optional)                                             |

---

## 🔹 Kubernetes Concepts in the Project

### 1️⃣ **Deployment**

* A `Deployment` ensures that the desired number of Pods are always running.
* You used it to:

  * Deploy `nginx` with 3 replicas
  * Deploy `busybox` with injected environment variables

🧠 In `deployment.yaml`:

```yaml
replicas: 3       # Run 3 instances of nginx
image: nginx      # Use the nginx container image
```

---

### 2️⃣ **Service**

* A `Service` exposes a set of Pods.
* You used a `NodePort` service so it’s accessible from outside Minikube.

🧠 In `service.yaml`:

```yaml
type: NodePort       # Exposes the service on a static port
targetPort: 80       # Port inside the pod
port: 80             # Internal cluster port
```

Use this command to open in browser:

```bash
minikube service hello-service
```

---

### 3️⃣ **ConfigMap**

* Stores **non-sensitive** data like welcome messages, app titles, etc.
* Injected into containers as environment variables or mounted as files.

🧠 Used in `env-deployment.yaml`:

```yaml
env:
  - name: WELCOME_MSG
    valueFrom:
      configMapKeyRef:
        name: app-config
        key: WELCOME_MSG
```

📦 Create with:

```bash
kubectl create configmap app-config --from-literal=WELCOME_MSG="Hello"
```

---

### 4️⃣ **Secret**

* Stores **sensitive** data (e.g., passwords).
* Injected like ConfigMaps but encoded.

🧠 In `env-deployment.yaml`:

```yaml
- name: DB_PASSWORD
  valueFrom:
    secretKeyRef:
      name: app-secret
      key: DB_PASSWORD
```

📦 Create with:

```bash
kubectl create secret generic app-secret --from-literal=DB_PASSWORD="mypassword"
```

---

### 5️⃣ **Environment Variables Injection**

You used a `busybox` pod that runs:

```bash
sh -c "echo Welcome: $WELCOME_MSG && echo DB Pass: $DB_PASSWORD && sleep 3600"
```

This demonstrates:

* How to inject external values into containers
* How ConfigMaps & Secrets integrate with deployments

---

### 6️⃣ **Volume Mount (index.html)**

* Your `index.html` is mounted into the Nginx container to replace the default page.

```yaml
volumeMounts:
  - name: html
    mountPath: /usr/share/nginx/html/index.html
    subPath: index.html
volumes:
  - name: html
    configMap:
      name: nginx-html
```

📦 Create the ConfigMap:

```bash
kubectl create configmap nginx-html --from-file=index.html
```

---

### 7️⃣ **Namespace: `demo`**

* Kubernetes lets you isolate resources in namespaces like `demo` and `default`.
* In `env-deployment.yaml`, you used:

```yaml
namespace: demo
```

📦 Create namespace:

```bash
kubectl create namespace demo
```

Apply YAML to namespace:

```bash
kubectl apply -f env-deployment.yaml -n demo
```

---

### 8️⃣ **kubectl Commands Used**

```bash
kubectl apply -f deployment.yaml       # Apply Nginx deployment
kubectl apply -f service.yaml          # Expose the Nginx service
kubectl apply -f env-deployment.yaml   # Deploy BusyBox with env vars
kubectl get pods                       # View running pods
kubectl logs <pod-name>                # View pod logs
kubectl get svc                        # View services
kubectl delete -f deployment.yaml      # Clean up deployment
kubectl delete -f service.yaml         # Clean up service
```

---

## 🧠 Summary of What You Learned in Phase 1

✅ Deploying containers to Kubernetes
✅ Making your app accessible using NodePort
✅ Injecting environment variables using ConfigMap and Secret
✅ Mounting files like `index.html` via ConfigMap
✅ Working in multiple namespaces
✅ Viewing pod logs to verify output
✅ Using busybox to simulate real apps
✅ Using `kubectl` to manage your cluster

---
