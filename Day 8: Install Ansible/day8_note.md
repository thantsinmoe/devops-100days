Task : Install Ansible version 4.7.0 by using pip3 to run all user on jumphost server

cmd >> which pip3      #Check pip3 already exist or not
output >> /usr/local/bin/pip3

cmd >> sudo pip3 install ansible==4.7.0   #Install Ansible
cmd >> ansible --version     #Check ansible version

cmd >> sudo visudo       #Edit sudoer file, if can't run ansible by sudo user

Defaults        secure_path= /sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin"