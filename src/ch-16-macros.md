# 宏

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#macros)

宏定义要求在指令 `#define` 之后有一个空格符，而在定义主体部分之前至少有 2 个空格符。例如：

```C
#define F(x, y, z)  ((z) ^ ((x) & ((y) ^ (z))))
```

有时会在定义主体部分之前使用更多空格，目的是为了将多个密切相关的宏定义垂直对齐，如：

```C
#define NGX_RESOLVE_A         1
#define NGX_RESOLVE_CNAME     5
#define NGX_RESOLVE_PTR       12
#define NGX_RESOLVE_MX        15
#define NGX_RESOLVE_TXT       16
#define NGX_RESOLVE_AAAA      28
#define NGX_RESOLVE_SRV       33
#define NGX_RESOLVE_DNAME     39
#define NGX_RESOLVE_FORMERR   1
#define NGX_RESOLVE_SERVFAIL  2
```

对于跨越多行的宏定义，应该把连续字符 `\` 纵向对齐成一条直线，如：

```C
#define ngx_conf_init_value(conf, default)                                   \
    if (conf == NGX_CONF_UNSET) {                                            \
        conf = default;                                                      \
    }
```

我们推荐将 `\` 放在第 78 个字符的位置，尽管 NGINX 核心有时没这么做。