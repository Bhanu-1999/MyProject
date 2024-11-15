CI/CD Pipeline with Terraform, Jenkins, Ansible, Kubernetes, Docker, and Maven
This project demonstrates a complete CI/CD pipeline for automating the deployment of a containerized application on AWS infrastructure. It uses tools like Terraform for infrastructure provisioning, Jenkins for automation, Ansible for configuration management, Kubernetes for orchestration, Docker for containerization, and Maven for Java application builds.

Overview
Tools Used:
Terraform: Infrastructure as Code (IaC) to provision AWS resources.
Jenkins: Automation server for CI/CD.
Ansible: Configuration management for application deployment.
Kubernetes: Orchestration platform for containerized applications.
Docker: To containerize the application.
Maven: Build and dependency management for Java projects.
Steps
1. Set Up Terraform Server
Launch an AWS EC2 instance for the Terraform server.
Install Terraform and configure the environment.
Use Terraform to create infrastructure (e.g., Jenkins server, Ansible server, and EKS cluster).
2. Provision Jenkins Server
Use Terraform to set up a Jenkins server with necessary security groups.
Install Jenkins and configure it with plugins (e.g., GitHub, Maven, and Publish over SSH).
Integrate Maven for Java builds.
3. Provision Ansible Server
Set up Ansible server using Terraform.
Install and configure Ansible to manage Docker tasks and Kubernetes deployments.
4. Build and Push Docker Image
Write a Dockerfile for the application.
Use an Ansible playbook to:
Build a Docker image.
Push the image to Docker Hub.
5. Set Up Kubernetes (EKS)
Provision an EKS cluster using Terraform and eksctl.
Install kubectl and eksctl on the EKS server.
Deploy application manifests (project-deployment.yml and project-service.yml) using Kubernetes.
6. Integrate Jenkins with Ansible and Kubernetes
Use Jenkins to trigger Ansible playbooks for deploying the application to Kubernetes.
Create jobs in Jenkins for CI (code integration and Docker image build) and CD (deployment to Kubernetes).
7. Test the CI/CD Pipeline
Modify the application code or README.md file and push changes to the Git repository.
Verify that Jenkins triggers a build and deploys the updated application to the EKS cluster.
Key Files
Terraform Scripts:

provider.tf: AWS provider configuration.
main.tf: AWS EC2 instance creation for Jenkins and Ansible servers.
security.tf: Security group configuration.
variables.tf: Variables for Terraform resources.
Docker:

Dockerfile: Containerizes the Java application with Tomcat.
Ansible Playbooks:

project-ci.yml: Build and push Docker image to Docker Hub.
kube_deploy.yml: Deploy application to Kubernetes.
Kubernetes Manifests:

project-deployment.yml: Deployment resource for the application.
project-service.yml: LoadBalancer service for exposing the application.
How It Works
Continuous Integration (CI):

Jenkins polls the Git repository for changes.
Maven builds the Java application.
Docker image is built and pushed to Docker Hub.
Continuous Deployment (CD):

Jenkins triggers an Ansible playbook to deploy the application to Kubernetes.
Kubernetes manages the application pods and services.
Testing:

Access the application via the LoadBalancer DNS exposed by the EKS cluster.
How to Run
Prerequisites:
AWS account with necessary permissions.
Docker Hub account.
Git repository for the project.
Pre-installed tools: Terraform, Jenkins, Ansible, Docker, Maven, and Kubernetes.
Steps:
Clone the repository:

bash
Copy code
git clone <repository-url>
cd <repository-name>
Follow the instructions in the respective directories (Terraform Scripts, Ansible, Manifests) to set up infrastructure and deploy the application.

Trigger the CI/CD pipeline by making changes to the codebase and pushing to the repository.

Accessing the Application
After deployment, retrieve the LoadBalancer DNS from Kubernetes and access the application in your browser:

bash
Copy code
kubectl get svc
URL: http://<LoadBalancer-DNS>:8080/register/


