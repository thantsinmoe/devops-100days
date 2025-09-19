Task: 
1. Create a docker network named as media on App Server 1 in Stratos DC.
2. Configure it to use macvlan drivers.
3. Set it to use subnet 192.168.0.0/24 and iprange 192.168.0.0/24.

# Create docker network 
docker network create --driver macvlan --subnet 192.168.0.0/24 --ip-range 192.168.0.0/24 media

# Check network details
docker network inspect media