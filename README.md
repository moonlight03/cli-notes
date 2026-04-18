# 命令行速查（GitHub Pages）

站点内容在 `docs/`，适配 GitHub Pages（`main` 分支 + `/docs` 目录发布）。

## 发布步骤（在你自己的终端里执行）

1) 初始化并提交
```bash
git init
git add -A
git commit -m "Add CLI notes site"
```

2) 创建远程仓库并推送（示例仓库名：`cli-notes`）
```bash
git branch -M main
git remote add origin git@github.com:<GITHUB_USER>/cli-notes.git
git push -u origin main
```

3) 打开仓库 Settings → Pages

- Build and deployment → Source：选择 `Deploy from a branch`
- Branch：选择 `main`，Folder 选择 `/docs`

保存后等待 1–3 分钟，Pages 会给出访问地址。

## 本地预览（可选）
已安装 Ruby/Jekyll 的情况下：
```bash
cd docs
bundle exec jekyll serve
```

