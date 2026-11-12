## THIS MANUAL IS RELATED TO ARGOCD-POC TASK OF WEEK 4
## INSTRUCTIONS ARE GIVEN IN TEXT WITH ADDITIONAL VIDEO DEMO BELOW


# Argo CD Installation on k3d

## 1. Creating a Kubernetes cluster with k3d

```bash
k3d cluster delete argo
k3d cluster create argo
```

## 2. Verifying the Kubernetes cluster

```bash
kubectl cluster-info
kubectl get all -A
```

## 3. Creating a namespace for Argo CD

```bash
kubectl create namespace argocd
```

## 4. Installing Argo CD

```bash
kubectl apply -n argocd --server-side --force-conflicts -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## 5. Verifying the Argo CD installation

```bash
kubectl -n argocd get all
kubectl -n argocd get pod
```

## 6. Accessing the Argo CD web UI

Forward the Argo CD server port:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443 &
```

Open **https://localhost:8080** in your browser.

> **Note:** Your browser may display a certificate warning because Argo CD uses a self-signed certificate by default.

## 7. Retrieving the Argo CD admin password

View the initial admin secret:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o yaml
```

Decode the admin password:

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

### Login credentials

- **Username:** `admin`
- **Password:** Output of the decoded secret command above.




https://github.com/user-attachments/assets/b600db4c-9590-42e8-bfaf-8278e5200d67

