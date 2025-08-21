Task:
a. Install nginx on LBR (load balancer) server.
b. Configure load-balancing with the an http context making use of all App Servers. Ensure that you update only the main Nginx configuration file located at /etc/nginx/nginx.conf.
c. Make sure you do not update the apache port that is already defined in the apache configuration on all app servers, also make sure apache service is up and running on all app servers.
d. Once done, you can access the website using StaticApp button on the top bar.

cmd >> sudo yum install nginx -y                #Install nginx 
cmd >> sudo systemctl --enable now nginx        #Start and enable nginx service

cmd >> sudo netstat -tulnp | grep httpd         #Check apache servcie port running on appservers

cmd >> sudo vi /etc/nginx/nginx.conf            #Edit nginx.conf to add load balancer

cmd >> sudo nginx -t                            #Check syntex 
cmd >> sudo systemctl restart nginx         