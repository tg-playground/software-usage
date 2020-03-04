# V2ray Note

Content

- Installation
- Configuration

## Installation

### Linux 安装脚本

```bash
bash <(curl -L -s https://install.direct/go.sh)
```

配置文件：`/etc/v2ray/config.json`

Systemd service：`/etc/systemd/system/v2ray.service`

控制 V2Ray 的运行：service v2ray start|stop|status|reload|restart|force-reload 

## Configuration

### Basic Configuration Example

Client Configurations

```json
{
  "inbounds": [{
    "port": 1080,  // SOCKS 代理端口，在浏览器中需配置代理并指向这个端口
    "listen": "127.0.0.1",
    "protocol": "socks",
    "settings": {
      "udp": true
    }
  }],
  "outbounds": [{
    "protocol": "vmess",
    "settings": {
      "vnext": [{
        "address": "server", // 服务器地址，请修改为你自己的服务器 ip 或域名
        "port": 10086,  // 服务器端口
        "users": [{ "id": "b831381d-6324-4d53-ad4f-8cda48b30811" }]
      }]
    }
  },{
    "protocol": "freedom",
    "tag": "direct",
    "settings": {}
  }],
  "routing": {
    "domainStrategy": "IPOnDemand",
    "rules": [{
      "type": "field",
      "ip": ["geoip:private"],
      "outboundTag": "direct"
    }]
  }
}
```



Server Configurations

```json
{
  "inbounds": [{
    "port": 10086, // 服务器监听端口，必须和上面的一样
    "protocol": "vmess",
    "settings": {
      "clients": [{ "id": "b831381d-6324-4d53-ad4f-8cda48b30811" }]
    }
  }],
  "outbounds": [{
    "protocol": "freedom",
    "settings": {}
  }]
}
```

Conditions：

- 服务器的配置中需要确保 `id` 和端口与客户端一致
- 客户端的 outbounds port 和 服务端的 inbounds port 一致。 

### Configuration Format

```
{
  "log": {}, # 日志配置，表示 V2Ray 如何输出日志。
  "api": {}, # 内置的远程控置 API，详见远程控制配置。
  "dns": {}, # 内置的 DNS 服务器，若此项不存在，则默认使用本机的 DNS 设置。详见DNS 配置
  "stats": {}, # 当此项存在时，开启统计信息。
  "routing": {}, # 路由配置
  "policy": {}, # 本地策略可进行一些权限相关的配置，详见本地策略
  "reverse": {}, # 反向代理配置。
  "inbounds": [], # 一个数组，每个元素是一个入站连接配置。
  "outbounds": [], # 一个数组，每个元素是一个出站连接配置。列表中的第一个元素作为主出站协议。当路由匹配不存在或没有匹配成功时，流量由主出站协议发出。
  "transport": {} # 用于配置 V2Ray 如何与其它服务器建立和使用网络连接。详见底层传输配置
}
```

### 协议：VMess

[VMess](https://v2ray.com/developer/protocols/vmess.html) 是一个加密传输协议，它分为入站和出站两部分，通常作为 V2Ray 客户端和服务器之间的桥梁。

VMess 依赖于系统时间，请确保使用 V2Ray 的系统 UTC 时间误差在 90 秒之内，时区无关。在 Linux 系统中可以安装`ntp`服务来自动同步系统时间。

VMess 的配置分为两部分，`InboundConfigurationObject`和`OutboundConfigurationObject`，分别对应入站和出站协议配置中的`settings`项。

`OutboundConfigurationObject`

```
{
  "vnext": [
    {
      "address": "127.0.0.1",
      "port": 37192,
      "users": [
        {
          "id": "27848739-7e62-4138-9fd3-098a63964b6b",
          "alterId": 4,
          "security": "auto",
          "level": 0
        }
      ]
    }
  ]
}
```

### 本地策略配置

本地策略可以配置一些用户相关的权限，比如连接超时设置。V2Ray 处理的每一个连接，都对应到一个用户，按照这个用户的等级（level）应用不同的策略。本地策略可按照等级的不同而变化。

### 路由功能配置

V2Ray 内建了一个简单的路由功能，可以将入站数据按需求由不同的出站连接发出，以达到按需代理的目的。这一功能的常见用法是分流国内外流量，V2Ray 可以通过内部机制判断不同地区的流量，然后将它们发送到不同的出站代理。

### DNS 服务器配置

V2Ray 内置了一个 DNS 服务器，其有两大主要用途：根据域名的解析IP匹配路由规则，以及像传统的DNS功能，解析目标地址进行连接。

由此 DNS 服务器所发出的 DNS 查询请求，会自动根据路由配置进行转发，无需额外配置。

### Mux 多路复用配置

Mux 功能是在一条 TCP 连接上分发多个 TCP 连接的数据。实现细节详见[Mux.Cool](https://v2ray.com/developer/protocols/muxcool.html)。Mux 是为了减少 TCP 的握手延迟而设计，而非提高连接的吞吐量。使用 Mux 看视频、下载或者测速通常都有反效果。Mux 只需要在客户端启用，服务器端自动适配。

### 远程控制配置（API配置）

V2Ray 中可以开放一些 API 以便远程调用。这些 API 都基于 [gRPC](https://grpc.io/)。

当远程控制开启时，V2Ray 会自建一个出站代理，以`tag`配置的值为标识。用户必须手动将所有的 gRPC 入站连接通过[路由](https://v2ray.com/chapter_02/03_routing.html)指向这一出站代理。

### 统计信息配置

V2Ray 提供了一些关于其运行状况的统计信息。

### 反向代理配置

反向代理是一个 V2Ray 的附加功能，可以把服务器端的流量向客户端转发，即逆向流量转发。

> 反向代理功能在 V2Ray 4.0+ 可用。目前处于测试阶段，可能会有一些问题。

### 底层传输配置

底层传输方式（transport）是当前 V2Ray 节点和其它节点对接的方式。底层传输方式提供了稳定的数据传输通道。通常来说，一个网络连接的两端需要有对称的传输方式。比如一端用了 WebSocket，那么另一个端也必须使用 WebSocket，否则无法建立连接。

底层传输（transport）配置分为两部分，一是全局设置([TransportObject](https://v2ray.com/chapter_02/05_transport.html#transportobject))，二是分协议配置([StreamSettingsObject](https://v2ray.com/chapter_02/05_transport.html#streamsettingsobject))。分协议配置可以指定每个单独的入站出站协议用怎样的方式传输。通常来说客户端和服务器对应的出站入站协议需要使用同样的传输方式。当分协议传输配置指定了一种传输方式，但没有填写其设置时，此传输方式会使用全局配置中的设置。

`TransportObject`对应配置文件的`transport`项。

```javascript
{
  "tcpSettings": {},
  "kcpSettings": {},
  "wsSettings": {},
  "httpSettings": {},
  "dsSettings": {},
  "quicSettings": {}
}
```

### 环境变量配置



## References

V2ray

- [Project V](https://v2ray.com/)
- [v2ray manual](https://github.com/v2ray/manual)
- [新 V2Ray 白话文指南](https://guide.v2fly.org/)

Limit network speed

- [V2Ray对抗运营商QoS限速](https://steemit.com/cn/@syt/v2ray-qos)
- [[科普\] 为什么你用的VPN网速那么慢？](https://fangeqiang.com/1378.html)