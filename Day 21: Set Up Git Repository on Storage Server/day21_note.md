Task:
1. Utilize yum to install the git package on the Storage Server.
2. Create a bare repository named /opt/games.git (ensure exact name usage).

# Install git 
sudo yum install -y git

# Create bare git repository
cd /opt
sudo git init --bare games.git