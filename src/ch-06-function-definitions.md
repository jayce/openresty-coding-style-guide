# 函数定义

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#function-definitions)

C 函数定义的风格不同于声明（见[函数声明](./ch-05-function-declarations.md)）。第一行由返回类型独占，第二行是函数名称及参数列表，第三行由左花括号独占。以下是 NGINX 核心的例子：

```c
ngx_int_t
ngx_http_compile_complex_value(ngx_http_compile_complex_value_t *ccv)
{
    ...
}
```

> **注意**：参数列表 `(` 字符周围没有空格，并且这三行是没有缩进的。

如果参数列表太长，超过 80 个字符宽度限制，应将它拆分成单独的行，每行保持 4 空格缩进。以下是 NGINX 核心的例子：

```c
ngx_int_t
ngx_http_complex_value(ngx_http_request_t *r, ngx_http_complex_value_t *val,
    ngx_str_t *value)
{
    ...
}
```

如果函数返回类型是个指针，应在类型与 `*` 字符之间加入空格，像这样：

```c
static char *
ngx_http_core_pool_size(ngx_conf_t *cf, void *post, void *data)
{
    ...
}
```