Task:
We already have a secret key file official.txt under /opt location on jump host. Create a generic secret named official, it should contain the password/license-number present in official.txt file.

Also create a pod named secret-datacenter.

Configure pod's spec as container name should be secret-container-datacenter, image should be ubuntu with latest tag (remember to mention the tag with image). Use sleep command for container so that it remains in running state. Consume the created secret and mount it under /opt/games within the container.

To verify you can exec into the container secret-container-datacenter, to check the secret key under the mounted path /opt/games. Before hitting the Check button please make sure pod/pods are in running state, also validation can take some time to complete so keep patience.

# Create secret 
 create secret generic official --from-file=/opt/official.txt

# Create pod
k run secret-datacenter --image=ubuntu:latest --dry-run=client -o yaml  # create template by dry-run
vi pod.yaml   # Write pod.yaml
k apply -f pod.yaml

# Check mounting file inside container
k exec -it secret-datacenter -c secret-container-datacenter -- sh
cd /opt/games
ls 
cat official.txt