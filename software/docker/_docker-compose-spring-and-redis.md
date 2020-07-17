# Docker Compose Spring and Redis



## Default Method

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

## Links method

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



## References

[1] [Networking in Compose - docker docs](https://docs.docker.com/compose/networking/)

[2] [compose file reference - docker docs](https://docs.docker.com/compose/compose-file/)

