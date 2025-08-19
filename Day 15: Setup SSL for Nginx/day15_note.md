Task : 
1. Install and configure nginx on App Server 2.
2. On App Server 2 there is a self signed SSL certificate and key present at location /tmp/nautilus.crt and /tmp/nautilus.key. Move them to some appropriate location and deploy the same in Nginx.
3. Create an index.html file with content Welcome! under Nginx document root.
4. For final testing try to access the App Server 2 link (either hostname or IP) from jump host using curl command. For example curl -Ik https://<app-server-ip>/.

cmd >> sudo yum install nginx -y
cmd >> sudo systemctl enable --now nginx
cmd >> sudo mkdir /etc/nginx/ssl                    #Create directory for ssl cert&key
cmd >> sudo mv /tmp/nautilus.*  /etc/nginx/ssl/
cmd >> sudo chmod -R 600 /etc/nginx/ssl/

cmd >> sudo vi /etc/nginx/conf.d/nginx.conf

----nginx.conf-----
server {
    listen 443 ssl;
    server_name localhost;

    ssl_certificate /etc/nginx/ssl/nautilus.crt;
    ssl_certificate_key /etc/nginx/ssl/nautilus.key;

    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}

----------------

cmd >> sudo systemctl restart nginx 
cmd >> echo "Welcome!" | sudo tee /usr/share/testpage/index.html

cmd >> curl -k https://stapp02      #Check from jumphost server