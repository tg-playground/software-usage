# Nginx HTTP Reverse Proxy Configurations

## File Locations

```shell
/etc/nginx/conf.d/{your_file_name}
```

## Configurations

```shell
server
{
	listen 80;
	server_name hot.const520.com;
	location / {
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_pass http://104.225.148.90:8080;
	}
	access_log /var/log/nginx/hot.const520.com/http_access.log;
}
```

