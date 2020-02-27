# Tomcat Server Configurations

## File Locations

```shell
{tomcat_home}/conf/server.xml
```

## Configurations

```shell
<!-- HTTP -->
<Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
<!-- Database Connection Pool -->
```

