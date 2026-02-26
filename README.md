📦 Kubernetes Beginner Practical Project 

🚀 Project Overview

This project demonstrates core Kubernetes concepts using Minikube.
It covers deployment, service exposure, scaling, self-healing, and rolling updates using an NGINX application.

This is a hands-on beginner DevOps project to understand how Kubernetes manages containerized applications.

🛠️ Technologies Used

Kubernetes

Minikube

Docker

kubectl

NGINX

🏗️ Architecture Flow

Deployment → ReplicaSet → Pod → Container → Application
User → Service → Pod → Container → Application

📌 Step-by-Step Implementation

1️⃣ Start Minikube Cluster

Start the Kubernetes cluster using Docker driver:

minikube start --driver=docker

Check cluster status:

minikube status

Verify node:

kubectl get nodes

## Minikube Running

![Minikube Status](https://github.com/SPaital98/kubernetes-nginx-beginner-project/blob/bcde2bf35fe0981a344e8df4acde40a3e3e0cda3/minikube%20status1.PNG)

✅ This starts the Kubernetes control plane locally.

2️⃣ Create Deployment

Create an NGINX deployment:

kubectl create deployment my-nginx --image=nginx

This automatically creates:

Deployment

ReplicaSet

Pod

Container

3️⃣ Verify Deployment

Check deployment:

kubectl get deployments

Check pods:

kubectl get pods

![Pods Status](https://github.com/SPaital98/kubernetes-nginx-beginner-project/blob/41bf82ceaf9b203c084f65c7f717d8675a76d19b/get%20pods.PNG)

Get detailed pod info:

kubectl get pods -o wide

Describe pod:

kubectl describe pod <pod-name>

4️⃣ Expose Service (NodePort)

Expose deployment externally:

kubectl expose deployment my-nginx --type=NodePort --port=80

Verify service:

kubectl get svc

✅ This creates a Service to allow external access to the application.

5️⃣ Access Application

Port forward to access locally:

kubectl port-forward service/my-nginx 8080:80

Open browser:

http://localhost:8080

You should see the NGINX welcome page.

6️⃣ Scaling the Application

Increase replicas:

kubectl scale deployment my-nginx --replicas=3

Verify scaling:

kubectl get pods

✅ Kubernetes creates additional pods automatically.

7️⃣ Self-Healing Feature

Delete a pod manually:

kubectl delete pod <pod-name>

Check pods again:

kubectl get pods

✅ Kubernetes automatically recreates the deleted pod.

8️⃣ Rolling Update

Update NGINX image version:

kubectl set image deployment/my-nginx nginx=nginx:1.25

Check rollout status:

kubectl rollout status deployment/my-nginx

![Rollout Status](https://github.com/SPaital98/kubernetes-nginx-beginner-project/blob/9f1d32b6da5c2fb2af6e6e9ef46bbdd60601a35b/till%20roll%20out.PNG)

✅ Kubernetes updates pods one by one without downtime.

9️⃣ Clean Up Resources

Delete service:

kubectl delete svc my-nginx

Delete deployment:

kubectl delete deployment my-nginx

🧠 Key Concepts Demonstrated

Kubernetes Cluster Setup

Deployment Management

ReplicaSet & Pod Creation

Service Exposure (NodePort)

Port Forwarding

Horizontal Scaling

Self-Healing

Rolling Updates

Resource Cleanup
