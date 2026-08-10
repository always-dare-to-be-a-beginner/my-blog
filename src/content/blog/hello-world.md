---
title: "你好，世界"
description: "这是用 Astro + Cloudflare Pages 在本机一键支棱起来的第一篇博客。"
pubDate: 'Aug 10 2026'
---

这是我的第一篇博客，由 **小王八** 帮老板在本机直接跑起来的。

## 怎么写一篇新文章

只要往 `src/content/blog/` 丢一个 `.md` 文件，写好开头的 frontmatter（标题、日期、描述），保存后网站就会自动更新。

```md
---
title: "文章标题"
date: 2026-08-10
description: "一句话摘要"
---

正文用 Markdown 随便写。
```

## 整体链路

- **写**：本地 Markdown
- **存**：GitHub
- **建+托**：Cloudflare Pages 自动构建分发
- **访问**：自定义域名（HTTPS）

成本只有域名钱，其余全免费。完事，开写吧。
