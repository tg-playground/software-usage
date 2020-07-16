# Travis CI



## Getting Started with Travis CI

- Sign up Travis CI by GitHub account.

- Accept the Authorization of Travis CI.

- Add `.travis.yml` file to your repository to tell Travis CI what to do.

  ```
  language: ruby
  rvm:
   - 2.2
   - jruby
  ```

- Push `.travis.yml` file to GitHub and it will trigger a Travis CI build.



## Example Travis CI Configuration File

### My Spring Boot Project Travis-CI config

```yml
language: java
dist: trusty
withIntermediateDirectories: YES
jdk:
  - oraclejdk8
services:
  - redis-server
before_install:
  - sudo mkdir -p /var/log/hot.const520.com
  - sudo touch /var/log/hot.const520.com/hotcrawler.log
  - sudo touch /var/log/hot.const520.com/hotcrawler-test.log
  - sudo chmod 777 /var/log/hot.const520.com/hotcrawler.log
  - sudo chmod 777 /var/log/hot.const520.com/hotcrawler-test.log
install:
  - mvn install -DskipTests=true -Dmaven.javadoc.skip=true -B -V
script:
  - mvn test -B
  - mvn cobertura:cobertura
after_success:
  - bash <(curl -s https://codecov.io/bash)
```



References

[1] [Travis Documentation](https://docs.travis-ci.com/)