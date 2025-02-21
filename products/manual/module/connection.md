---
sidebar_position: 7
---

# 本地模式与远程模式

由于 Yak 核心引擎与 Yakit 的分离式安装，Yakit 仅仅作为一个客户端而存在，Yakit 的使用理所当然就应该存在两种模式

1. 本地模式：默认启动一个随机端口的 `yak grpc` 服务器
1. 远程模式：`yak grpc` 可以启动在任何平台 / 任何网络位置，包括
    1. 远端托管主机 ECS/VPS
    1. 本地个人 PC
    1. 内网环境

与此同时，yak grpc 启动参数支持设置 `--tls` 与 `--secret` 以实现一些远程连接的安全需求。

同时 Yakit 既然作为客户端，在远程模式和本地模式下，出了网络延迟之外，其他的使用体验应该是完全一致的。

## 本地模式

下载启动即可，不多做概述

## 远程模式：启动你自己的 `yak grpc`

当我们在命令行工具中输入：`yak grpc -h`，将会看到如下帮助信息

```
NAME:
   yak grpc - 启动 GRPC 服务器

USAGE:
   yak grpc [command options] [arguments...]

OPTIONS:
   --host value         启动 GRPC 服务器的本地地址 (default: "localhost")
   --port value         启动 GRPC 的端口 (default: 8087)
   --secret value       启动 GRPC 的认证口令
   --tls
   --gen-tls-crt value  (default: "build/")
```

一般来说，我们看到上述信息的基础参数就已经知道如何使用了。比如：
```
yak grpc --host 0.0.0.0 --port 8087 --secret youR-aw0some-PA5s --tls
```
启动GRPC服务器后，在本地用yakit客户端进行连接

![](/img/products/yakit/connection-1.png)

![](/img/products/yakit/connection-2.png)

![](/img/products/yakit/connection-3.png)

但是，我们仍然有一些解释的点需要告诉大家

:::danger 公网使用记得使用 TLS：保障通信不被窃听

`--tls` 选项可以显著降低通信劫持的风险

:::

:::danger 设置密码，保证私密性

`--secret youR-aw0some-PA5s` 这个参数可以为你的 gRPC 服务器增加一个简单的密码认证

原理是：
> gRPC 是基于 HTTP2 协议的全双通通信协议
>
> secret 参数将会设置服务器验证 gRPC 通信每一个请求/响应/流请求的 HTTP Headers 中的 authorization 头
>
> 这个验证在 Yakit 和 Yak 中是配套的，用户并不需要额外设置即可使用。

:::
权限切换：在使用某些功能时，如果不是以root或者管理员权限启动会出现报错的情况，权限的切换如下图所示

![](/img/products/yakit/connection-4.png)
