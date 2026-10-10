---
layout: post
title: Flexbox 与 Grid 的分工：我现在的判断标准
date: 2026-10-09
excerpt: 一维排列用 Flexbox，二维布局用 Grid，这条经验帮我省了很多反复试错。
tags:
  - 前端
  - CSS
  - 布局
---

刚学布局时我总在这两者之间犹豫：都能排，用哪个？用了几个月之后，我总结出一条简单的判断标准。

## 一维就用 Flexbox

当内容是**排成一行或一列**的，用 Flexbox：

```css
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}
```

导航栏、按钮组、卡片内部那一行「日期 · 标签」，全都是这类场景。

## 二维就用 Grid

当内容需要**同时控制行和列**的，用 Grid：

```css
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 18px;
}
```

想要「一行放三张卡片，窄屏自动变一列」，Grid 加一个媒体查询就够了：

```css
@media (max-width: 760px) {
  .cards { grid-template-columns: 1fr; }
}
```

## 我的判断流程

1. 内容只有一行或一列 → **Flexbox**
2. 需要对齐成网格、或者要跨行跨列 → **Grid**
3. 还在犹豫 → 先用 Flexbox，等发现要控制第二维再换 Grid

## 一个容易忘记的点

`gap` 这两个布局都支持，比用 `margin` 手动推开子元素干净得多——不会再出现最后一个元素多出一块外边距的问题。

不用追求一次写对。布局本来就是试着试着才清楚的过程。
