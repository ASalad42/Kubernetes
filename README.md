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

### Nginx-deploy 

- create folder > create nginx-deploy.yml 

```
# kubectl get service_name - deployment -pod - rs
# kubectl get deploy nginx-deploy (nginx_svc)
# kubectl get pods 
# kubectl describe pod_name
# kubectl descrie svc kubernetes 

apiVersion: apps/v1
kind: Deployment

# what would you like to call it - name the service/object
metadata:
  name: nginx-deploy # naming deployment 
spec:
  selector:
    matchLabels:
      app: nginx # looks for this lable to match with k8 service 
  # lets create a replica set of this with instances/pods
  replicas: 3
  # template to use its lable for k8 service to launch in browser
  template: 
    metadata:
      labels: 
        app: nginx 
    
    spec:
      containers:
      - name: nginx 
        image: asalad42/eng122_nginx_web_hosting:latest 
        ports:
        - containerPort: 80 
```

- `kubectl get svc`
- `kubectl create -f nginx-deploy.yml`
- `kubectl get deploy`
- `kubectl get pods`

![image](https://user-images.githubusercontent.com/104793540/190618815-931a17cb-1fd0-45a5-85a8-89a8b2db95ea.png)

### Nginx service 
create nginx service yml file 


```
apiVersion: v1

kind: Service

# Metadata for name

metadata:  

  name: nginx-svc

  namespace: default # sre  

# Specificaition to include ports Selector to connecto to the deployment

spec:  

  ports:

  - nodePort: 30442 # range is 30000-32768

    port: 80

    protocol: TCP

    targetPort: 80

# Let's define the selector and label to connect to nginx deployment

  selector:

    app: nginx # this label connects this service to deployment

  # Creating NodePort type of deployment

  type: NodePort # also use LoadBalancer -  for local use cluster IP
```
- ``
- ``
- `kubectl create -f nginx-service.yml`
- `kubectl get svc`
