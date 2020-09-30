# Speed Up GitHub Connection

Content

- Update Git Config
- Using Proxy
- Update hosts
- Final Solutions



## Update Git Config

```
git config --global http.postBuffer 524288000
```

## Using Proxy

```
# Set Proxy
git config --global http.https://github.com.proxy https://127.0.0.1:10809
git config --global https.https://github.com.proxy https://127.0.0.1:10809

# Unset Proxy
git config --global --unset http.proxy
git config --global --unset https.proxy
# or
git config --global --unset http.https://github.com.proxy
git config --global --unset https.https://github.com.proxy
```

## Update hosts

1. Get IP

Find the best IP for `github.global.ssl.fastly.net`, and `github.com` from https://www.ipaddress.com

2. Update hosts

hosts on Windows: `C:\Windows\System32\drivers\etc\hosts`

hosts on Linux: `/etc/hosts`

```
# Speed Up GitHub from China
199.232.69.194 github.global.ssl.fastly.net
140.82.114.4 github.com
```

3. Update DNS

Windows

```
ipconfig /flushdns
```

Linux

```
sudo /etc/init.d/networking restart
```

References: [git clone速度太慢的解决办法](https://www.cnblogs.com/lywJ/p/11038611.html)

## Final Solutions

1. Add Buffer

```
git config --global http.postBuffer 524288000
```

2. Update hosts

I have not use proxy client.