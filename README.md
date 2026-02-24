 # MEAN Stack Application: Automated Deployment to AWS
 The main aim of the task is  establishes a fully automated CI/CD pipeline using GitHub Actions to build, push to Docker Hub, and deploy the application with zero manual intervention.
 1. Local Configuration
Clone the repository: git clone <your-repo-link>.

Ensure Docker and Docker Compose are installed on your machine.

Run the application locally using: docker compose up --build.

2. Infrastructure Setup
Cloud Provider: AWS EC2 (Ubuntu 24.04 LTS).

Web Server: Nginx is configured within the frontend container to serve static assets on Port 80.

Network: AWS Security Groups are configured to allow inbound traffic on Port 80 (HTTP) and Port 22 (SSH).

3. CI/CD Pipeline
The pipeline is triggered automatically on every push to the main branch.

GitHub Actions builds the Docker images for both frontend and backend.

Images are pushed to Docker Hub.

The pipeline connects to the EC2 instance via SSH, pulls the latest images, and restarts the containers using Docker Compose.

1. CI/CD Configuration and Execution
Shows the automated GitHub Actions workflow successfully triggering and completing.

2. Docker Image Build and Push Process
Logs showing the multi-stage Docker build and the successful push to the Docker Hub registry.

3. Application Deployment and Working UI
The live application running on AWS (at 54.255.151.217) showing a functional "Tutorials List".

4. Nginx Setup and Infrastructure Details
Proof of the AWS Security Group configuration and the Nginx web server handling Port 80 traffic.
   
