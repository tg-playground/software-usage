# Web Servers On Linux

**Content**

- Apache httpd
- Nginx



## Apache httpd

Configuration

```
/etc/httpd/conf/httpd.conf
```

Deployment

```
/var/www/html
/var/www/error/404.html
```

Logging

```
/var/log/httpd/access_log
/var/log/httpd/error_log
```



## Nginx

Configuration

```
# server configurations
/etc/nginx/nginx.conf

# proxy configurations
/etc/nginx/conf.d
```

Deployment

```
# debian 
/usr/share/nginx/html
```

Logging 

```
/var/log/nginx/access.log
/var/log/nginx/error.log
```

