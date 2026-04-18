---
title: Docker
---

# Docker（镜像/容器常用操作）

## 镜像
```bash
docker images
docker tag <IMAGE_ID> <REPO>:<TAG>
docker rmi -f <IMAGE_ID>
```

导入/导出：
```bash
docker load -i <image>.tar
docker save <REPO>:<TAG> > <image>.tar
```

从运行中的容器生成镜像（谨慎使用，确保不包含密钥/数据）：
```bash
docker commit <CONTAINER_ID> <REPO>:<TAG>
```

## 容器
```bash
docker ps
docker ps -a
docker start <CONTAINER_ID>
docker stop <CONTAINER_ID>
docker kill <CONTAINER_ID>
docker rm -f <CONTAINER_ID>
docker rename <OLD_NAME> <NEW_NAME>
```

进入容器：
```bash
docker exec -it <CONTAINER_ID> /bin/bash
```

## GPU/挂载（示例）
```bash
docker run --gpus all --shm-size 8G -ti -d \
  -v <HOST_DIR>:/mnt \
  <IMAGE_ID> /bin/bash
```

## Jupyter（示例）
```bash
nohup jupyter notebook --allow-root &
```
