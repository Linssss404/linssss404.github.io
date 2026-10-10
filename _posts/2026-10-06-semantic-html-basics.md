---
layout: post
title: 静态网页入门：先写对结构，再谈样式
date: 2026-10-06
excerpt: 回头整理我刚学 HTML 时最容易忽略的事——语义化的标签到底有什么用。
tags:
  - 前端
  - HTML
---

刚开始写网页的时候，我最关心的是「怎么让它看起来像样」。后来才发现，结构没写对，样式越写越难维护。

## 先想清楚内容是什么

一个页面里的东西其实只有几类：标题、段落、列表、链接、图片、区块。对应到 HTML，就是 `h1`–`h6`、`p`、`ul`/`ol`、`a`、`img` 和 `section`/`article`。

我给自己定的第一条规则是：**不要因为「想要某个外观」去选标签，要因为「内容是什么」去选标签。**

- 想加粗强调 → 用 `strong`，不是把 `span` 调成粗体
- 想分组内容 → 用 `section` 加 `aria-labelledby`，不是套一堆 `div`
- 想做一个按钮 → 能跳转就用 `a`，能提交就用 `button`，别用 `div` 加点击事件

## 结构写对之后，样式会变简单

给区块加上清楚的类名，CSS 就能写得很短：

```html
<section class="card">
  <h2>文章标题</h2>
  <p>一句话摘要。</p>
  <a class="card-link" href="/posts/example/">阅读文章 →</a>
</section>
```

```css
.card { padding: 24px; border: 1px solid var(--line); border-radius: 18px; }
.card h2 { margin: 0 0 8px; }
```

不需要深层嵌套选择器，也不需要 `!important`。

## 我踩过的两个坑

1. **一个页面写了三个 `h1`**。标题层级是文档的大纲，跳级会让读屏软件和搜索引擎都困惑。现在我坚持整页只有一个 `h1`。
2. **图片不写 `alt`**。图片加载失败时，`alt` 是唯一能告诉别人这里是什么的东西。

结构是地基。地基平了，后面的 CSS 才好往上砌。
