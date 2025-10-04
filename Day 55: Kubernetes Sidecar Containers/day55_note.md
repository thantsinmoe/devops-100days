Task:
1. Create a pod named webserver.

2. Create an emptyDir volume shared-logs.

3. Create two containers from nginx and ubuntu images with latest tag only and remember to mention tag i.e nginx:latest, nginx container name should be nginx-container and ubuntu container name should be sidecar-container on webserver pod.

4. Add command on sidecar-container "sh","-c","while true; do cat /var/log/nginx/access.log /var/log/nginx/error.log; sleep 30; done"

5. Mount the volume shared-logs on both containers at location /var/log/nginx, all containers should be up and running.

# Creat pod 
k run webserver --image=nginx:latest --dry-run=client -o yaml
vi pod.yaml
# webserver pod config
    apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: webserver
  name: webserver
spec:
  volumes:
  - name: shared-logs
    emptyDir: {}
  containers:
  - image: nginx:latest
    name: nginx-container
    volumeMounts:
    - mountPath: /var/log/nginx
      name: shared-logs
  - image: ubuntu:latest
    name: sidecar-container
    command: ["sh","-c","while true; do cat /var/log/nginx/access.log /var/log/nginx/error.log; sleep 30; done"]
    volumeMounts:
    - mountPath: /var/log/nginx
      name: shared-logs
# 
k apply -f pod.yaml

# Check status pod
k get po

# Create Streaming logs 
k log -f webserver -c sidecar-container