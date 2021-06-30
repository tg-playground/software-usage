# Redis Errors

## NOAUTH Authentication required

Solution: 

Using right user and password to connect Redis servers.

## org.redisson.client.RedisException: ERR unknown command 'EVAL'

Reason:

Redisson is not compatible with redis "2.4.6" version. Please use 2.8 or higher

Solution:

- Upgrade your Redis server version.

## misconf redis is configured to save rdb snapshots

Solution: 

1. Search dbfilename and dir in your redis conf file
2. Make sure redis have permission to access the {dir} directory and the {dbfilename} file.

