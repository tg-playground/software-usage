# Docker Compose Spring and Redis

**Content**

- Compose Java and Redis 
- Redis Configurations

## Compose Java and Redis 

### Default Method

**1.`docker-compose.yml`** 

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

When you run `docker-compose up`, the following happens:

1. A network called `myapp_default` is created.
2. A container is created using `web`’s configuration. It joins the network `myapp_default` under the name `web`.
3. A container is created using `db`’s configuration. It joins the network `myapp_default` under the name `db`.

Each container can now look up the hostname `web` or `db` and get back the appropriate container’s IP address. For example, `web`’s application code could connect to the URL `postgres://db:5432` and start using the Postgres database.

**2.Spring Redis connection configurations**

```java
//host: redis (service name in docker-compose.yml)
//port: 6379
private Jedis jedis = new Jedis("redis", 6379);
```

### Links method

Links allow you to define extra aliases by which a service is reachable from another service.

They are not required to enable services to communicate - by default, any service can reach any other service at that service’s name. In the following example, `redis` is reachable from `webapp` at the hostnames `redis` and `cache`:

**1.`docker-compose.yml`** 

```yaml
version: "3.8"
services:

  webapp:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    links:
      - "redis:cache"

  redis:
    image: "redis:alpine"
```

Containers for the linked service are reachable at a hostname identical to the alias, or the service name if no alias was specified.

**2.Spring Redis connection configurations**

```java
//host: redis (service name or linked aliases in docker-compose.yml)
//port: 6379
private Jedis jedis = new Jedis("redis", 6379);
// or
private Jedis jedis = new Jedis("cache", 6379);
```



### Networks Method

Instead of just using the default app network, you can specify your own networks with the top-level `networks` key. This lets you create more complex topologies and specify [custom network drivers](https://docs.docker.com/engine/extend/plugins_network/) and options. You can also use it to connect services to externally-created networks which aren’t managed by Compose.

Each service can specify what networks to connect to with the *service-level* `networks` key, which is a list of names referencing entries under the *top-level* `networks` key.

Here’s an example Compose file defining two custom networks. The `proxy` service is isolated from the `db` service, because they do not share a network in common - only `app` can talk to both.

```yaml
version: "3"
services:

  proxy:
    build: ./proxy
    networks:
      - frontend
  app:
    build: ./app
    networks:
      - frontend
      - backend
  db:
    image: postgres
    networks:
      - backend

networks:
  frontend:
    # Use a custom driver
    driver: custom-driver-1
  backend:
    # Use a custom driver which takes special options
    driver: custom-driver-2
    driver_opts:
      foo: "1"
      bar: "2"
```

**0.Create a docker network**

```shell
docker network create <network-name>
```

For example:

```shell
docker network create my-network
```

**1.`docker-compose.yml`** 

```yaml
version: "3.8"
services:

  webapp:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    links:
      - "redis:cache"
    networks:
      - my-network
  redis:
    image: "redis:alpine"
    networks:
      - my-network
networks:
  my-network:
    external: true
```

**2.Spring Redis connection configurations**

```java
//host: redis (service name or linked aliases in docker-compose.yml)
//port: 6379
private Jedis jedis = new Jedis("redis", 6379);
// or
private Jedis jedis = new Jedis("cache", 6379);
```

## Redis Configurations

methods

- Override redis configurations by specify key-value in docker files or application configuration.
- Specify a custom `redis.conf`.



Download a version of `redis.conf` sample file from [Redis Configuration](https://redis.io/topics/config).

### Specify password of Redis in Docker file

` docker-compose.yml`

Use Docker’s CMD override feature with Docker Compose:

You’re likely using Compose and it’s really easy to set a password without any config file shenanigans. If you happen to not be using Compose, you can just override the `CMD` by passing in a custom command to the end of `docker run`.

```yaml
redis:
    image: 'redis:4-alpine'
    # to set a custom password
    command: redis-server --requirepass yourpassword
    volumes:
      - ./docker/redis/redis.conf:/usr/local/etc/redis/redis.conf
    ports:
      - '6379:6379'
```

### Specify password of Redis in redis.conf

```yaml
services:
...
redis:  
  image: redis
  command: redis-server /usr/local/etc/redis/redis.conf
  volumes:
    - ./docker/redis/redis.conf:/usr/local/etc/redis/redis.conf
  ports:
    - "6379:6379"
```

### Specify password on environment file

Specify password on environment file, and gitignore the .env file.

.env

```
REDIS_AUTH=yourpassword
```

docer-compose.yml

```yaml
version: "3.8"
services:

  webapp:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    environment:
      - TZ=Asia/Shanghai
  redis:
    image: "redis:alpine"
    command: redis-server --requirepass ${REDIS_AUTH}
```

Run compose

```shell
# default environment file root directory .env
docker-compose up
#or
docker-compose --env-file ./docker/.env up
```

### Manage sensitive data with Docker secrets

create a secret

```shell
# Create a secret
printf <secret> | docker secret create my_secret -
# Create a secret with a file
docker secret create my_secret ./secret.json

# status
docker secret ls
```

```
printf "yourpassword" | docker secret create redis_pass -
```

To connect this node to swarm

```
docker swarm init
```

docer-compose.yml

```yaml
######### TODO

version: "3.8"
services:

  webapp:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:8080"
    environment:
      - TZ=Asia/Shanghai
  redis:
    image: "redis:alpine"
    secrets:
      - redis_pass
    environment:
        REDIS_PASS_FILE: /run/secrets/redis_pass
    command: [
      "bash", "-c",
      '
       docker-entrypoint.sh
       --requirepass "$$(cat $$REDIS_PASS_FILE)"
      '
    ]
```





## References

[1] [Networking in Compose - docker docs](https://docs.docker.com/compose/networking/)

[2] [compose file reference - docker docs](https://docs.docker.com/compose/compose-file/)

[3] [Communication between Spring Boot and Redis containers - Stack Overflow](https://stackoverflow.com/questions/46135373/communication-between-spring-boot-and-redis-containers)

Redis Configurations

- [Docker-compose , anyway to specify a redis.conf file? - Stack Overflow](https://stackoverflow.com/questions/30547274/docker-compose-anyway-to-specify-a-redis-conf-file)
- [Run Redis with Compose](https://kb.objectrocket.com/redis/run-redis-with-docker-compose-1055)
- [bitnami/redis](https://hub.docker.com/r/bitnami/redis/)
- [Setting a Password on Redis without a Custom Config](https://nickjanetakis.com/blog/docker-tip-27-setting-a-password-on-redis-without-a-custom-config)
- [Environment variables in Compose - docker docs](https://docs.docker.com/compose/environment-variables/)
- [Docker and securing passwords](https://stackoverflow.com/questions/22651647/docker-and-securing-passwords)