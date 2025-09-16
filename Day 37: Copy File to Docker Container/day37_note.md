1. Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /opt/. Ensure the file is not modified during this operation. 

# Copy file to docker container 
docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/opt/

# Check file inside of container
docker exec -it ubuntu_latest ls -la /opt/
