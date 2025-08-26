Task : To Configure LAMP server
a. Install httpd, php and its dependencies on all app hosts.

b. Apache should serve on port 8087 within the apps.

c. Install/Configure MariaDB server on DB Server.

d. Create a database named kodekloud_db7 and create a database user named kodekloud_joy identified as password B4zNgHA7Ya. Further make sure this newly created user is able to perform all operation on the database you created.

e. Finally you should be able to access the website on LBR link, by clicking on the App button on the top bar. You should see a message like App is able to connect to the database using user kodekloud_joy

Setup Apache and PHP on App servers.
# Update system
sudo yum update -y

# Install Apache
sudo yum install httpd net-tools -y

# Enable and start Apache
sudo systemctl enable --now httpd

# Change default port from 80 to 3000 
sudo sed -i 's/^\s*Listen 80/Listen 3000 /' /etc/httpd/conf/httpd.conf

# Reload Apache to apply port change
sudo systemctl restart httpd

# Install PHP and common modules
sudo yum install php php-cli php-common php-gd php-mysqlnd php-pdo -y

# Check if Apache is now listening on port 3000 
echo "Checking Apache listening port:"
sudo netstat -tulnp | grep httpd

# Final output
echo "✅ LAMP stack installed. Apache is running on port 3000."

Setup Mariadb on Database server
# Install Mariadb 
sudo yum install mariadb-server mariadb -y
sudo systemctl enable --now mariadb

CREATE USER 'kodekloud_joy'@'%' IDENTIFIED BY 'B4zNgHA7Ya';

CREATE DATABASE kodekloud_db7;

GRANT ALL PRIVILEGES ON kodekloud_db7.* TO 'kodekloud_joy'@'%';

After setup database, restart apache service on app servers agian.



