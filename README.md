# Kubernetes (kubectl) Command Cheat Sheet

A quick reference guide for commonly used Kubernetes commands during development, troubleshooting, and production operations.

---

# Cluster & Node Commands

## Check cluster information

```bash
kubectl cluster-info
```

## View nodes

```bash
kubectl get nodes
```

## Detailed node information

```bash
kubectl describe node <node-name>
```

## Check node resource usage

```bash
kubectl top nodes
```

---

# Pod Commands

## List pods

```bash
kubectl get pods
```

## List pods with additional details

```bash
kubectl get pods -o wide
```

## Watch pods continuously

```bash
kubectl get pods -w
```

## Describe a pod

```bash
kubectl describe pod <pod-name>
```

## Delete a pod

```bash
kubectl delete pod <pod-name>
```

## Execute commands inside a pod

```bash
kubectl exec -it <pod-name> -- bash
```

or

```bash
kubectl exec -it <pod-name> -- sh
```

---

# Deployment Commands

## List deployments

```bash
kubectl get deployments
```

## Create or update deployment

```bash
kubectl apply -f deployment.yaml
```

## Describe deployment

```bash
kubectl describe deployment <deployment-name>
```

## Delete deployment

```bash
kubectl delete deployment <deployment-name>
```

## Scale deployment

```bash
kubectl scale deployment nginx --replicas=3
```

## Restart deployment

```bash
kubectl rollout restart deployment nginx
```

---

# Service Commands

## List services

```bash
kubectl get svc
```

or

```bash
kubectl get services
```

## Describe service

```bash
kubectl describe svc <service-name>
```

## Delete service

```bash
kubectl delete svc <service-name>
```

---

# YAML Operations

## Apply YAML file

```bash
kubectl apply -f file.yaml
```

## Apply all YAML files in a directory

```bash
kubectl apply -f .
```

## Delete resources using YAML

```bash
kubectl delete -f file.yaml
```

## View resource as YAML

```bash
kubectl get pod nginx -o yaml
```

---

# Logs & Troubleshooting

## View logs

```bash
kubectl logs <pod-name>
```

## Follow logs

```bash
kubectl logs -f <pod-name>
```

## View previous container logs

```bash
kubectl logs --previous <pod-name>
```

## Describe pod for troubleshooting

```bash
kubectl describe pod <pod-name>
```

### Common Troubleshooting Flow

```bash
kubectl get pods

kubectl describe pod <pod-name>

kubectl logs <pod-name>
```

---

# ConfigMap Commands

## Create ConfigMap

```bash
kubectl create configmap app-config \
--from-literal=APP_ENV=dev
```

## List ConfigMaps

```bash
kubectl get configmaps
```

## Describe ConfigMap

```bash
kubectl describe configmap app-config
```

## View ConfigMap YAML

```bash
kubectl get configmap app-config -o yaml
```

---

# Secret Commands

## Create Secret

```bash
kubectl create secret generic mongo-secret \
--from-literal=mongo-user=mongouser \
--from-literal=mongo-password=mongopassword
```

## List Secrets

```bash
kubectl get secrets
```

## Describe Secret

```bash
kubectl describe secret mongo-secret
```

## View Secret YAML

```bash
kubectl get secret mongo-secret -o yaml
```

## Decode Secret

```bash
echo bW9uZ291c2VyCg== | base64 -d
```

---

# Namespace Commands

## List namespaces

```bash
kubectl get ns
```

## Create namespace

```bash
kubectl create namespace dev
```

## Get resources from namespace

```bash
kubectl get pods -n dev
```

## Delete namespace

```bash
kubectl delete namespace dev
```

---

# Rollout Commands

## Check rollout status

```bash
kubectl rollout status deployment nginx
```

## Restart deployment

```bash
kubectl rollout restart deployment nginx
```

## Rollout history

```bash
kubectl rollout history deployment nginx
```

## Rollback deployment

```bash
kubectl rollout undo deployment nginx
```

---

# Resource Monitoring

## Pod resource usage

```bash
kubectl top pods
```

## Node resource usage

```bash
kubectl top nodes
```

---

# Port Forwarding

## Forward port to pod

```bash
kubectl port-forward pod/nginx-pod 8080:80
```

## Forward port to deployment

```bash
kubectl port-forward deployment/webapp 3000:3000
```

## Forward port to service

```bash
kubectl port-forward service/webapp-service 8080:80
```

---

# Generate YAML Templates

## Generate Deployment YAML

```bash
kubectl create deployment nginx \
--image=nginx \
--dry-run=client \
-o yaml
```

## Generate Pod YAML

```bash
kubectl run nginx \
--image=nginx \
--dry-run=client \
-o yaml
```

---

# Context Commands

## Current context

```bash
kubectl config current-context
```

## List contexts

```bash
kubectl config get-contexts
```

## Switch context

```bash
kubectl config use-context minikube
```

---

# Commands Used in Hands-On Labs

Apply resources:

```bash
kubectl apply -f mongo-secret.yaml

kubectl apply -f mongo-config.yaml

kubectl apply -f mongo.yaml

kubectl apply -f webapp.yaml
```

Get resources:

```bash
kubectl get pods

kubectl get svc

kubectl get deployments
```

Inspect pod:

```bash
kubectl describe pod <pod-name>
```

Logs:

```bash
kubectl logs <pod-name>
```

Access pod shell:

```bash
kubectl exec -it <pod-name> -- bash
```

Restart deployments:

```bash
kubectl rollout restart deployment mongo-deployment

kubectl rollout restart deployment webapp-deployment
```

View Secrets and ConfigMaps:

```bash
kubectl get secret mongo-secret -o yaml

kubectl get configmap mongo-config -o yaml
```

---

# Most Important Commands (80/20 Rule)

These commands cover most day-to-day Kubernetes work:

```bash
kubectl get pods

kubectl get svc

kubectl get deployments

kubectl get all

kubectl apply -f file.yaml

kubectl delete -f file.yaml

kubectl describe pod <pod-name>

kubectl logs <pod-name>

kubectl exec -it <pod-name> -- bash

kubectl rollout restart deployment <deployment>

kubectl get secret

kubectl get configmap

kubectl get pods -o wide
```

---

# Kubernetes Troubleshooting Workflow

```bash
kubectl get pods

kubectl describe pod <pod-name>

kubectl logs <pod-name>

kubectl exec -it <pod-name> -- bash

kubectl get svc

kubectl get endpoints

kubectl get events
```

This workflow solves most Kubernetes pod startup, networking, image, and configuration issues.
