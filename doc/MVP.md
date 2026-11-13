## THIS MANUAL IS RELATED TO ARGOCD-MVP TASK OF WEEK 4
## INSTRUCTIONS ARE GIVEN IN TEXT WITH ADDITIONAL VIDEO DEMO BELOW


## Deploying and Testing an Application with Argo CD

### 1. Connecting to Argo CD

- Open the Argo CD web UI at `https://localhost:8080`.
- Log in using the `admin` account and the initial admin password.

### 2. Creating a New Application

- Click **New App** in the Argo CD UI.
- Configure the required application parameters:
  - **Application Name:** `asciiartify`
  - **Project:** `default`
  - **Sync Policy:** `Automatic`
  - **Repository URL:** GitHub repository containing the Helm chart
  - **Revision:** `HEAD`
  - **Path:** `helm`
  - **Cluster URL:** `https://kubernetes.default.svc`
  - **Namespace:** `asciiartify`
- Click **Create**.

### 3. Verifying Application Deployment

- Confirm that the application appears in the Argo CD dashboard.
- Verify that the application reaches **Synced** and **Healthy** status.
- Check that the Kubernetes resources have been deployed:

```bash
kubectl -n asciiartify get all
kubectl -n asciiartify get pods
```

### 4. Verifying Application Functionality

- Access the application through its configured endpoint.
- Confirm that the application is accessible and functioning correctly.

### 5. Testing Automatic Synchronization

- Open the application's Helm configuration in the GitHub repository.
- Modify a parameter
- Commit and push the change to GitHub.

### 6. Observing Argo CD Auto-Sync

- Open the application in the Argo CD dashboard.
- Observe Argo CD detecting the change in the Git repository.
- Confirm that Argo CD automatically synchronizes the application without manual intervention.
- Verify that the application returns to **Synced** and **Healthy** status.

### 7. Verifying Changes in Kubernetes

Check that the updated configuration was applied.

### 8. Verifying Application Functionality After Synchronization

- Access the application again.
- Confirm that it remains accessible and functions correctly after the configuration change.




https://github.com/user-attachments/assets/05fcfdf1-cca4-4794-a401-46b326d9e5c2

