# Linssss 的个人博客

一个纯静态的 Jekyll 个人博客，部署在 GitHub Pages 上。**不需要** Node.js、npm、React、Vue 或任何构建工具：文章用 Markdown 写，由 GitHub Actions 上的 Jekyll 编译成 HTML。

- 博客网址：https://linssss404.github.io/
- 仓库：https://github.com/Linssss404/linssss404.github.io

## 文件结构

```text
_config.yml                 站点标题、描述、网址、作者信息
index.html                  首页（Hero、文章列表、项目卡片）
about.md                    关于页
assets/style.css            全站样式（配色变量集中在 :root）
_layouts/default.html       全站外框：导航与页脚
_layouts/post.html          文章页布局
_posts/YYYY-MM-DD-title.md  所有文章
.github/workflows/pages.yml 自动构建并部署到 GitHub Pages
```

## 写一篇新文章

在 `_posts/` 中新建文件，文件名必须是：

```text
YYYY-MM-DD-title.md
```

开头保留 Front Matter：

```yaml
---
layout: post
title: 文章标题
date: 2026-10-10
excerpt: 一句话摘要，会显示在首页卡片上
tags:
  - 前端
---
```

第二个 `---` 之后直接写 Markdown 正文。标题、段落、列表、链接、引用、代码块都可以用。

文章的网址由 `_config.yml` 里的 `permalink: /posts/:title/` 决定，例如 `_posts/2026-10-10-static-site-workflow.md` 会发布在 `/posts/static-site-workflow/`。

## 修改个人信息与配色

| 想改什么 | 改哪里 |
| --- | --- |
| 站点标题、描述、作者、邮箱 | `_config.yml` |
| 首页自我介绍、按钮、项目卡片 | `index.html` |
| 关于页内容 | `about.md` |
| 页脚与导航里的链接 | `_layouts/default.html` |
| 主色、辅助色、字体、圆角 | `assets/style.css` 顶部的 `:root` 变量 |

配色只需要改 `:root` 里的几个变量，全站会自动跟着变：

```css
:root {
  --accent: #4f5bd5;       /* 主色：分隔线、标签、链接 */
  --accent-dark: #37409e;  /* 主色深版：小标题、hover */
  --accent-2: #0f8f7d;     /* 辅助色：关于页竖线 */
  --ink: #1b2130;          /* 正文 */
  --muted: #667085;        /* 次要文字 */
  --paper: #ffffff;        /* 卡片背景 */
}
```

## 发布流程

```text
本地改 Markdown / HTML / CSS
        ↓
git add . && git commit -m "说明"
        ↓
git push
        ↓
GitHub Actions 自动运行 Jekyll
        ↓
网站更新到 https://linssss404.github.io/
```

推送后到仓库的 **Actions** 标签页可以看到 `Build and deploy Jekyll site` 是否成功，约 1 分钟完成。

## 本地预览说明

`index.html` 是 Jekyll 模板源码，直接双击打开看不到最终效果（文章列表需要构建时才能生成）。本地预览不是必须的 —— 推送到 GitHub 后由 Actions 完成构建即可。

## 注意

- 仓库必须保持 **Public**，否则免费账号无法使用 GitHub Pages。
- Pages 的 Source 需要设为 **GitHub Actions**（首次部署时 Actions 会自动开启）。
- 本仓库不引入任何外部 CDN、前端框架或构建工具。
