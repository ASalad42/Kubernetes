# Kubernetes - Production-Grade Container Orchestration

![image](https://user-images.githubusercontent.com/104793540/190595401-22a89af5-a911-4823-b50f-baa75e281805.png)

##  What k8 is 
Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.
It groups containers that make up an application into logical units for easy management and discovery. 

## K8 Architecture 
- open source orchestrator for microservice apps
- Kubernetes clusters together groups of hosts running containers, and helps you easily and efficiently manage those clusters.

### Kubernetes Features:

- self healing 
- Storage orchestration
- Secret and configuration management
- Service discovery and load balancing
- Automated rollouts and rollbacks


- cluster 
- Nodes - The Kubernetes Workers

Kubernetes runs your workload by placing containers into Pods to run on Nodes. A node may be a virtual or physical machine, depending on the cluster. Each node is managed by the control plane and contains the services necessary to run Pods.

Typically you have several nodes in a cluster

- Pods - To scale, create more pods
- service 
