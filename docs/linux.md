---
title: Linux
---

# Linux/运维杂项

## 进程
```bash
pkill -f python
```

## 磁盘与目录大小
```bash
du -h --max-depth=1
du -sh <DIR>
du -ah | sort -h
```

## 挂载（示例）
```bash
mount /dev/<DISK> /mnt/
```

NFS（示例，参数按实际环境调整）：
```bash
mount -t nfs -o vers=3,nolock,proto=tcp,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2 \
  <NFS_SERVER>:/<EXPORT> /public
```

## 网络（示例）
```bash
sudo dhclient <IFACE>
```

## 用户/权限（示例）
> 下面命令会改动系统用户与权限，仅在你明确知道含义并有权限的服务器上使用。
```bash
useradd -d /public/localUsers/<USER> -m <USER>
chown -R <USER>:<USER> /public/localUsers/<USER>
chmod 760 /public/localUsers/<USER>
gpasswd -a <USER> docker
```
