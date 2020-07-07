# Nginx HTTP Load Balance Configuration

## File Locations

```shell
/etc/nginx/conf.d/{your_file_name}
```

## Configurations

```shell
upstream myapp1 {
    server srv1.example.com max_fails=1 fail_timeout=10s;
    server srv2.example.com;
    server srv3.example.com;
}

server {
    listen 80;
    location / {
    	proxy_pass http://myapp1;
    }
}
```

