---
title: SSH 免密登录配置
top: false
cover: false
toc: true
date: 2020-02-04 10:06:49
password:
summary:
categories: "Linux 基础"
tags: "SSH"
---
### 环境说明

客户端机器（本地）: A
服务端机器（远程）: B
服务器IP: 192.168.1.2
服务器用户: root    登录密码: 123456

<!-- more -->

### 客户端生成SSH的公钥和私钥

``` bash
ssh-keygen -t rsa
```

这时候第一个提示是确认密钥文件的保存路径，一般直接按回车（此时的密钥文件会保存在 当前用户的家目录/.ssh/）
第二、三个提示是让你输入一个密钥的密码，目前可以直接跳过，直接按回车

### 上传公钥到服务器

``` bash
ssh-copy-id root@192.168.1.2
```

这时候会提示要你输入 root 用户的密码，直接输入 123456 ，然后按回车

### 验证

``` bash
ssh root@192.168.1.2
```

### 配置别名登录

在 A 创建 ~/.ssh/config 文件（如有则直接编辑）

``` bash
touch ~/.ssh/config
```

编辑 ~/.ssh/config ，在文件末尾添加以下内容后保存

{% code %}
Host B
  HostName 192.168.1.2
  Port 22
  User root
  IdentityFile ~/.ssh/id_rsa
{% endcode %}

### 别名登录
``` bash
ssh B
```