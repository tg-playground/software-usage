# Set Maven Environment Variables

Set Maven Environment Variables

```
export MAVEN_OPTS="-verbose:gc -Xms200m -Xmx300m -XX:MaxPermSize=200m"
```

```
export MAVEN_OPTS="-XX:+PrintGCDetails -Xloggc:my_jvm_log.txt"
```

Unset Maven Environment Variables

```
export MAVEN_OPTS=""
```

## References

[1] [Configuring Apache Maven](http://maven.apache.org/configure.html)