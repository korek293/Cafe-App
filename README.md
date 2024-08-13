# CI/CD pipeline project for deploying Cafe App to a Kubernetes cluster using Jenkins

![image](https://github.com/user-attachments/assets/c61a7524-5496-4689-9bcc-0d6484f76832)


Here's some of the key steps for this project for deploying simple cafe app to a Kubernetes cluster using Jenkins:

### CI Job (Continuous Integration)
Set Up Jenkins:

Create a virtual machine (VM) on Azure to host Jenkins.
Install Java Development Kit (JDK) and Jenkins on the VM.
Configure Jenkins to run on port 8080.
Integrate Ansible with Jenkins:

Set up a separate VM on Azure for Ansible.
Install Ansible and Docker on the Ansible VM.
Create an SSH key for passwordless authentication between Jenkins and the Ansible server.
Install the SSH plugin in Jenkins and configure it to communicate with the Ansible server.
Create Jenkins CI Job:

In Jenkins, create a new Freestyle project named CI job cafe app.
Configure the job to pull code from a GitHub repository.
Add a post-build action to trigger an Ansible Playbook that:
Clones the repository from GitHub.
Builds a Docker image from the code.
Tags and pushes the Docker image to Docker Hub.
CD Job (Continuous Deployment)
Set Up Kubernetes Cluster:

Create a new VM to manage the Kubernetes cluster.
Install Azure CLI on the VM.
Use Azure CLI to create a Kubernetes cluster with two nodes.
Connect to Kubernetes Cluster:

Log in to Azure from the VM using Azure CLI.
Install Kubernetes CLI (kubectl) and connect to the Kubernetes cluster.
Create Kubernetes Deployment and Service:

Write a deployment manifest file (Cafe app-deployment.yml) to deploy the application.
The deployment pulls the Docker image from Docker Hub and runs it in the Kubernetes cluster.
Write a service manifest file (Cafe app-service.yml) to expose the deployment.
Create Jenkins CD Job:

In Jenkins, create a new job that triggers the deployment process.
The job runs the Ansible Playbook to:
Pull the Docker image from Docker Hub.
Deploy the image on the Kubernetes cluster using the deployment and service manifest files.
Summary of the Pipeline Flow:
CI Job: Automatically triggered by changes in the GitHub repository, builds and pushes a Docker image.
CD Job: Triggered after the CI job completes, pulls the image from Docker Hub, and deploys it to the Kubernetes cluster.
This pipeline ensures that any code changes in the repository are automatically built, tested, and deployed to the Kubernetes cluster, following a fully automated CI/CD process.
