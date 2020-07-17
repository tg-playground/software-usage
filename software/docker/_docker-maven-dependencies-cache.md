# Docker Maven Dependencies Cache

Edit `Dockerfile` of your project:

```dockerfile
#
# Build stage
#
FROM maven:3.5.3-jdk-8-alpine AS maven
# copy the project files
COPY ./pom.xml ./pom.xml
# build all dependencies
RUN mvn dependency:go-offline -B
# copy your other files
COPY ./src ./src
# build for release
RUN mvn clean
RUN mvn package spring-boot:repackage

#
# Package stage
#

# our final base image
FROM openjdk:8-jdk-alpine
# set deployment directory
WORKDIR /app/jenkins-playground
# copy over the built artifact from the maven image
COPY --from=maven target/*.jar ./app.jar
EXPOSE 8080
# set the startup command to run your binary
ENTRYPOINT ["java","-jar","./app.jar"]
```

Docker build

```shell
cd <your_project_dir>
docker build -t <your_specified_image_name> .
```

Docker run

```
docker run -d -p 8080:80 <your_image_name>
```



## References

[1] [Optimizing Docker Images for Maven Projects](http://whitfin.io/speeding-up-maven-docker-builds/)

