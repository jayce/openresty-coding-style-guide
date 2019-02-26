# 处理内存分配错误

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#allocation-error-handling)

在 NGINX 世界里一直有个好习惯，在任何时候都会检查内存分配失败。像这样：

```C
    sa = ngx_palloc(cf->pool, socklen);
    if (sa == NULL) {
        return NULL;
    }
```

这两条语句经常一起出现，所以我们就没有在分配语句与 `if` 语句之间加空行。

确保不要省略动态内存分配语句后的 `if` 语句。