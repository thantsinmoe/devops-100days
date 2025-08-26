Task:
a. Install httpd package and dependencies on app server 1.

b. Apache should serve on port 5001.

c. There are two website's backups /home/thor/media and /home/thor/demo on jump_host. Set them up on Apache in a way that media should work on the link http://localhost:5001/media/ and demo should work on link http://localhost:5001/demo/ on the mentioned app server.

d. Once configured you should be able to access the website using curl command on the respective app server, i.e curl http://localhost:5001/media/ and curl http://localhost:5001/demo/

Install Httpd on App server
# Install Apache
sudo yum install httpd -y

# Enable and start Apache
sudo systemctl enable --now httpd

# Change default port from 80 to 3000 
sudo sed -i 's/^\s*Listen 80/Listen 5001 /' /etc/httpd/conf/httpd.conf

# Reload Apache to apply port change
sudo systemctl restart httpd

# Create folders for source code
sudo mkdir /var/www/html/demo 
sudo mkdir /var/www/html/media

# Create site.conf 
sudo vi /etc/httpd/conf/site.conf

# Copy source code from Jump host server
sudo scp -r demo/* tony@stapp01:/var/www/html/media/
sudo scp -r demo/* tony@stapp01:/var/www/html/demo/

# Test result on App server
curl http://localhost:5001/media/
curl http://localhost:5001/demo/

