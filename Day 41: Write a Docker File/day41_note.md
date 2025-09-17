Task:
1. Use ubuntu:24.04 as the base image.
2. Install apache2 and configure it to work on 8088 port. (do not update any other Apache configuration settings like document root etc).

# Write a Dockerfile
sudo vi /opt/docker/Dockerfile

# Dockerfile 
#This is base image
FROM ubuntu:24.04   

#Run command update & install necessary service
RUN apt update && \
    apt install -y apache2 && \
    apt clean

#Change apache port in port.conf and default.conf
RUN sed -i 's/Listen 80/Listen 8088/g' /etc/apache2/ports.conf && \
    sed -i 's/:80/:8088/g' /etc/apache2/sites-enabled/000-default.conf

#Expose a port for the application
EXPOSE 8088

#Define the command to run when the container starts/ FOREGROUND is apache running on container's terminal
CMD [ "apache2ctl", "-D", "FOREGROUND" ]

# Build a docker image
cd /opt/docker
docker build -t apache2:ubuntu .

# Run a container & test apache port
docker run -d -p 8088:8088 --name apache2 apache2:ubuntu
curl localhost:8088