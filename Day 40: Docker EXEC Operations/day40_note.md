Task: 
a. Install apache2 in kkloud container using apt that is running on App Server 3 in Stratos Datacenter.

b. Configure Apache to listen on port 3002 instead of default http port. Do not bind it to listen on specific IP or hostname only, i.e it should listen on localhost, 127.0.0.1, container ip, etc.

c. Make sure Apache service is up and running inside the container. Keep the container in running state at the end.

# Check container and enter into the container
docker ps
docker exec -it kkloud sh

# Install apache2 and change default port
apt install -y apache2
service apache2 start 
apt install -y vi
vi port.conf (edit port 80 to 3002)
vi /etc/apache2/sites-enabled/000-default.conf (edit port 80 to 3002)

# Restart apache service and check running port
service apache2 restart
curl localhost:3002

# Check container status
docker ps
