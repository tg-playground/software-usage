# Docker Compose

# Install Docker Compose

Download executable file [docker compose](https://docs.docker.com/compose/install/#alternative-install-options)



## Docker Compose Yaml

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

