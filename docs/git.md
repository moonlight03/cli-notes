---
title: Git
---

# Git（常用命令）

## 基本概念（速记）
- 工作区：当前目录里的文件
- 暂存区：`git add` 后等待提交的集合
- 版本库：提交历史与对象（`.git`）

## 初始配置
```bash
git config --global user.name "<NAME>"
git config --global user.email "<EMAIL>"
```

## 仓库与提交
```bash
git init
git status
git add -A
git commit -m "msg"
```

## 分支与同步（常用）
```bash
git branch
git switch -c <branch>
git switch <branch>
git pull --rebase
git push -u origin <branch>
```
