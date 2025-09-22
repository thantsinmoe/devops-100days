Task:
1. On App Server 3 in Stratos Datacenter create a docker compose file /opt/dba/docker-compose.yml (should be named exactly).

2. The compose should deploy two services (web and DB), and each service should deploy a container as per details below:

For web service:

a. Container name must be php_apache.

b. Use image php with any apache tag. Check here for more details.

c. Map php_apache container's port 80 with host port 3000

d. Map php_apache container's /var/www/html volume with host volume /var/www/html.

For DB service:

a. Container name must be mysql_apache.

b. Use image mariadb with any tag (preferably latest). Check here for more details.

c. Map mysql_apache container's port 3306 with host port 3306

d. Map mysql_apache container's /var/lib/mysql volume with host volume /var/lib/mysql.

e. Set MYSQL_DATABASE=database_apache and use any custom user ( except root ) with some complex password for DB connections.

After running docker-compose up you can access the app with curl command curl <server-ip or hostname>:3000/

# Create docker-compose.yml
cd /opt/dba/
vi docker-compose.yml

# docker-compose.yml
version: '3.8'

services:
  web:
    container_name: php_apache
    image: php:apache
    ports:
      - "3000:80"
    volumes:
      - /var/www/html:/var/www/html
    depends_on:
      - db
  db:
    container_name: mysql_apache
    image: mariadb:latest
    ports:
      - "3306:3306"
    volumes:
      - /var/lib/mysql:/var/lib/mysql
    environment:
      MYSQL_DATABASE: database_apache
      MARIADB_ROOT_PASSWORD: R00tP@ssw0rd
      MYSQL_USER: app_user
      MYSQL_PASSWORD: Str0ngP@ssw0rd

# Run container & check application
docker compose up -d
docker ps -a
curl stapp03:3000