Task : Disable direct SSH root login to server
SSH config directory - /etc/ssh/sshd_config
cmd >> vi /etc/ssh/sshd_config     #Open ssh confing file
edit & save config >> PermitRootLogin = no 
cmd >> sudo systemctl restart sshd  # Restart ssh service
