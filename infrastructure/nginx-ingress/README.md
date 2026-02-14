# NGINX Ingress Controller Installation

This project uses the official NGINX Ingress Controller static manifest
for AWS environments.

Version: controller-v1.1.3

---

## Install Controller

kubectl apply -f \
https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.1.3/deploy/static/provider/aws/deploy.yaml

---

## What This Manifest Creates

- Namespace: ingress-nginx
- ServiceAccount
- RBAC (ClusterRole, ClusterRoleBinding)
- Deployment (nginx-ingress-controller)
- Service (Type: LoadBalancer)
- Admission Webhooks

---

## Verify Installation

kubectl get pods -n ingress-nginx
kubectl get svc -n ingress-nginx

