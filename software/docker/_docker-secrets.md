# Docker Secrets

## Commands

```shell
################# create ################# 
# Create a secret
printf <secret> | docker secret create my_secret -
# Create a secret with a file
docker secret create my_secret ./secret.json
# Create a secret with labels
docker secret create --label env=dev \
                       --label rev=20170324 \
                       my_secret ./secret.json
# status
docker secret ls
```

