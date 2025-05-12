
# DevOps Training Homework - Flux v2 and MongoDB Deployment

## Part 1: Install Flux CLI

Open PowerShell and install the Flux CLI using Chocolatey:

```powershell
choco install flux
```

## Part 2: Bootstrap Flux with GitHub

1. Generate a new fine-grained personal access token (GitHub):
   - **Administration**: Read-only
   - **Contents**: Read and write
   - **Metadata**: Read-only

> ⚠️ **Note**: For security reasons, never share your personal access token publicly.

2. Run the following command to bootstrap your GitHub repository with Flux:

```powershell
flux bootstrap github `
  --token-auth `
  --owner=Nguyen-Son-Tung `
  --repository=devops-traning `
  --branch=main `
  --path=clusters/devops-traning `
  --personal
```

## Part 3: Clone Repository

Use GitHub Desktop (or your preferred Git client) to clone the repository to your local machine.

## Part 4: Verify Flux System

Check the status of the Flux system components:

```bash
kubectl get pods -n flux-system
kubectl get kustomizations -n flux-system
```

## Part 5: Deploy MongoDB Using Flux v2 and Helm Charts

### Step 1: Prepare Infrastructure Directory

Inside your repository path (`clusters/devops-traning`), create a new folder named `infras` to store infrastructure-related manifests.

### Step 2: Define Helm Resources

Follow the official Flux Helm guide: [https://fluxcd.io/flux/guides/helmreleases/](https://fluxcd.io/flux/guides/helmreleases/)

- First, create a `HelmRepository` manifest to reference the external Helm chart repository.
- Then, define a `HelmRelease` manifest with proper configuration, including:
  - Target namespace (e.g., `mongodb`)
  - Chart name and version
  - Values for configuration overrides

### Step 3: Commit and Push

After defining the required manifests, commit your changes and push them to the remote GitHub repository. Flux will automatically reconcile and deploy the resources.
