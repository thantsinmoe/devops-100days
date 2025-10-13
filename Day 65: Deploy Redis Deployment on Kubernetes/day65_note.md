Task:
1. Create a config map called my-redis-config having maxmemory 2mb in redis-config.

2. Name of the deployment should be redis-deployment, it should use
redis:alpine image and container name should be redis-container. Also make sure it has only 1 replica.

The container should request for 1 CPU.

Mount 2 volumes:

a. An Empty directory volume called data at path /redis-master-data.

b. A configmap volume called redis-config at path /redis-master.

c. The container should expose the port 6379.

Finally, redis-deployment should be in an up and running state.

# Create configMap 
k get cm
k create cm my-redis-config --from-literal=redis-config="maxmemory 2mb"

# Crate deployment
k create deploy redis-deployment --image=redis:alpine -r 1 --dry-run=client -o yaml  # create template by dry-run
vi redis-deploy.yaml  # Write redis-deploy.yaml
k apply -f redis-deploy.yaml
k get deployments.apps