---
title: 'Hexo常见问题'
date: 2025-03-29 18:19:43
tags: hexo
Q1: 如何更新博客内容？
在本地用 hexo new "文章标题" 创建新文章

编辑 source/_posts/文章标题.md

运行 hexo clean && hexo generate 重新生成

推送代码到 GitHub：

bash
复制
git add .
git commit -m "更新文章"
git push origin main
Vercel 会自动检测更新并重新部署（无需手动操作）

Q2: 如何更换主题？
在 Hexo 主题商店 选一个主题（如 Butterfly）

在终端运行：

bash
复制
git clone https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
修改 _config.yml：

yaml
复制
theme: butterfly
推送代码到 GitHub，Vercel 会自动更新

🎯 总结
✅ GitHub 存放代码 + Vercel 自动部署 = 免费、快速、稳定的 Hexo 博客！
你现在已经拥有一个可访问的博客了，接下来可以：

写文章（hexo new "标题"）

换主题（修改 _config.yml）

绑定自己的域名（可选）
