# CI/CD pipeline project for deploying Cafe App to a Kubernetes cluster using Jenkins

![image](https://github.com/user-attachments/assets/c61a7524-5496-4689-9bcc-0d6484f76832)


Here's some of the key steps for this project for deploying simple cafe app to a Kubernetes cluster using Jenkins:

### Continuous Integration
Setting Up Jenkins:
  Creating a virtual machine (VM) on Azure to host Jenkins.
  Installing Java Development Kit (JDK) and Jenkins on the VM.
  Configuring Jenkins to run on port 8080.

Integrating Ansible with Jenkins:
  Setting up a separate VM on Azure for Ansible.
  Installing Ansible and Docker on the Ansible VM.
  Creating an SSH key for passwordless authentication between Jenkins and the Ansible server.
  Installing the SSH plugin in Jenkins and configure it to communicate with the Ansible server.

Creating Jenkins CI Job:
  In Jenkins, creating a new Freestyle project named CI job cafe app.
  Configuring the job to pull code from a GitHub repository.
  Adding a post-build action to trigger an Ansible Playbook

### Continuous Deployment
Setting Up Kubernetes Cluster:
  Installing Azure CLI on the VM.
  Using Azure CLI to create a Kubernetes cluster with two nodes.
  Connecting to Kubernetes Cluster:

Creating Kubernetes Deployment and Service:
  Writing a deployment manifest file to deploy the application.
  The deployment pulls the Docker image from Docker Hub and runs it in the Kubernetes cluster.
  Writing a service manifest file to expose the deployment.

Create Jenkins CD Job:
  In Jenkins, creating a new job that triggers the deployment process.
  The job runs the Ansible Playbook to:
  Pulling the Docker image from Docker Hub.
  Deploying the image on the Kubernetes cluster using the deployment and service manifest files.

After this setup CI Job is automatically triggered by changes in the GitHub repository, builds and pushes a Docker image. CD Job triggered after the CI job completes, pulls the image from Docker Hub, and deploys it to the Kubernetes cluster.


Thanks https://www.youtube.com/watch?v=DcxhGcWgVUo&list=PLmSlOWkfkugnSv2TCC
