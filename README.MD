# Setup Application Default Credentials (ADC) in GKE

This guide walks you through enabling **Workload Identity Federation** in Google Kubernetes Engine (GKE) to allow your Kubernetes workloads to authenticate with Google Cloud APIs securely and without using service account keys.

---

## ✅ Prerequisites

- Existing GKE cluster
- IAM permissions to modify clusters and node pools
- `gcloud` CLI installed and authenticated
- `kubectl` configured to access your cluster

---

## ⚙️ Enable Workload Identity Federation for an Existing GKE Cluster

1. Open the [Google Kubernetes Engine page](https://console.cloud.google.com/kubernetes/list).
2. Click the name of the cluster you want to modify.
3. In the **Security** section, click **Edit** next to _Workload Identity Federation for GKE_.
4. In the dialog, select the checkbox **Enable Workload Identity**.
5. Click **Save Changes**.

📖 [Reference Documentation](https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity?cloudshell=true#console_1)

---

## 🔁 Modify an Existing Node Pool to Use Workload Identity

1. Go to the [Google Kubernetes Engine page](https://console.cloud.google.com/kubernetes/list).
2. Click the name of the cluster to modify.
3. Go to the **Nodes** tab.
4. Under **Node Pools**, click the name of the node pool you want to update.
5. Click **Edit**.
6. In the **Security** section, check **Enable GKE Metadata Server**.
7. Click **Save**.

📖 [Reference Documentation](https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity?cloudshell=true#console_1)

---

## 🔐 Configure Kubernetes Service Account to Use Workload Identity

### 1. Create a Kubernetes Service Account (KSA)

```bash
kubectl create serviceaccount secretmanagersa -n syndication
