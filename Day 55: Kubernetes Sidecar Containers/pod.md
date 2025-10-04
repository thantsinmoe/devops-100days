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