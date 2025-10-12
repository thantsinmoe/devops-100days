Task:
1. Create a Deployment named as ic-deploy-nautilus.

2. Configure spec as replicas should be 1, labels app should be ic-nautilus, template's metadata lables app should be the same ic-nautilus.

3. The initContainers should be named as ic-msg-nautilus, use image debian with latest tag and use command '/bin/bash', '-c' and 'echo Init Done - Welcome to xFusionCorp Industries > /ic/beta'. The volume mount should be named as ic-volume-nautilus and mount path should be /ic.

4. Main container should be named as ic-main-nautilus, use image debian with latest tag and use command '/bin/bash', '-c' and 'while true; do cat /ic/beta; sleep 5; done'. The volume mount should be named as ic-volume-nautilus and mount path should be /ic.

5. Volume to be named as ic-volume-nautilus and it should be an emptyDir type.

# Create deployment 
k create deploy ic-deploy-nautilus --image=debian:latest --replicas=1 --dry-run=client -o yaml   # create template by dry-run
vi deploy.yaml  # Write deploy.yaml
k apply -f deploy.yaml

# Check container logs 
k logs ic-deploy-nautilus-544bd54685-zfwd6 -c ic-main-nautilus