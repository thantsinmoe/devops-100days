Task:
1. Create a deployment named grafana-deployment-devops using any grafana image for Grafana app. Set other parameters as per your choice.

2. Create NodePort type service with nodePort 32000 to expose the app.

# Create deployment
k create deploy grafana-deployment-devops --image=grafana/grafana --dry-run=client -o yaml > deploy.yaml
k apply -f deploy.yaml
k get deploy

# Create service to expose port
k expose deploy grafana-deployment-devops --port=3000 --type=NodePort --dry-run=client -o yaml > service.yaml
vi service.yaml
    # Add nodePort
k apply -f service.yaml
k get svc -o wide

