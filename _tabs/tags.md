---
layout: tags
title: Tags
icon: fas fa-tags
order: 6
---

<style>
/* 最高优先级强制隐藏左侧导航栏中的 Tags（针对 Chirpy 实际结构） */
#sidebar .nav-link[href*="/tags"],
#sidebar a[href*="/tags"],
.sidebar .nav-link[href*="/tags"],
.sidebar a[href*="/tags"],
.nav-pills .nav-link[href*="/tags"],
#sidebar li:has(a[href*="/tags"]),
.sidebar li:has(a[href*="/tags"]) {
    display: none !important;
}

/* 隐藏带图标的 Tags 项 */
#sidebar .nav-link i.fa-tags,
.sidebar .nav-link i.fa-tags,
#sidebar .fa-tags,
.sidebar .fa-tags {
    display: none !important;
}

/* 防止隐藏后留下多余空白或间距 */
#sidebar li:has(a[href*="/tags"]) {
    margin: 0 !important;
    padding: 0 !important;
    height: 0 !important;
    overflow: hidden !important;
}
</style>
