# Kubernetes Voting App with Observability

A fully scalable, production-grade voting application deployed on Kubernetes with comprehensive monitoring and observability using Prometheus and Grafana.

## 🎯 Project Overview

This project demonstrates a complete Kubernetes deployment of a multi-tier voting application. The system includes a voting interface, result aggregation, background workers, and persistent data layers—all orchestrated with custom-written manifest files. Real-time monitoring and dashboards track system health and performance metrics across the entire cluster.

## ✨ Key Features

- **Full Kubernetes Deployment**: Voting, Result, Worker, Redis, and Database services running on Kubernetes
- **Custom Manifest Files**: All Deployments, Services, and configurations written from scratch
- **Real-Time Monitoring**: Prometheus scraping metrics from all pods and containers
- **Centralized Dashboards**: Grafana visualizations for service health, container metrics, and pod performance
- **Cluster Networking**: Proper service exposure, port forwarding, and inter-pod communication
- **Production-Grade Configuration**: YAML manifests following Kubernetes best practices

## 🏗️ Architecture

The application consists of five core components:

| Component | Purpose | Type |
|-----------|---------|------|
| **vote** | User-facing voting interface | Deployment |
| **result** | Displays voting results | Deployment |
| **worker** | Processes votes asynchronously | Deployment |
| **redis** | In-memory data store | Deployment |
| **db** | Persistent database | Deployment |

All components are exposed via Kubernetes Services and communicate through cluster networking.

## 🛠️ Tech Stack

- **Container Orchestration**: Kubernetes
- **Infrastructure**: Amazon EC2
- **Monitoring**: Prometheus
- **Visualization**: Grafana
- **Infrastructure as Code**: YAML/Kubernetes Manifests
- **Container Runtime**: Docker

## 📋 Prerequisites

- Kubernetes cluster (local or cloud-based)
- `kubectl` configured
- Docker (for building/pushing images if needed)
- Prometheus and Grafana deployed on the cluster

## 🚀 Getting Started

### 1. Clone the Repository
git clone https://github.com/Krishna7031/k8s-voting-app.git
cd k8s-voting-app

### 2. Apply Kubernetes Manifests
Create namespace (optional)
kubectl create namespace voting-app

Deploy all components
kubectl apply -f deployments/
kubectl apply -f services/

Verify deployments
kubectl get deployments
kubectl get pods
kubectl get services

### 3. Access the Voting App
Port-forward to access the voting interface
kubectl port-forward svc/vote 5000:5000 -n voting-app

Port-forward to access results
kubectl port-forward svc/result 5001:5001 -n voting-app

Then open your browser:
- Voting App: `http://localhost:5000`
- Results: `http://localhost:5001`

### 4. Monitor with Prometheus & Grafana
Port-forward to Prometheus
kubectl port-forward svc/prometheus 9090:9090

Port-forward to Grafana
kubectl port-forward svc/grafana 3000:3000


- Prometheus: `http://localhost:9090`
- Grafana: `http://localhost:3000` (default credentials: admin/admin)

## 📊 Monitoring & Observability

This project includes:

- **Prometheus Scrape Configs**: Configured to collect metrics from all pods
- **Custom Dashboards**: Grafana dashboards displaying:
  - Pod resource utilization
  - Container metrics
  - Service health status
  - Network traffic (bytes transmitted/received)
  - Request latency and error rates

## 🎓 Learning Outcomes

Through this project, I gained hands-on experience with:

✅ **Pod Orchestration**: Managed multiple pods, resource allocation, and scheduling  
✅ **Cluster Networking**: Configured service discovery and inter-pod communication  
✅ **Service Exposure**: Used Services to expose applications internally and externally  
✅ **Port Forwarding**: Enabled external access to internal services  
✅ **Observability**: Implemented comprehensive monitoring and alerting  
✅ **Infrastructure as Code**: Wrote production-grade YAML configurations  

## 🔧 Customization

To modify the application:

1. Update manifest files in `k8s-specifications/`
2. Modify Prometheus scrape configs in `prometheus-stack/prometheus.yml`
3. Update Grafana dashboards for custom metrics
4. Redeploy:
kubectl apply -f k8s-specifications/


## 📝 Production Considerations

- Implement resource quotas and limits for better cluster management
- Set up persistent volumes for data persistence
- Configure network policies for security
- Use namespaces for resource isolation
- Implement auto-scaling based on metrics
- Add health checks and readiness probes (already included)

## 🤝 Contributing

This is a learning project. Feel free to fork, modify, and build upon it!

## 📄 License

Apache 2.0

---

**Deployed on**: Kubernetes (Kind Cluster / EC2)  
