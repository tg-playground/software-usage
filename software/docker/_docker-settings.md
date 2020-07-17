# Docker Settings

## System Settings

### Datetime

**Method 1**

You can add your local files (/etc/timezone and /etc/localtime) as volume in your docker-container.

Update your `docker-compose.yml` with the following lines.

```yaml
services:
  my_service:
    ...
    volumes:
      - /etc/localtime:/etc/localtime:ro
```

```yaml
services:
  my_service:
    ...
    volumes:
      - "/etc/timezone:/etc/timezone:ro"
      - "/etc/localtime:/etc/localtime:ro"
```

**Method 2**

docker-compose.yml

```yaml
services:
  my_service:
    #...
    environment: 
      - TZ=Asia/Shanghai
```



## References

Time Zone

- [How to Synchronize Container Timezone With a Host Machine via Docker Compose in Ubuntu 18.04](https://medium.com/better-programming/docker-tips-synchronize-container-timezone-with-host-machine-via-docker-compose-in-ubuntu-18-04-6f01615efc24)
- [Using docker-compose to set containers timezones - Stack Overflow](https://stackoverflow.com/questions/39172652/using-docker-compose-to-set-containers-timezones)
- [Docker Container time & timezone (will not reflect changes) - Server Fault](https://serverfault.com/questions/683605/docker-container-time-timezone-will-not-reflect-changes)
- [5 ways to change time in Docker container](https://bobcares.com/blog/change-time-in-docker-container/)
