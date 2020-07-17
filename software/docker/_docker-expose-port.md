# Docker Expose Port

### Difference between “expose” and “publish” in Docker?

`docker run port:port` vs `dockerfile expose port`

Basically, you have three options:

1. Neither specify `EXPOSE` nor `-p`
2. Only specify `EXPOSE`
3. Specify `EXPOSE` and `-p`

1) If you specify neither `EXPOSE` nor `-p`, the service in the container will only be accessible from *inside* the container itself.

2) If you `EXPOSE` a port, the service in the container is not accessible from outside Docker, but from inside other Docker containers. So this is good for inter-container communication.

3) If you `EXPOSE` and `-p` a port, the service in the container is accessible from anywhere, even outside Docker.

### Port in docker run

docker run <host_port>:<app_listening_port> 

- There is a mapping. Map application in docker container listening port to OS host port. 
- OS host port for tcp connection.

### Port in Dockerfile

`EXPOSE:port` in a Dockerfile.

- This port is for docker containers communication. 
- This port is meaning others docker containers can communicate this docker container with EXPOSE:port. 

## References

[1] [What is the difference between “expose” and “publish” in Docker? - Stack Overflow](https://stackoverflow.com/questions/22111060/what-is-the-difference-between-expose-and-publish-in-docker)