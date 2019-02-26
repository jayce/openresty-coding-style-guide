# 全局/静态变量

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#globalstatic-variables)

在局部变量、顶层静态变量定义和声明时，类型符号和变量标识符之间加至少 2 个空格符（包括前导符 `*`）。
以下是些例子：

```C
ngx_uint_t   ngx_http_max_module;


ngx_http_output_header_filter_pt  ngx_http_top_header_filter;
ngx_http_output_body_filter_pt    ngx_http_top_body_filter;
ngx_http_request_body_filter_pt   ngx_http_top_request_body_filter;
```

这同样适用于变量的初始化表达式，如下：

```C
ngx_str_t  ngx_http_html_default_types[] = {
    ngx_string("text/html"),
    ngx_null_string
};
```