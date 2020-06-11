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

Find the best IP for `github.global.ssl.fastly.net`, and `github.com` from [https://www.ipaddress.com](https://link.zhihu.com/?target=https%3A//www.ipaddress.com/)

```
# Speed Up GitHub from China
199.232.69.194 github.global.ssl.fastly.net
140.82.113.4 github.com
```

## Final Solutions

1. Add Buffer

```
git config --global http.postBuffer 524288000
```

2. Set proxy "global" for proxy client.