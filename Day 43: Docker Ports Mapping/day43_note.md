Task:
a. Pull nginx:alpine docker image on Application Server 3.
b. Create a container named media using the image you pulled.
c. Map host port 3001 to container port 80. Please keep the container in running state.

# Pull nginx image
docker pull nginx:alpine

# Run docker container with port mapping
docker run -d --name media -p 3001:80 nginx:alpine