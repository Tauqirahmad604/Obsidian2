
## Docker Build and Push to Artifact Registry Workflow

### Overview

This pipeline automates the process of building a Docker image, pushing it to Google Cloud Artifact Registry (GAR), and deploying the image to two different servers via SSH. It ensures consistent image updates and deployments in a seamless manner.

### Key Features

1. **Automated Docker Image Build and Push**: Builds and pushes the Docker image to the Google Artifact Registry for the `docker-branch`.
2. **Deploy to Multiple Servers**: The pipeline securely SSHs into two separate servers, pulls the new Docker image, and deploys it by stopping the old container (if running) and starting a new one.

### Steps Breakdown

#### 1. **Trigger: Push to `docker-branch`**

- The pipeline is triggered whenever a commit is pushed to the `docker-branch`.
- This ensures the workflow runs every time new code is committed to this branch.

#### 2. **Docker Build**

- The Docker image is built from the project’s root `Dockerfile`.
- The image is tagged as `latest` and stored in Google Cloud Artifact Registry at:
    
    bash
    
    Copy code
    
```
    us-central1-docker.pkg.dev/crmcopilotd/crmcopilot/crm-copilot-app:latest
```
    
```
    docker build --tag us-central1-docker.pkg.dev/${{ env.PROJECT_ID      }}/crmcopilot/crm-copilot-app:latest .
```

#### 3. **Google Cloud SDK Setup**

- The `google-github-actions/setup-gcloud` action sets up the Google Cloud SDK for authentication using a service account key stored as a GitHub secret.
- This enables the GitHub Actions runner to authenticate with Google Cloud and push the Docker image to the Artifact Registry.

```
    `uses: google-github-actions/setup-gcloud@v0.4.0`
```

#### 4. **Push Docker Image to Artifact Registry**

- The Docker image is pushed to the Google Artifact Registry using the `gcloud auth configure-docker` command.
- This ensures that the latest image is stored in a centralized repository, ready for deployment.

```
`gcloud auth configure-docker ${GAR_LOCATION}-docker.pkg.dev --quiet docker push us-central1-docker.pkg.dev/${{ env.PROJECT_ID }}/crmcopilot/crm-copilot-app:latest`
```

#### 5. **Deploy to Server 1 and Server 2**

- The deployment process is executed by SSH-ing into two remote servers (server 1 and server 2), pulling the latest Docker image, stopping the old container (if running), and running the new container.
- SSH keys for both servers are securely passed from GitHub secrets.

**Steps for Deployment:**

1. Create a secure SSH directory and add the private key for SSH login.
2. SSH into the target server and execute the following commands:
    - Prune any unused images to free up space.
    - Pull the latest Docker image from the Artifact Registry.
    - Stop and remove the running container (if applicable).
    - Run the new Docker container with the updated image, exposing it on the specified port (e.g., 5000).

**Server 1:**

```
`docker system prune -a
```

```
docker pull us-central1-docker.pkg.dev/${{ env.PROJECT_ID }}/crmcopilot/crm-copilot-app:latest`
```

**Server 2:**

```
`docker stop crm-copilot-app || true
```

```
docker rm crm-copilot-app || true
```

```
docker run -d -p 5000:5000 --name crm-copilot-app us-central1-docker.pkg.dev/${{ env.PROJECT_ID }}/crmcopilot/crm-copilot-app:latest`
```

### Best Practices

1. **Security**:
    - Service account keys and SSH keys are securely managed via GitHub Secrets, ensuring that sensitive data is not exposed in the workflow.
2. **Consistency**:
    - The `latest` image tag is used for both servers, ensuring that the same image version is deployed across all environments.
3. **Automated Cleanup**:
    - Unused Docker images are pruned before pulling the latest image, helping to free up disk space on the remote servers.
4. **Robust Deployment**:
    - The pipeline gracefully handles existing running containers, stopping and removing them before deploying the new container.

### Summary

This workflow automates the end-to-end process of building, tagging, pushing, and deploying Docker images. The `docker-branch` acts as the source of truth for new changes, triggering this process whenever code is pushed to it. With Google Artifact Registry for image storage and automated deployment via SSH, this pipeline ensures that the latest version of the application is consistently delivered to the servers with minimal manual intervention.