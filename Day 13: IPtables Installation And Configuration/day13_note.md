Task : Install iptables and open port 6200 on appservers (apache port) for load balancer server only.

cmd >> sudo yum install iptables-services -y 
cmd >> sudo systemctl enable --now iptables     #start&enable iptables service
cmd >> sudo iptables -F                         #iptables refulsh
cmd >> sudo iptables -A INPUT -i lo -j ACCEPT
cmd >> sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
cmd >> sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
cmd >> sudo iptables -A INPUT -p tcp -s 172.16.238.14 --dport 6200 -j ACCEPT
cmd >> sudo iptables -A INPUT -p tcp --dport 6200 -j DROP

cmd >> sudo service iptables save
cmd >> sudo systemctl restart iptables
cmd >> sudo iptables -L -n --line-numbers