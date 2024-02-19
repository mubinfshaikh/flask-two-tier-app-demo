# How to setup two-tier application deployment on kubernetes cluster
## Prerequisite :setup kubernetes kubeadm cluster

## Setup
- First clone the code to your machine
```bash
git clone git clone https://github.com/mubinfshaikh/flask-two-tier-app-demo.git
```
- Move to k8s directory
```bash
cd flask-two-tier-app-demo/kubernetes
```
- Now, execute below commands one by one
```bash
kubectl apply -f twotier-deployment.yml
```
```bash
kubectl apply -f twotier-deployment-svc.yml
```
```bash
kubectl apply -f mysql-deployment.yml
```
```bash
kubectl apply -f mysql-deployment-svc.yml
```
```bash
kubectl apply -f persistent-volume.yml
```
```bash
kubectl apply -f persistent-volume-claim.yml
```

## or
- You can run all manifests at once
```bash
cd flask-two-tier-app-demo/kubernetes
kubectl apply -f .
```
