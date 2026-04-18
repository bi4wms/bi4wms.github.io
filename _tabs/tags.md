---
layout: tags
title: Tags
icon: fas fa-tags
order: 7
---

<style>
/* 最高优先级强制隐藏 Tags 导航项 */
#sidebar .nav-link[href*="/tags"],
.sidebar .nav-link[href*="/tags"],
#nav .nav-link[href*="/tags"],
.nav-pills .nav-link[href*="/tags"],
.sidebar li a[href*="/tags"],
#sidebar li a[href*="/tags"] {
    display: none !important;
}

#sidebar .nav-item:has(a[href*="/tags"]),
.sidebar .nav-item:has(a[href*="/tags"]) {
    display: none !important;
}

/* 隐藏图标和可能残留的项 */
.sidebar .fa-tags,
#sidebar .fa-tags {
    display: none !important;
}
</style>
