
🚀 Task 2: Simple Jenkins Pipeline for CI/CD

 ✅ Objective

To automate the process of building and deploying an application using a basic Jenkins pipeline. This task demonstrates a foundational understanding of Continuous Integration and Continuous Deployment (CI/CD) using Jenkins and Docker.

 🧰 Tools & Technologies Used

* Jenkins – Automation server for building pipelines
* Docker – To containerize and deploy the application
* GitHub – Source code version control
* Jenkinsfile – Declarative pipeline as code
* Node.js or Python – Sample application (optional)

 📁 Project Structure

├── Dockerfile               # Dockerfile to containerize the app
├── Jenkinsfile              # Jenkins pipeline definition
├── app/                     # Sample application source code
│   └── index.js             # Sample app code (Node.js example)
├── .dockerignore
├── .gitignore
└── README.md                # Project documentation


📄 Jenkinsfile

The Jenkinsfile used in this project contains the following stages:

groovy
pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git  https://github.com/Roopaskumar7/Task-2.git
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("my-app-image")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("my-app-image").run("-d -p 3000:3000")
                }
            }
        }
    }
}


✅ Replace the git URL and image names as per your project setup.
 🐳 Dockerfile (Sample for Node.js App)

dockerfile
# Use official Node.js image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy app source code
COPY . .

# Expose port
EXPOSE 3000

# Run the application
CMD ["node", "index.js"]



🚦 How the Pipeline Works

1. Cloning Repository – Pulls the latest code from GitHub.
2. Building Docker Image – Uses the Dockerfile to create a new container image.
3. Deploying Container – Runs the container using Docker on the Jenkins agent or server.


📌 Prerequisites

* Jenkins installed and running
* Docker installed on Jenkins host
* Jenkins Docker plugin (if needed)
* A GitHub repository with your source code and Dockerfile


 📬 Result

By completing this task, the application is automatically built and deployed using Jenkins whenever new changes are pushed to the repository. This CI/CD setup reduces manual work and ensures faster and more reliable delivery.

