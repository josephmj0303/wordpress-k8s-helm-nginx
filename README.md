# WordPress on Kubernetes using Helm & NGINX Ingress
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![Helm 3](https://img.shields.io/badge/Helm%203-0F1689?style=for-the-badge&logo=helm&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-Ingress-009639?style=for-the-badge&logo=nginx&logoColor=white)
![WordPress](https://img.shields.io/badge/WordPress-21759B?style=for-the-badge&logo=wordpress&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)

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
│       ├── README.md
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
├── infrastructure/
│   └── nginx-ingress/
│       ├── README.md
│       └── install.sh   
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

---

## 🚀 Deployment Steps

1. Deploy NGINX Ingress Controller
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.3/deploy/static/provider/aws/deploy.yaml
```
Verify:
```
kubectl get pods -n ingress-nginx
kubectl get svc -n ingress-nginx
```
2. Install WordPress using Helm
```
helm install wp helm-charts/wordpress -n wp-ns --create-namespace
```
3. Verify Resources
```
kubectl get all -n wp-ns
kubectl get ingress -n wp-ns
```
🌐 Access Application
```
http://wordpress.joedevopslab.xyz
```

Admin:
```
http://wordpress.joedevopslab.xyz/wp-admin
```

---

## 📸 Screenshots
```
| Description     | Image                               |
| --------------- | ----------------------------------- |
| Ingress Details | screenshots/ingress-details.png     |
| WordPress Home  | screenshots/wordpress-home.png      |
| Login Page      | screenshots/wordpress-login.png     |

```

---

## 🔒 Security Considerations

- WordPress and MySQL credentials are stored as Kubernetes Secrets
  and injected into pods via environment variables.

- Database data and WordPress content are stored using PersistentVolumeClaims,
  preventing data loss during pod restarts.

- Application is exposed externally through NGINX Ingress Controller
  with controlled host-based routing.

- HTTPS is not currently enabled. TLS can be implemented using
  cert-manager and Let’s Encrypt for production deployments.

- For production environments, it is recommended to:
  - Enable TLS termination
  - Restrict database access using NetworkPolicies
  - Rotate credentials periodically

---

## 🧠 Use Cases

1️⃣ Real-World Application Deployment

- Deploys a stateful production-like WordPress application using Kubernetes primitives.

2️⃣ Helm Chart Authoring

- Parameterized deployments using values.yaml

- Reusable Helm templates

- Secrets management via Kubernetes Secrets

3️⃣ Kubernetes Ingress & Load Balancing

- NGINX Ingress Controller

- AWS ELB integration

- Host-based routing using custom domain

4️⃣ Persistent Storage Management

- PVCs for WordPress content and MySQL data

- Demonstrates stateful workloads in Kubernetes

5️⃣ Cloud-Native DevOps Skills

- AWS infrastructure awareness

- DNS mapping

- Production troubleshooting (helm lint, ingress debugging)

---

## 🔄 Future Enhancements

- HTTPS with cert-manager & Let’s Encrypt

- CI/CD using GitHub Actions

- Horizontal Pod Autoscaler

- External MySQL (RDS)

- Monitoring with Prometheus & Grafana

