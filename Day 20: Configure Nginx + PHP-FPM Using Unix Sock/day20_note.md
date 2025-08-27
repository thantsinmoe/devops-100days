Task :
1. Install nginx on app server1, configure port 8093, document root should be /var/www/html
2. Install php-fpm version 8.1 on app server1. It must use /var/run/php-fpm/default.sock (create parent directory if does not exist)
3. Configure nginx and php-fpm to work together
4. Test curl http://stapp01:8093/index.php from jump host server.

# Install nginx and enable
sudo yum install nginx -y
sudo systemctl enable --now nginx

# Change nginx port
sudo sed -i 's/^\s*Listen 80/Listen 8093 /' /etc/nginx/nginx.conf
sudo systemctl restart nginx

# Install php-fpm 8.1 on centos 9
sudo dnf install epel-release -y
sudo dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpm -y
sudo dnf module enable php:remi-8.1 -y
sudo dnf install php php-cli php-fpm php-common -y
sudo systemctl enable --now php-fpm

# Configure php-fpm using unix socket
sudo vi /etc/php-fpm.d/www.conf

  listen = /var/run/php-fpm/default.sock                 # change listen socket

sudo systemctl restart php-fpm

# Configure nginx.conf to run with php-fpm
sudo vi /etc/nginx/nginx.conf

# Add config 
  location ~ \.php$ {
      include snippets/fastcgi-php.conf; # Or include fastcgi_params;
      fastcgi_pass unix:/var/run/php-fpm/default.sock;  # Use same socket path as in PHP-FPM config
      fastcgi_index index.php;
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
  }

sudo systemctl restart php-fpm
sudo systemctl restart nginx