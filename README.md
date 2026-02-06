# WordPress on Kubernetes using Helm & NGINX Ingress

This project demonstrates deploying a production-ready WordPress application
on a Kubernetes cluster using Helm charts and NGINX Ingress Controller.

The setup includes:
- WordPress application
- MySQL database
- Persistent storage using PVCs
- NGINX Ingress Controller
- Custom domain routing via AWS Load Balancer

---

## 🛠️ Technology Stack

- Kubernetes
- Helm 3
- NGINX Ingress Controller
- WordPress
- MySQL
- AWS (EC2, ELB, Route53 / External DNS)
- Linux (Ubuntu)

---

## 📐 Architecture Overview

![Architecture](architecture/wordpress-k8s-architecture.png)

---

## 📂 Repository Structure

```
wordpress-k8s-helm-nginx/
│
├── helm-charts/
│   └── wordpress/
│       ├── Chart.yaml
│       ├── values.yaml
│       └── templates/
│           ├── _helpers.tpl
│           ├── mysql-deployment.yaml
│           ├── mysql-pvc.yaml
│           ├── mysql-service.yaml
│           ├── wordpress-deployment.yaml
│           ├── wordpress-pvc.yaml
│           ├── wordpress-service.yaml
│           ├── wordpress-ingress.yaml
│           ├── wordpress-secret.yaml
│           └── NOTES.txt
│
├── manifests/
│   └── nginx-ingress/
│       ├── controller.yaml
│       └── rbac.yaml
│
├── screenshots/
│   ├── ingress-details.png
│   ├── wordpress-login.png
│   └── wordpress-home.png
│
├── architecture/
│   └── wordpress-k8s-architecture.png
│
├── .gitignore
└── README.md
```

