Task:
1. Install docker-ce and docker compose packages on App Server 1.

2. Initiate the docker service.

# Setup docker repository
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

# Install docker-ce and docker compose
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Start service and check status
sudo systemctl enable --now docker
sudo systemctl status docker