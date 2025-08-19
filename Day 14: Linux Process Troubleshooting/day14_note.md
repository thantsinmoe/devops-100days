Task : Check apache service to run with port 3000 on appserver

cmd >> sudo systemctl status httpd
cmd >> sudo journalctl -xue httpd

cmd >> sudo netstat -tulnp | grep 3000          #Check which service using prot 3000

#Sendmail service using port 3000

cmd >> sudo systemctl stop sendmail
cmd >> sudo systemctl disable sendmail          #stop&disable service

cmd >> sudo systemctl start httpd               
cmd >> sudo systemctl enable httpd              #Start&enable apache service

