# Docker Compose

**Content**

- Install Docker Compose
- Docker Compose Commands
- Docker Compose Yaml Element Usages
- Docker Compose Yaml Examples

# Install Docker Compose

Download executable file [docker compose](https://docs.docker.com/compose/install/#alternative-install-options)





## Docker Compose Commands

Validate 

```shell
# Validate and view the Compose file
docker-compose config
```

Services & Containers

```shell
########### start and stop ##########
# Build or rebuild services
docker-compose build
# Create and start containers
docker-compose up
docker-compose up -d
# Start services
docker-compose start
# Restart services
docker-compose restart
# stop your services
docker-compose stop
# Kill containers
docker-compose kill

########### status #############
# Display the running processes
docker-compose top
# List images
docker-compose images
# List containers
docker-compose ps
# View output from containers
docker-compose logs
# Print the public port for a port binding
docker-compose port

########### clear #############
# Remove stopped containers
docker-compose rm
# Stop and remove containers, networks, images, and volumes
docker-compose down


######### others ############
# Pull service images
docker-compose pull
# Push service images
docker-compose push
```



## Docker Compose Yaml Element Usages

### volumes in Docker

Docker host-mounted volumes

Syntax: `/host/path`:`/container/path`

Host path can be defined as an absolute or as a relative path.

```yaml
version '3'

services:
  app:
    image: nginx:alpine
    ports:
      - 80:80
    volumes:
      - /var/opt/my_website/dist:/usr/share/nginx/html:ro
```



## Docker Compose Yaml Examples

**`docker-compose.yml` refer to `Dockerfile`**

```yaml
version: "3.8"
services:

  webapp:
    build:
      context: .
      dockerfile: Dockerfile
```

**`docker-compose.yml` spring boot  and redis**

```yaml
version: "3.8"
services:

  webapp:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"

  redis:
    image: "redis:alpine"
```

spring access redis by redis:6379

```java
// redis host is docker service name or service alias
private Jedis jedis = new Jedis("redis", 6379);
```



## References

Docker Compose Yaml Element Usages

- [Using volumes in Docker Compose](https://devopsheaven.com/docker/docker-compose/volumes/2018/01/16/volumes-in-docker-compose.html)