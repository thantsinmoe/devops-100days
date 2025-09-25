Task:
1. Create a deployment named httpd to deploy the application httpd using the image httpd:latest (ensure to specify the tag)

Note: The kubectl utility on jump_host is set up to interact with the Kubernetes cluster.

# Check resources
k get resources 
k get resources | grep deploy

# Create deployment
k create deploy httpd --image=httpd:latest --dry-run=client -o yaml > httpd_deployment.yaml
k apply -f httpd_deployment.yaml 

# Check deployment & pod
k get deploy
k get po