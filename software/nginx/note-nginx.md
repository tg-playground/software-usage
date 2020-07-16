# Note of Nginx

conf

/etc/nginx/conf.d

### Start or Stop Nginx

The same commands can be used to start / stop / restart the nginx server on a Ubuntu Linux:

```shell
sudo systemctl start nginx  
sudo systemctl stop nginx  
sudo systemctl restart nginx
```

OR

```shell
sudo service nginx start 
sudo service nginx stop 
sudo service nginx restart
```

OR

```shell
sudo /etc/init.d/nginx start 
sudo /etc/init.d/nginx stop 
sudo /etc/init.d/nginx restart
```

### Nginx Command

```
nginx -s <SIGNAL>
```

`<SIGNAL>` can be one of the following:

- `quit` – Shut down gracefully
- `reload` – Reload the configuration file
- `reopen` – Reopen log files
- `stop` – Shut down immediately (fast shutdown)



### Configuration Reverse Proxy

80. reverse_proxy.conf

```
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



443. https_reverse_proxy.conf

```
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



### Using nginx as HTTP Load Balancer

The simplest configuration for load balancing, /etc/nginx/conf.d/load-balancer.conf

```shell
http {
    upstream myapp1 {
        server srv1.example.com;
        server srv2.example.com;
        server srv3.example.com;
    }

    server {
        listen 80;

        location / {
            proxy_pass http://myapp1;
        }
    }
}
```

Directives

- Weight 
- Hash (respond to clients same VPS each time)
- Max Fails (Health checks)



HTTP Load Balancing

/etc/nginx/conf.d/load-balancer.conf

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



My HTTPS Load Balancing Example

/etc/nginx/conf.d/load-balancer.conf

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



### Reference

Reverse Proxy

- [Simple guide to configure Nginx reverse proxy with SSL](https://linuxtechlab.com/simple-guide-to-configure-nginx-reverse-proxy-with-ssl/)

Load Balancing

- [Using nginx as HTTP load balancer - nginx doc](http://nginx.org/en/docs/http/load_balancing.html)

- [How To Set Up Nginx Load Balancing](https://www.digitalocean.com/community/tutorials/how-to-set-up-nginx-load-balancing)

- [How to configure load balancing using Nginx](https://upcloud.com/community/tutorials/configure-load-balancing-nginx/)