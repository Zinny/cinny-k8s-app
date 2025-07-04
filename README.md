
## 🚀 Minikube Installation Guide (Ubuntu 24.04)

This guide walks you through installing Minikube on Ubuntu 24.04 and setting up a local Kubernetes cluster, including the dashboard and Argo CD.

---

### 📝 Prerequisites

- 🖥️ Ubuntu 24.04 LTS (or similar)  
- 💾 Minimum 2GB free memory  
- 📦 Minimum 20GB disk space  
- 🌐 Internet connection  
- 🛠️ Virtualization enabled (VirtualBox or KVM)  

---

### ⚙️ Step 1: Install Dependencies


sudo apt update -y

---

### 📥 Step 2: Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client

---

### 📦 Step 3: Install Minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube version

---

### ▶️ Step 4: Start Minikube
Option 1: Start with Docker (recommended if Docker is installed)

minikube start --driver=docker
Option 2: Start with VirtualBox

minikube start --driver=virtualbox
💡 Tip: Run minikube drivers to see available drivers on your system.

---

### 🔍 Step 5: Verify Installation
kubectl get nodes
You should see a running node named minikube.

----

🌐 Step 6: Access Minikube Dashboard
minikube dashboard
This will open the Kubernetes dashboard in your default browser.

---

### 🚩 Step 7: Deploy Argo CD on Minikube
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


---

### 🚪 Step 8: Access Argo CD UI
kubectl port-forward svc/argocd-server -n argocd 8080:443
Open your browser and visit:
https://localhost:8080

---

### 🔑 Step 9: Login to Argo CD
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
Username: admin

Password: (from above command)

🛠️ Useful Commands
Stop cluster:

minikube stop
Delete cluster:

minikube delete
SSH into VM:

minikube ssh
Get cluster info:

kubectl cluster-info
View services:

minikube service list

---

### 🧹 Cleanup (if needed)
minikube stop
minikube delete
Maintained by: 👩‍💻 Cinny
