# DevOps Lab 2: Containerization and Kubernetes Orchestration

A Flask application that is containerized with Docker and deployed to Kubernetes (Minikube).

## Tools
- Docker Desktop
- Minikube and kubectl
- Python 3.9 and Flask

## Files
- app.py: Flask application
- requirements.txt: Python dependencies
- Dockerfile: builds the image
- deployment.yaml: Kubernetes Deployment (2 replicas)
- service.yaml: Kubernetes NodePort Service
- docker-compose.yml: multi-container setup
- Jenkinsfile: continuous deployment pipeline

## Build and run with Docker
```
docker build -t sample-app:v1 .
docker run -d -p 5000:5000 --name my-running-app sample-app:v1
```
Open http://localhost:5000

## Deploy to Kubernetes
```
minikube start
minikube image load sample-app:v1
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
```

## Scale, update and roll back
```
kubectl scale deployment sample-deployment --replicas=4
docker build -t sample-app:v2 .
minikube image load sample-app:v2
kubectl set image deployment/sample-deployment sample-app=sample-app:v2
kubectl rollout status deployment/sample-deployment
kubectl rollout undo deployment/sample-deployment
```

## Observations
- Pods reached the Running state after kubectl apply.
- Scaling to 4 replicas took a few seconds.
- The rolling update replaced pods without downtime.
- The rollback returned the deployment to the previous version.
