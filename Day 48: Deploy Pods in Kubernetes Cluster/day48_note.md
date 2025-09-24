Task:
1. Create a pod named pod-nginx using the nginx image with the latest tag. Ensure to specify the tag as nginx:latest.

2. Set the app label to nginx_app, and name the container as nginx-container.

# Check kubectl and pod
kubectl
k get po

# Kube Dry run and output file
k run pod-nginx --image=nginx:latest --labels=app=nginx_app --dry-run=client -o yaml > nginx.yaml

# Edit output file
vi nginx.yaml
    apiVersion: v1
    kind: Pod
    metadata:
    labels:
        app: nginx_app
    name: pod-nginx
    spec:
    containers:
    - image: nginx:latest
        name: nginx-container

# Kube apply and check pod status
k apply -f nginx.yaml
k get po