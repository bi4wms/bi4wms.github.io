---
layout: categories
icon: fas fa-stream
order: 5
---

<style>
/* 强制隐藏左侧导航栏中的 Tags 项（支持 Light 和 Dark 模式） */
.sidebar .nav-link[href*="categories"],
.sidebar a[href*="/categories/"],
.sidebar li:has(a[href*="/categories"]) {
    display: none !important;
}

/* 如果上面不行，尝试这个更强的版本 */
#sidebar .nav-pills .nav-link[href$="/categories/"],
#sidebar .nav-link[title="categories"],
#sidebar a[title="categories"] {
    display: none !important;
}
</style>
