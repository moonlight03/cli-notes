---
title: Docker
---

# Docker（镜像/容器常用操作）

## 我常用的镜像/容器记录（保留原始编号）

> 这些 ID/名称来自你的原始笔记，用于快速定位环境；按需替换成你当前机器上的实际值。

容器（示例）：
```bash
docker ps
docker ps -a

# 进入
docker exec -it 9a3da8b7a829 /bin/bash
docker exec -it fa5f7ee0259f /bin/bash
docker exec -it da2212b210c7 /bin/bash
docker exec -it d46292017381 /bin/bash   # 4090*4 10 lixiang10
docker exec -it 2acddd94905d /bin/bash   # 4090*4 11 lixiang11
docker exec -it be30b783ef89 /bin/bash   # 4090*4 12 lixiang12
docker exec -it 168f3e361844 /bin/bash   # 4090*4 13 lixiang

# 启停/删除/重命名（示例）
docker start e1be6e8cdcc4
docker kill 14cd72952ed6
docker stop 2c7a344ba3b4
docker rm -f 14cd72952ed6
docker rename agitated_wing wufanghao08
```

镜像（示例）：
```bash
docker images
docker tag ce83519912f7 conda:conda
docker rmi -f ac024bd40d34

# 导入/导出
docker load -i qizhuangnode3.tar
docker save lixiang2025815 > lixiang2025815.tar

# 从容器固化镜像
docker commit 2acddd94905d lixiang2025815
```

运行（示例，含 GPU/挂载）：
```bash
docker run --gpus all --shm-size 8G -ti -d -v /public/localUsers/wufanghao08:/mnt ce83519912f7 /bin/bash
docker run --gpus all --shm-size 8G -ti -d -v /public/localUsers/lixiang:/mnt d74c7d8a7d7a /bin/bash
docker run --gpus all --shm-size 8G -ti -d -v /public/localUsers/lixiang11:/mnt be0668c2b26e /bin/bash
docker run --gpus all --shm-size 8G -ti -d -v /public/wu/chenxu:/mnt ce83519912f7 /bin/bash
```

## 备忘：Jupyter/NFS（原笔记）
```bash
nohup jupyter notebook --allow-root &

mount -t nfs -o vers=3,nolock,proto=tcp,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2 \
  192.168.11.10:/mnt/sdata/shumei /public
```

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
