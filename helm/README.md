## Helm App Deployment with Argo CD UI

This guide explains how to deploy a Helm-based Kubernetes application manually and through Argo CD using its web UI.

---

### 📁 Folder Structure

cinny-k8s-app/
└── helm/ # Helm chart created using helm create . inside this folder

yaml
Copy
Edit

---

### 🧰 Prerequisites

- Kubernetes Cluster (e.g., Minikube)
- Helm v3+
- kubectl
- Argo CD installed and UI accessible
- Your GitHub repo (e.g., https://github.com/<your-username>/cinny-k8s-app)

---

### 🛠️ Step 1: Install Helm and Deploy Locally (Optional)

#### Install Helm (Ubuntu)

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
Deploy the app manually using Helm
bash
Copy
Edit
cd helm
helm install cinny-release .
Verify the deployment:

bash
Copy
Edit
helm list
kubectl get pods
kubectl get svc
🚀 Step 2: Deploy Helm App using Argo CD UI
1. Log in to Argo CD UI
Access the Argo CD web interface, usually at:

cpp
Copy
Edit
https://localhost:8080 (via port-forward)
or
http://<node-ip>:<node-port> (if exposed via NodePort)
2. Create a New Application
Click + NEW APP

Fill out the form as follows:

Field	Value
Application Name	cinny-helm-app
Project	default
Sync Policy	Manual or Auto as preferred
Repository URL	https://github.com/<your-username>/cinny-k8s-app.git
Revision	main
Path	helm
Cluster URL	https://kubernetes.default.svc (for in-cluster)
Namespace	default or any namespace you wish to deploy to

3. Click Create
Argo CD will fetch your chart and show the status.

🔄 Step 3: Sync Application from UI
After the app is created:

Click on the app tile (e.g., cinny-helm-app)

Click SYNC to apply the Helm chart into the cluster

You can also set Auto-Sync if desired

🧹 To Delete the Helm App
From CLI (manual install):

bash
Copy
Edit
helm uninstall cinny-release
From Argo CD:

Go to the Argo CD UI

Click the three dots (⋮) on the application tile

Click Delete

🔍 Tips
Use values.yaml inside your chart to configure your app

To override values via Argo CD, use Helm Parameters under the Helm section of the App form

Your repo must be public or accessible by Argo CD

🛠 Maintained by: Cinny 🚀
EOF
