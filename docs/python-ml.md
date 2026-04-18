---
title: Python & 机器学习环境
---

# Python & 机器学习环境（CUDA/Conda/Pip）

## 常用环境变量
```bash
export CUDA_VISIBLE_DEVICES=0,1,2,3
export CUDA_HOME=/usr/local/cuda-11.7
```

敏感信息（API Token 等）不要写进仓库；用环境变量或密钥管理工具注入：
```bash
export REPLICATE_API_TOKEN="<TOKEN>"
```

## conda 镜像源（示例）
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
conda config --set show_channel_urls yes
conda config --show channels
```

## pip/系统依赖（示例）
```bash
pip install --upgrade pyopengl==3.1.4
apt-get install -y libglfw3-dev libgles2-mesa-dev libglib2.0-0 libosmesa6-dev
```

（某些环境里需要修复 `libstdc++` 软链，路径按实际 conda env 调整）
```bash
ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6 \
  <CONDA_PREFIX>/lib/libstdc++.so.6
```

## 常见 Git 克隆（示例）
```bash
git clone --recursive <REPO_URL>
git clone --recursive --branch <BRANCH> --single-branch <REPO_URL>
```

## PyOpenGL（OSMesa 后端示例）
```python
import os
os.environ["PYOPENGL_PLATFORM"] = "osmesa"
```
