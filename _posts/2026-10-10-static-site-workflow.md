---
layout: post
title: 我把博客做成了纯静态网站
date: 2026-10-10
excerpt: 不装 Node.js，不打包，不引外部 CDN——只靠 Markdown 和一个 GitHub Actions。
tags:
  - 建站
  - GitHub Pages
---

在动手之前我列过一堆技术选型：要不要上框架？要不要建个构建流程？最后我选了一条最省事的路——**纯静态**。

## 最终的技术栈

```text
Markdown 文章
      ↓
Jekyll（在 GitHub Actions 上运行）
      ↓
HTML 页面
      ↓
GitHub Pages
```

就这样四步。

## 为什么不做更复杂的

- **不需要本地环境**。这台电脑上没装 Node.js、npm 或 Python，写文章只需要一个文本编辑器。
- **没有构建负担**。我不需要记得「先跑构建命令再部署」，`git push` 就是发布。
- **页面足够快**。服务器直接返回生成好的 HTML，浏览器不用等 JavaScript 把内容渲染出来。
- **出问题好排查**。整个站点的样式只有一个 CSS 文件，没有依赖树的层层嵌套。

## 我每天实际要做的

1. 在 `_posts/` 里新建 `YYYY-MM-DD-title.md`
2. 开头写好 Front Matter（标题、日期、摘要、标签）
3. 用 Markdown 写正文
4. 提交并推送

GitHub Actions 会检测到推送，自动用 Jekyll 把 Markdown 编译成 HTML，再发布到 Pages。整个过程我不需要碰服务器。

## 一句提醒

仓库里的 `index.html` 是 Jekyll 的模板源码，直接双击打开是看不到最终效果的——它需要在构建时才能拿到文章列表。所以本地看效果不是必须的，推送后等 Action 跑完再看就行。

工具越少，注意力越能留在写作上。这就是我选择纯静态的原因。
