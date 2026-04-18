---
title: tmux
---

# tmux（终端复用/分屏）

## 常用概念
- `session`：一组工作环境
- `window`：一个标签页
- `pane`：分屏后的单元格

## 常用命令
```bash
tmux              # 新建会话
tmux ls           # 列出会话
tmux a            # 重新连接最近会话
tmux a -t <ID>    # 连接指定会话
```

## 常用快捷键（默认前缀 Ctrl+b）
- `Ctrl+b` 然后 `%`：左右分屏
- `Ctrl+b` 然后 `"`：上下分屏
- `Ctrl+b` 然后方向键：切换 pane
- `Ctrl+b` 然后 `z`：当前 pane 全屏/取消
- `Ctrl+b` 然后 `d`：detach（后台挂起会话）
- `Ctrl+d`：关闭当前 shell（可能导致 pane/window/session 结束）

## 复制模式（最常用）
- `Ctrl+b` 然后 `[`：进入复制模式（可滚动/选择）
- 选择内容后复制到 tmux 缓冲区
- `Ctrl+b` 然后 `]`：粘贴缓冲区
