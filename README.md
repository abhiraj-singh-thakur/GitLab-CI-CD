# GitLab CI/CD

This repository contains the CI/CD GitLab pipeline code. The project, **Node Notes Taking App**, was deployed on an **EC2 instance** using the GitLab pipeline.

## Project Link
Access the project here: [GitLab Repository](https://gitlab.com/devops9014809/node-todo-cicd)

## About the Project
This project demonstrates the CI/CD pipeline using GitLab CI/CD. The pipeline automates testing, building, security scanning, and deployment of a **Node.js** notes-taking application using **Docker** and **AWS EC2**.

## Prerequisites
- A GitLab account
- An AWS account with an EC2 instance
- GitLab Runner installed and registered on the EC2 instance
- Docker and Docker Compose installed on the EC2 instance
- Trivy for security scanning

## Steps to Set Up the Pipeline

### 1. Create an EC2 Instance
Launch an **EC2 instance** on AWS with the required configurations (e.g., Ubuntu 22.04, t2.micro, security group allowing SSH and required ports).

### 2. Register the EC2 Instance as a GitLab Runner
- Install GitLab Runner on the EC2 instance.
- Register the runner with the GitLab repository using a **registration token**.
- Configure the runner to use the **Docker** executor.

### 3. Create a `.gitlab-ci.yml` File
Define the CI/CD pipeline in `.gitlab-ci.yml` file to automate the deployment process.

### 4. Define Pipeline Stages
The pipeline consists of the following stages:
  - **test**: Runs unit and integration tests.
  - **build**: Builds the Docker image.
  - **scan**: Scans the Docker image for vulnerabilities.
  - **deploy**: Deploys the application to the EC2 instance.

### 5. Define Jobs for Each Stage
Each stage has a corresponding job:
- **test-job**: Runs the test cases using Jest/Mocha.
- **build-job**: Builds the Docker image and pushes it to DockerHub or GitLab Container Registry.
- **scan-job**: Scans the Docker image using **Trivy**, generates a vulnerability report, and stores it in artifacts.
- **deploy-job**:
  - Pulls the latest Docker image.
  - Stops and removes the existing container.
  - Runs the new container using Docker Compose or a direct `docker run` command.

### 6. Configure Environment Variables
Set up environment variables in **GitLab CI/CD settings** (e.g., `DOCKER_USERNAME`, `DOCKER_PASSWORD`).

### 7. Trigger the Pipeline
Push the code to the repository, and the GitLab pipeline will be triggered automatically.

## Deployment Architecture
- The **GitLab Runner** executes the pipeline steps on the EC2 instance.
- The **Dockerized application** is deployed and served using **NGINX or PM2**.
- Security scanning is performed before deployment to ensure a safe production environment.

## Conclusion
This project demonstrates a complete CI/CD pipeline setup using GitLab, from writing code to automated testing, security scanning, and deployment on AWS EC2.

---
For any issues or contributions, feel free to create a pull request or open an issue in the GitLab repository.
