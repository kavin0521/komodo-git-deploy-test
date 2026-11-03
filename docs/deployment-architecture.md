# Application Deployment – Infrastructure Overview

## 1. Overview

The goal of this project is to make application deployment easier for our developers.

We want to connect our GitHub repositories with Komodo so that application changes can go through a consistent build and deployment process without manually handling everything on the server.

We also want to create a common setup that developers can reuse for future projects.

For the first implementation, we are focusing on the DEV environment and a simple Hello World application.

## 2. How the Deployment Process Works

The planned deployment process is:

1. A developer pushes code to the application's GitHub repository.
2. GitHub Actions runs the required build and testing steps.
3. The application is packaged into a Docker image.
4. The image is stored in the configured container registry.
5. Komodo manages deployment to the appropriate Unraid server.
6. The team can monitor the application and check deployment logs.
7. Slack notifications can alert the team when something goes wrong.

The idea is to make this process consistent across applications so developers don't need to create a completely different deployment process every time.

## 3. Services and Components

### GitHub

GitHub stores the application source code and deployment configurations. Each application container should have a corresponding repository in our organization.

### GitHub Actions and Runners

GitHub Actions handles automated workflows, including building and testing applications.

Runners execute these workflows. We need to verify that the required runners are available and configured correctly.

### Docker

Docker packages each application and its dependencies into a container. This helps applications run consistently across different environments.

### Container Registry

The registry stores Docker images produced during the build process. These images can then be used for deployment.

GHCR is mentioned in the Infra documentation, while the existing reusable CI workflows also contain Docker Hub configuration. The final registry approach still needs confirmation.

### Komodo

Komodo is used to manage and coordinate deployments through its web interface. It helps manage containers and servers from one place.

The plan is to connect application repositories with their corresponding Komodo deployment configurations.

### Unraid

Unraid provides the servers where application containers will run.

The DEV servers need to be connected to Komodo so that deployments can be managed centrally.

### Secrets Management – SOPS and Infisical

Applications need sensitive information such as passwords, API keys and database credentials.

SOPS is already used in the existing infrastructure to encrypt sensitive configuration files. It works with age encryption keys.

Infisical is another secrets-management service discussed during the meeting. We still need to confirm whether the final approach will use SOPS, Infisical, Komodo secrets, or a combination.

Private keys and unencrypted secrets must never be committed to GitHub.

### Renovate

Renovate checks for newer versions of dependencies and Docker images. It can create pull requests when updates are available.

This helps keep application dependencies and images updated.

### Slack Notifications and Uptime

We want to connect deployment notifications with Slack so the team knows when a build or deployment fails.

We also need to monitor whether deployed applications are running properly and identify issues early.

The exact uptime-monitoring and notification configuration still needs confirmation.

## 4. What We Are Building First

For the initial implementation, we are using a simple Hello World application.

The purpose is to test the complete process before using the same approach for other applications.

The test project will help us verify:

- Code changes trigger the required GitHub workflow.
- The Docker image builds successfully.
- The image can be stored in the selected registry.
- Komodo can use the Git repository and image to manage deployment.
- The application can run on the DEV Unraid server.
- Deployment errors can be identified and reported.

Once this works, the same setup can be used as a starting point for other developers.

## 5. Current Progress

The Hello World application is running locally using Docker and Docker Compose.

A GitHub Actions workflow has been created to validate the Compose configuration, build the Docker image and test the webpage. The workflow has completed successfully.

The project README and infrastructure research notes have also been added to the test repository.

SOPS encryption and decryption have been tested locally using a separate test key and dummy credentials.

The following items are still pending:

- Confirming the container registry.
- Verifying the available GitHub runners.
- Connecting the GitHub repository with Komodo.
- Getting access to the DEV Unraid server.
- Finalizing the secrets-management approach.
- Testing the complete deployment process.
- Configuring Slack notifications and uptime monitoring.

## 6. Next Steps

The next step is to connect the Hello World project with the approved registry and Komodo configuration.

After that, we will test deployment on the DEV server and document the process so other developers can follow the same steps when creating applications.

The main objective is to have one working deployment example that can be reused across future projects.

---

Note: This document describes the planned deployment approach and progress verified so far. Components awaiting access or confirmation are marked as pending rather than presented as completed.