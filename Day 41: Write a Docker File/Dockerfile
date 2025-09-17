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
