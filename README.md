# DevOps and Automation Lab - Lab 2
Containerization and Kubernetes Orchestration

Welcome to my official repository for Lab 2. This repository contains all the code, container configurations, and Kubernetes orchestration manifests required to complete the DevOps and Automation Lab assignments.

## Tech Stack and Tools Used
* Containerization: Docker and Docker Desktop
* Orchestration: Kubernetes (Minikube, kubectl)
* Application Framework: Python, Flask

## Project Directory Structure
```text
DevOps-Lab2/
│
├── app.py              # Main Flask web application code
├── requirements.txt    # Python dependencies (Flask)
├── Dockerfile          # Instructions to build the Docker container image
├── deployment.yaml     # Kubernetes Deployment configuration (Replicas & Pods)
└── service.yaml        # Kubernetes Service configuration (NodePort)

## Step-by-Step Execution Guide

### 1. Build and Run Docker Container Locally
To build the Docker image and run the application locally on your machine:
docker build -t sample-app:v1 .
docker run -d -p 5000:5000 --name my-running-app sample-app:v1

You can access the running application in your web browser at: http://localhost:5000

### 2. Deploy to Kubernetes (Minikube)
To deploy the application inside a local Kubernetes cluster using Minikube:
minikube start
minikube image load sample-app:v1
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods

### 3. Scaling the Application Replicas
To test scaling capabilities within the Kubernetes cluster:
kubectl scale deployment sample-deployment --replicas=4
kubectl get pods

## Lab Verification and Evidence
* Local Container Test: Successfully verified via browser showing "Hello from DevOps Lab 2!".
* Kubernetes Pods: Running instances successfully verified through kubectl get pods.
* Replica Scaling: Scaled up smoothly to multiple active replicas.

Student Details:
* Name: Akshita Sharma
* Course: DevOps and Automation Lab (ENSP461)
