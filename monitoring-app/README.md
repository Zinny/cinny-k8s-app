# 🚀 Prometheus & Grafana Monitoring Setup with Argo CD

This repository contains manifests and Helm value files to deploy Prometheus and Grafana on Kubernetes using Argo CD.

---

## 📁 Repository Structure

monitoring-app/
├── prometheus/
│ └── values.yaml
├── grafana/
│ └── values.yaml
├── argo-apps/
│ ├── app-prometheus.yaml
│ └── app-grafana.yaml


---

## ⚙️ Prerequisites

- Kubernetes cluster (Minikube, EKS, GKE, etc.)
- Argo CD installed and configured
- `kubectl` installed and configured
- GitHub account (or any Git server)

---

## 🛠️ Deployment Steps

### 1. Clone this repository

```bash
git clone https://github.com/yourusername/monitoring-app.git
cd monitoring-app

---

### 2. Push your local changes (if applicable)

git add .
git commit -m "Add Prometheus and Grafana Argo CD apps"
git push origin main


### 3. Create namespaces in your cluster

kubectl create namespace monitoring
kubectl create namespace argocd

---

### 4. Deploy Argo CD Applications

You can deploy Argo CD apps either by applying YAML manifests or via the Argo CD UI.

Option A: Apply manifests using kubectl

kubectl apply -f argo-apps/app-prometheus.yaml
kubectl apply -f argo-apps/app-grafana.yaml

Option B: Create applications via Argo CD UI
Login to Argo CD UI (port-forward if needed):

kubectl port-forward svc/argocd-server -n argocd 8080:443
Open https://localhost:8080 and login with admin credentials.

Create new apps pointing to the repository URL and the paths:

prometheus

grafana

Set sync policy to automatic for auto deployment.

---

🔧 Helm Values (customize if needed)
prometheus/values.yaml

alertmanager:
  enabled: false
pushgateway:
  enabled: false
server:
  persistentVolume:
    enabled: false
grafana/values.yaml


persistence:
  enabled: false
adminUser: admin
adminPassword: admin

---

🚀 Accessing Services
Prometheus and Grafana are deployed in the monitoring namespace.

Use port forwarding or configure an ingress to access Grafana dashboards.

Example port forward Grafana:

kubectl -n monitoring port-forward svc/grafana 3000:80
Open http://localhost:3000 in your browser.

Maintained by 👩‍💻 Cinny
