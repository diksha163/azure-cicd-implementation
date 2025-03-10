Azure CI/CD Pipeline Implementation

Overview

The implemented Azure CI/CD pipeline automates the process of building, testing, and deploying a web application to Azure App Services. It leverages Azure DevOps to manage the pipeline, which integrates with Azure Container Registry (ACR) to build and store Docker images, and Azure Web Apps for deployment. The pipeline incorporates multiple best practices such as unit testing, SonarQube integration, and secure secret management using Azure Key Vault.


Tech Stack

1. Version Control: Azure Repos / GitHub
2. CI/CD Tool: Azure DevOps Pipelines
3. Web Framework: Python Flask
4. Containerization: Docker
5. Infrastructure: Azure Web App (Linux, Docker)
6. Code Quality: SonarQube
7. Secrets Management: Azure Key Vault

Azure Resources Setup

1. Azure Virtual Machine : For creating and building the docker image and later pushing it to ACR.
2. Azure Container Registry: For storing the built docker image.
3. Azure Key Vault: For storing and managing secrets like ACR password.
4. Azure Web App: To hosst the containerized application in different environments.
5. Azure DevOps Project: To implement the azure-pipeline.yml for running the pipeline.


Pipeline Overview 

The Azure DevOps Pipeline is defined in the azure-pipeline.yml file which gets triggered on every commit to the main branch and includes the following steps:

1. Azure Key Vault Task: Fetches the service principal credentials from Key Vault.
2. SSH Task: Logs into the VM to build and push the Docker image.
3. Docker Task: Builds and pushes the Docker image to Azure Container Registry (ACR).
4. Deployment Steps: Deploys the image to Azure Web Apps in different environments (Dev, Staging).
