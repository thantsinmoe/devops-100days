Task:
1. Execute a rolling update for this application, integrating the nginx:1.19 image. The deployment is named nginx-deployment.

Ensure all pods are operational post-update.

# Check deployment and pods
k get deploy
k get pods
k describe deploy nginx-deployment

# Change nginx image # kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=docker.io/jocatalin/kubernetes-bootcamp:v2
k set image deployment/nginx-deployment nginx-container=nginx:1.19

# Check the status of rolling update
k rollout status deployments/nginx-deployment