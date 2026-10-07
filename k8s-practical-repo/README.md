# Kubernetes PostgreSQL Practical Repository

This repository contains Kubernetes YAML manifests for:

- Set A: PostgreSQL + Adminer
- Set B: PostgreSQL + Go API
- Set C: PostgreSQL + Go API + Frontend

## Prerequisite
Create a Kubernetes cluster with one control-plane/master node and one worker node.
Then clone this repository on the master/control-plane node.

## Deploy Set A
```bash
cd set-a-postgres-adminer
kubectl apply -f .
kubectl get pods
kubectl get svc
```
Adminer is exposed through NodePort 30080.

## Deploy Set B
Before applying, edit `set-b-postgres-go-api/go-api-deployment.yaml` and replace:
`YOUR_DOCKERHUB_USERNAME/go-api:latest`
with the Docker image containing your Go API.

Then:
```bash
cd set-b-postgres-go-api
kubectl apply -f .
kubectl get pods
kubectl get svc
```
Go API is exposed through NodePort 30081.

## Deploy Set C
Before applying, build/push the Go API and frontend images and replace the image names in the deployment YAML files.

```bash
cd set-c-three-tier
kubectl apply -f .
kubectl get pods
kubectl get svc
```
Frontend is exposed through NodePort 30082.

## Useful commands
```bash
kubectl get nodes
kubectl get pods -o wide
kubectl get svc
kubectl get deployments
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

## Important
The YAML files deploy the applications. They do not create the AWS EC2 instances or initialize the Kubernetes cluster. Cluster setup must be completed first.
