Task: 1. On Application Server 1 create a container named nginx_1 using the nginx image with the alpine tag. Ensure container is in a running state.

# Pull nginx:alpine image from docker hub
sudo docker pull nginx:alpine

# Run docker container 
sudo docker run -d --name nginx_1 nginx:alpine  
docker ps -a        

