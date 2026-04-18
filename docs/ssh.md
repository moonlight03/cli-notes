---
title: SSH
---

# SSH（远程登录/免密/执行命令）

## 登录
```bash
ssh <USER>@<HOST>
ssh <USER>@<HOST> -p <PORT>
```

首次连接会提示主机指纹，确认后会写入 `~/.ssh/known_hosts`。

## 配置别名（推荐）
编辑 `~/.ssh/config`：
```sshconfig
Host myserver
  HostName <HOST>
  User <USER>
  Port 22
```
之后即可：
```bash
ssh myserver
```

## 生成密钥与免密登录
```bash
ssh-keygen -t ed25519
ssh-copy-id myserver
```

## 远程执行命令
```bash
ssh myserver 'ls -la'
ssh myserver 'for i in {1..3}; do echo $i; done'
```

单引号会在远端解释变量；双引号会先在本地做部分展开（容易踩坑，除非你很确定）。
