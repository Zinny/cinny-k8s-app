# Cinny K8s App

This is a simple Kubernetes app deployed via **Argo CD** on **Minikube** using GitOps workflow.

## 🚀 Deployment Overview

- **Platform:** Minikube (local Kubernetes cluster)
- **CD Tool:** Argo CD
- **Repo Path:** `k8s/` folder contains Kubernetes manifests (`Deployment`, `Service`, `Ingress`)
- **Branch:** `master` (default)
- **Sync:** Argo CD monitors the Git repo and auto-syncs deployments

## 🧱 Folder Structure

\`\`\`
Cinny-k8s-app/
├── k8s/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
└── README.md
\`\`\`

## ⚙️ Accessing the App

### ➤ Option 1: Via NodePort

If using a `NodePort` service:

\`\`\`bash
minikube service cinny-k8s-app -n default
\`\`\`

This opens the app in your default browser.

### ➤ Option 2: Via Ingress (e.g., http://cinny.local)

1. Make sure Ingress is enabled:

\`\`\`bash
minikube addons enable ingress
\`\`\`

2. Add entry to \`/etc/hosts\`:

\`\`\`txt
<minikube-ip>   cinny.local
\`\`\`

(Find IP using \`minikube ip\`)

3. Visit: [http://cinny.local](http://cinny.local)

## ✅ Current Status

- ✅ App deployed and synced via Argo CD
- ✅ GitHub default branch set to \`master\`
- ✅ Working pod confirmed via \`kubectl get pods\`

---

Made with 💻 by Cinny 🚀
EOF
