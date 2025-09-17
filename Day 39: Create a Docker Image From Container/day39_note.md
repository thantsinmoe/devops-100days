Task: Create an image news:nautilus on Application Server 2 from a container ubuntu_latest that is running on same server.

# Check container list
docker ps

# Create docker image from container 
# docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
docker commit --author="steve" --message="create image" ubuntu_latest news:nautilus
# Check docker image list
docker images 

