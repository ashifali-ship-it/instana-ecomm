# Instana E-Commerce (AKS + Helm Deployment)

This project is a **multi-service e-commerce application** deployed on **Azure Kubernetes Service (AKS)** using **Helm charts**.

It includes the source code for all microservices for reference and potential local development.

## Services

| Service    | Description               |
|------------|---------------------------|
| web        | Frontend UI               |
| catalogue  | Product catalog service   |
| cart       | Shopping cart management  |
| payment    | Payment processing        |
| shipping   | Shipping service          |
| ratings    | Product ratings & reviews |
| user       | User management           |

## Prerequisites

- Azure account with AKS cluster provisioned
- `kubectl` installed and configured for your AKS cluster
- Helm 3 installed

## Deployment Instructions

### 1. Deploy Helm Charts

Deploy each service to its own namespace:

```bash
# Example: deploy the web service
helm install web AKS/helm/web -n web --create-namespace

# Deploy other services
helm install catalogue AKS/helm/catalogue -n catalogue --create-namespace
helm install cart AKS/helm/cart -n cart --create-namespace
helm install payment AKS/helm/payment -n payment --create-namespace
helm install shipping AKS/helm/shipping -n shipping --create-namespace
helm install ratings AKS/helm/ratings -n ratings --create-namespace
helm install user AKS/helm/user -n user --create-namespace
```

## 2. Verify Deployment

Check that all pods and services are running:

```bash
kubectl get pods -A
kubectl get svc -A
```

## 3. Notes

- **Environment-specific values**: Modify `AKS/helm/<service>/values.yaml` for dev, staging, or production settings.  
- **Secrets**: Store secrets using Kubernetes Secrets or Azure Key Vault; do not include them in Helm values.  
- **Ingress / Load Balancer**: Configure in `values.yaml` if public access is required.  

### Optional: Architecture Overview

[AKS Cluster]

├─ Namespace: web → Frontend UI pods and service

├─ Namespace: catalogue → Product catalog service pods and service

├─ Namespace: cart → Shopping cart service pods and service

├─ Namespace: payment → Payment processing service pods and service

├─ Namespace: shipping → Shipping service pods and service

├─ Namespace: ratings → Product ratings & reviews service pods and service

└─ Namespace: user → User management service pods and service


## Source / Acknowledgment

This project is a sample microservices application originally provided by **IBM Instana** for learning purposes.  
It has been adapted here for deployment on **Azure Kubernetes Service (AKS)** using **Helm charts**.


