Task : Set up a password-less authentication from jumphost user to another server (app-server)

cmd >> ssh keygen     #Generate ssh key on jumphost server 
ssh key directory - /user/.ssh/

cmd >> ssh-copy-id user@host     #Copy key.pub to another server (eg:ssh-copy-id tony@172.16.238.10)
