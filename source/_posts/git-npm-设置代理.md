---
title: git npm 设置代理
date: 2020-02-07 08:31:23
categories: 开发常用
tags:
  - git
  - node
  - 代理设置
photo:
---

### Git 代理设置

#### 1. https 访问

``` bash
# 对全部网址生效
git config --global http.proxy 'socks5://127.0.0.1:1080'
git config --global https.proxy 'socks5://127.0.0.1:1080'
# 设置仅对 github.com 生效
git config --global http.https://github.com.proxy 'socks5://127.0.0.1:1080'
```

<!-- more -->

#### 2. ssh 访问

以macOS为准，需要修改 ~/.ssh/config 文件，添加下面的内容。如果没有这个文件的话则新建（仅对github.com设置代理）

``` bash
Host github.com
  User git
  ProxyCommand nc -v -x 127.0.0.1080 %h %p
```

如果是 Windows 系统，则修改用户家目录下的 .ssh\config，没有这个文件就新建（仅对github.com设置代理）

``` bash
Host github.com
  User git
  # -S 代表使用的是 socks5 代理，-H 是 http 代理
  ProxyCommand connect -S 127.0.0.1080 %h %p
```

### Git 取消代理

#### 1. 取消 http 代理

``` bash
# 取消全部的
git config --global --unset http.proxy
git config --global --unset https.proxy
# 取消github.com的
git config --global --unset http.https://github.com.proxy
```

#### 2. 取消 ssh 代理

编辑 .ssh/config 文件，把上面新添加进去的内容删掉

### npm 代理设置

#### 1. http 代理

``` bash
# 没有用户密码的代理
npm config set proxy 'http://127.0.0.1:8080'
npm config set https-proxy 'http://127.0.0.1:8080'

# 有用户密码的代理
npm config set proxy 'http://username:password@127.0.0.1:8080'
npm confit set https-proxy 'http://username:password@127.0.0.1:8080'
```

#### 2. socks5 代理

``` bash
# 假设本地socks5代理端口为8086
# 首先安装转换工具
npm install -g http-proxy-to-socks
# 然后使用这个工具监听8080端口,支持http代理，然后所有8080的http代理数据都将转换成socks的代理数据发送到8081上
hpts -s localhost:8086 -p 8080
# 最后设置npm代理为8080
npm config set proxy 'http://127.0.0.1:8080'
npm config set https-proxy 'http://127.0.0.1:8080'
```

### npm 取消代理

``` bash
npm config delete proxy
npm config delete https-proxy
```

{% blockquote %}
参考链接: 
1. [https://gist.github.com/laispace/666dd7b27e9116faece6](https://gist.github.com/laispace/666dd7b27e9116faece6)
2. [https://www.tapme.top/blog/detail/20191010/](https://www.tapme.top/blog/detail/20191010/)
{% endblockquote %}