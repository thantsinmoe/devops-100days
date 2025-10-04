Task:
1. Create a pod named volume-share-nautilus.

2. For the first container, use image debian with latest tag only and remember to mention the tag i.e debian:latest, container should be named as volume-container-nautilus-1, and run a sleep command for it so that it remains in running state. Volume volume-share should be mounted at path /tmp/media.

3. For the second container, use image debian with the latest tag only and remember to mention the tag i.e debian:latest, container should be named as volume-container-nautilus-2, and again run a sleep command for it so that it remains in running state. Volume volume-share should be mounted at path /tmp/games.

4. Volume name should be volume-share of type emptyDir.

5. After creating the pod, exec into the first container i.e volume-container-nautilus-1, and just for testing create a file media.txt with any content under the mounted path of first container i.e /tmp/media.

6. The file media.txt should be present under the mounted path /tmp/games on the second container volume-container-nautilus-2 as well, since they are using a shared volume.

# Create pod with dry-run
k run volume-share-nautilus --image=debian:latest --dry-run=client -o yaml 

# Edit pod config, add containers and volume
vi pod.yaml

# pod config 
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: volume-share-nautilus
  name: volume-share-nautilus
spec:
  containers:
  - image: debian:latest
    name: volume-container-nautilus-1
    command: ['sleep', '3600']
    volumeMounts:
    - mountPath: /tmp/media
      name: volume-share
  - image: debian:latest
    name: volume-container-nautilus-2
    command: ['sleep', '3600']
    volumeMounts:
    - mountPath: /tmp/games
      name: volume-share
  volumes:
  - name: volume-share
    emptyDir:

# Apply pod and create txt file inside container-1
k apply -f pod.yaml
k get po
k exec -it volume-share-nautilus -c volume-container-nautilus-1 -- bash
    - cd /tmp/media 
    - echo "Hello World" > media.txt
k exec -it volume-share-nautilus -c volume-container-nautilus-2 -- ls /tmp/games