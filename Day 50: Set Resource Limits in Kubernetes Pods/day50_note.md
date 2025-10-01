Task:
Create a pod named httpd-pod with a container named httpd-container. Use the httpd image with the latest tag (specify as httpd:latest). Set the following resource limits:

Requests: Memory: 15Mi, CPU: 100m

Limits: Memory: 20Mi, CPU: 100m

# Create pod with dry-run
k run httpd-pod --image=httpd:latest --dry-run=client -o yaml > pod.yaml

# Edit container name & resource limits
vi pod.yaml    # https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: httpd-pod
  name: httpd-pod
spec:
  containers:
  - image: httpd:latest
    name: httpd-container
    resources: 
        requests:
        memory: "15Mi"
        cpu: "100m"
      limits:
        memory: "20Mi"
        cpu: "100m"

# Run container
k apply -f pod.yaml
k get po
