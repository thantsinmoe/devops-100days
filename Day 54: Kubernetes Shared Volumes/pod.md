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