---
title: Hexo博客操作指南
date: 2025-03-29 18:42:35
tags:
---
Q1: 如何更新博客内容？
在本地用 hexo new "Q1: 如何更新博客内容？" 创建新文章

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


Q3: 如何删除文章？
📌 步骤 1：删除文章文件
进入博客目录的 source/_posts/ 文件夹

手动删除对应的 Markdown 文件（如 2024-05-20-old-post.md）

📌 步骤 2：同步到 GitHub 并触发部署
① 提交更改到 Git
bash
复制
# 进入博客根目录
cd my-blog

# 查看被删除的文件（确认文件已从工作区移除）
git status
# 应显示：deleted: source/_posts/2024-05-20-old-post.md

# 添加删除操作到暂存区
git add -u  # 或 git add source/_posts/2024-05-20-old-post.md

# 提交更改
git commit -m "删除旧文章《old-post》"
② 推送到 GitHub
bash
复制
git push origin main
✅ 成功输出示例：

text
复制
Delta compression using up to 8 threads.
Writing objects: 100% (3/3), 312 bytes | 312.00 KiB/s, done.
📌 步骤 3：验证 Vercel/GitHub Pages 更新
等待 1-2 分钟，Vercel/GitHub Pages 会自动检测变更并重新部署

检查线上效果：

访问文章原链接（如 https://你的域名/2024/05/20/old-post/）应返回 404

首页/归档页中该文章消失

⚠️ 注意事项
缓存问题：

如果线上仍能访问已删除的文章：

浏览器强制刷新（Ctrl + Shift + R）

在 Vercel 控制台 清除缓存（Settings → Storage → Clear Build Cache）

Git 历史记录：

文章文件仍会保留在 Git 历史中，如需彻底清除：

bash
复制
git filter-repo --path source/_posts/2024-05-20-old-post.md --invert-paths
git push origin main --force
（⚠️ 谨慎操作，会改写历史记录）