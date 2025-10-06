Task:
1. Create a deployment using nginx image with latest tag only and remember to mention the tag i.e nginx:latest. Name it as nginx-deployment. The container should be named as nginx-container, also make sure replica counts are 3.

2. Create a NodePort type service named nginx-service. The nodePort should be 30011.

# Creat deployment
k create deploy nginx-deployment --image=nginx:latest --replicas=3 --dry-run=client -o yaml  # dry-run to get yaml output
vi deploy.yaml  # write deploy.yaml

# Apply deployment
k apply -f deploy.yaml
k get deploy

# Expose port
k expose deploy nginx-deployment --name=nginx-service --type=NodePort --port=80 --target-port=80 --dry-run=client -o yaml
vi service.yaml  # write service.yaml
k apply -f service.yaml
