# Nginx HTTPS Reverse Proxy Configurations

## File Locations

```shell
/etc/nginx/conf.d/{your_file_name}
```

## Configurations

```shell
server {
	listen 443;
	server_name example.com;
	ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
	ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
	ssl on;
	ssl_session_cache builtin:1000 shared:SSL:10m;
	ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
	ssl_ciphers HIGH:!aNULL:!eNULL:!EXPORT:!CAMELLIA:!DES:!MD5:!PSK:!RC4;
	ssl_prefer_server_ciphers on;
	access_log /var/log/nginx/example.com/https_access.log;
	location / {
		proxy_set_header Host $host;
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
		proxy_set_header X-Forwarded-Proto $scheme;
		proxy_pass http://localhost:8080;
		proxy_read_timeout 90;
		proxy_redirect http://localhost:8080 https://example.com;
	}
}
```

