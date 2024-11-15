CI/CD Pipeline with Terraform, Jenkins, Ansible, Kubernetes, Docker, and Maven
This project demonstrates a complete CI/CD pipeline for automating the deployment of a containerized application on AWS infrastructure. It uses tools like Terraform for infrastructure provisioning, Jenkins for automation, Ansible for configuration management, Kubernetes for orchestration, Docker for containerization, and Maven for Java application builds.

🚀 Tools Used
Terraform: Infrastructure as Code (IaC) to provision AWS resources.
Jenkins: Automation server for CI/CD.
Ansible: Configuration management for application deployment.
Kubernetes: Orchestration platform for containerized applications.
Docker: To containerize the application.
Maven: Build and dependency management for Java projects.
📖 Steps to Set Up
1️⃣ Set Up Terraform Server
Launch an AWS EC2 instance for the Terraform server.
Install Terraform and configure the environment.
Use Terraform scripts to create infrastructure, including Jenkins, Ansible, and EKS cluster.
2️⃣ Provision Jenkins Server
Set up Jenkins using Terraform.
Install required plugins (GitHub, Maven, Publish over SSH).
Integrate Maven for Java application builds.
3️⃣ Provision Ansible Server
Use Terraform to set up the Ansible server.
Install and configure Ansible for Docker image building and Kubernetes deployment.
4️⃣ Build and Push Docker Image
Write a Dockerfile to containerize the application.
Use Ansible to:
Build the Docker image.
Push the image to Docker Hub.
5️⃣ Set Up Kubernetes (EKS)
Provision an EKS cluster using Terraform and eksctl.
Deploy Kubernetes manifests (project-deployment.yml and project-service.yml) to launch the application.
6️⃣ Integrate Jenkins with Ansible and Kubernetes
Configure Jenkins to trigger Ansible playbooks for Kubernetes deployments.
Set up CI jobs for Docker image builds and CD jobs for Kubernetes deployment.
7️⃣ Test the CI/CD Pipeline
Modify the code or README.md and push changes to the Git repository.
Verify that Jenkins triggers a build and deploys the updated application.
📁 Key Files
Terraform Scripts
provider.tf: AWS provider configuration.
main.tf: EC2 instance creation for Jenkins and Ansible servers.
security.tf: Security group configuration.
variables.tf: Configurable variables for the infrastructure.
Docker
Dockerfile: Defines the containerized application.
Ansible Playbooks
project-ci.yml: Builds and pushes Docker images to Docker Hub.
kube_deploy.yml: Deploys the application to Kubernetes.
Kubernetes Manifests
project-deployment.yml: Deployment resource for the application.
project-service.yml: Service resource to expose the application via LoadBalancer.
🛠️ How It Works
Continuous Integration (CI):
Jenkins polls the Git repository for changes.
Maven builds the Java application.
Docker image is built and pushed to Docker Hub.
Continuous Deployment (CD):
Jenkins triggers an Ansible playbook to deploy the application to Kubernetes.
Kubernetes manages the application pods and services.
Testing:
Access the application via the LoadBalancer DNS provided by Kubernetes.
✅ How to Run
Prerequisites
AWS account with appropriate permissions.
Docker Hub account.
Git repository for the project.
Pre-installed tools: Terraform, Jenkins, Ansible, Docker, Maven, and Kubernetes.
Steps
Clone the repository:
bash
Copy code
git clone <repository-url>
cd <repository-name>
Follow the instructions in the respective directories (Terraform Scripts, Ansible, Manifests) to set up infrastructure and deploy the application.
Trigger the CI/CD pipeline by pushing code changes to the repository.
🌐 Accessing the Application
After deployment, retrieve the LoadBalancer DNS from Kubernetes:

bash
Copy code
kubectl get svc
Access the application in your browser using the LoadBalancer DNS:

bash
Copy code
http://<LoadBalancer-DNS>:8080/register/

