# Nginx HTTPS Load Balance Configuration

## File Locations

```shell
/etc/nginx/conf.d/{your_file_name}
```

## Configurations

```shell
upstream backend {
	server localhost:8080 weight=1 max_fails=2 fail_timeout=15s;
    server xxx.xxx.xxx.xxx:8080 weight=1 max_fails=2 fail_timeout=15s;
}

# This server accepts all traffic to port 80 and passes it to the upstream.
# Notice that the upstream name and the proxy_pass need to match.
server {
    listen 80;
    server_name hot.const520.com;
    access_log /var/log/nginx/hot.const520.com/http_access.log;

    location / {
    	proxy_pass http://backend;
    }
}

server {
    listen 443 ssl;
    server_name hot.const520.com;
    ssl_certificate /etc/letsencrypt/live/const520.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/const520.com/privkey.pem;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    access_log /var/log/nginx/hot.const520.com/https_access.log;

    location / {
    	proxy_pass http://backend;
    }
}
```

