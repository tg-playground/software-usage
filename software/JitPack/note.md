# JitPack Note

### Easy to use package repository for Git

Publish your JVM and Android libraries



Steps

- Release your GitHub repository.

- Visit JitPack Website. <https://jitpack.io/>. 

- Input your repository url. Like https://github.com/tagnja/java-commons.git, will find your release log.

- To get a Git project into your build. Following the step from JitPack description.

  Add the JitPack repository to your build file

  pom.xml

  ```xml
  <repositories>
      <repository>
          <id>jitpack.io</id>
          <url>https://jitpack.io</url>
      </repository>
  </repositories>
  ```

  Add the dependency

  pom.xml

  ```xml
  <dependency>
      <groupId>com.github.{your_git_name}</groupId>
      <artifactId>{java-commons}</artifactId>
      <version>Tag</version>
  </dependency>
  ```

  