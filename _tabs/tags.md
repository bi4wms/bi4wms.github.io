---
layout: tags
icon: fas fa-tags
order: 7
---

<style>
/* 强制隐藏左侧导航栏中的 Tags（最高优先级） */
.sidebar .nav-link[href*="/tags"],
.sidebar a[href*="/tags"],
#sidebar a[href*="/tags"],
.nav-pills .nav-link[href*="/tags"],
li:has(a[href*="/tags"]) {
    display: none !important;
}

/* 同时兼容可能的不同结构 */
#sidebar .nav-item a[title="Tags"],
.sidebar .nav-item:has(.fa-tags),
.sidebar li a[href$="/tags/"] {
    display: none !important;
}
</style>
