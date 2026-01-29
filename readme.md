# Kubernetes Demo Application

A complete Kubernetes deployment example featuring a MongoDB database and a web application.

## 📁 Project Structure

This repository contains the following Kubernetes manifest files:

| File | Description |
|------|-------------|
| `mongo-config.yaml` | ConfigMap for MongoDB configuration |
| `mongo-secret.yaml` | Secret for MongoDB credentials |
| `mongo.yaml` | MongoDB deployment and service |
| `webapp.yaml` | Web application deployment and service |

## 🚀 Getting Started

### Prerequisites
- [Minikube](https://minikube.sigs.k8s.io/docs/start/) installed
- [kubectl](https://kubernetes.io/docs/tasks/tools/) installed
- Docker or VirtualBox (for Minikube driver)

### Setup Instructions

1. **Start Minikube**
   ```bash
   minikube start
   minikube status
   ```

2. **Deploy the application**
   ```bash
   kubectl apply -f mongo-config.yaml
   kubectl apply -f mongo-secret.yaml
   kubectl apply -f mongo.yaml
   kubectl apply -f webapp.yaml
   ```

3. **Access the application**
   ```bash
   minikube service webapp-service
   ```

## 📋 Useful Commands

### Cluster Management
```bash
# Start Minikube
minikube start

# Check cluster status
minikube status

# Get cluster IP
minikube ip

# Stop Minikube
minikube stop
```

### Resource Management
```bash
# Get basic info about components
kubectl get nodes
kubectl get pods
kubectl get services
kubectl get all

# Get detailed info with extended output
kubectl get pods -o wide
kubectl get nodes -o wide

# Describe specific resources
kubectl describe service {service-name}
kubectl describe pod {pod-name}

# View application logs
kubectl logs {pod-name}
```

### Debugging & Troubleshooting
```bash
# Check pod status and events
kubectl get pods --watch

# Get detailed pod information
kubectl describe pod {pod-name}

# Access pod shell
kubectl exec -it {pod-name} -- /bin/bash

# Port forwarding for local testing
kubectl port-forward service/{service-name} {local-port}:{service-port}
```

## 🛠 Troubleshooting

### Common Issues

**Issue: Minikube IP not accessible**
```bash
# Solution: Use minikube service command
minikube service webapp-service
```

**Issue: Pods stuck in Pending state**
```bash
# Check node resources
kubectl describe nodes

# Check pod events
kubectl describe pod {pod-name}
```

**Issue: ImagePullBackOff errors**
```bash
# Check if images are available
kubectl describe pod {pod-name}

# For Minikube, use local Docker daemon
eval $(minikube docker-env)
```

## 🔗 Resources

- [MongoDB Docker Image](https://hub.docker.com/_/mongo)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)

## 📝 Notes

This demo application is designed for learning purposes and demonstrates:
- ConfigMaps and Secrets management
- Multi-tier application deployment
- Service networking
- Basic Kubernetes concepts

---
*Last updated: January 2026*

