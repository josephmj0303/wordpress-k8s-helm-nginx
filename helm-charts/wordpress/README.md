
---

# 📘 `helm-charts/wordpress/README.md`

```markdown
# WordPress Helm Chart

This Helm chart deploys WordPress and MySQL into a Kubernetes cluster
with persistent storage and ingress-based access.

---

## Components

- WordPress Deployment & Service
- MySQL Deployment & Service
- PersistentVolumeClaims
- Kubernetes Secrets
- NGINX Ingress Resource

---

## Configuration

Key values in `values.yaml`:

```yaml
wordpress:
  image: wordpress:6.9.1
  replicas: 1

mysql:
  image: mysql:8.0
  storage: 10Gi

ingress:
  enabled: true
  host: wordpress.joedevopslab.xyz

