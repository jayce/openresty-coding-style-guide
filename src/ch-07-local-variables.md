# 局部变量

在[命名约定](./ch-01-naming-convention.md)中要求局部变量使用更短的名称，类似 `ev`, `clcf` 这样的。它们在定义的时候也有一些要求。

它们应总是写在每个 C 函数定义块开始的位置，且不仅仅只在任意代码块开头，除非为了调试或者有其他特殊要求。还有，它们的变量标识符（除 `*` 前缀字符以外），必须垂直对其。以下是 NGINX 核心的示例：

```C
    ngx_str_t            *value;
    ngx_uint_t            i;
    ngx_regex_elt_t      *re;
    ngx_regex_compile_t   rc;
    u_char                errstr[NGX_MAX_CONF_ERRSTR];
```

请注意 `value`, `i`, `re`, `rc`, `errstr` 这些标识符是如何垂直对其的。前缀 `*` 不计入对其。

有的时候，某些局部变量的定义可能特别长，要与其余变量对其可能会使代码变得丑陋。然后我们在它们之间放一个空行。
在这种情况下，两组定义是不需要垂直对齐的。以下就是这样的例子：

```C
static char *
ngx_http_core_open_file_cache(ngx_conf_t *cf, ngx_command_t *cmd, void *conf)
{
    ngx_http_core_loc_conf_t *clcf = conf;

    time_t       inactive;
    ngx_str_t   *value, s;
    ngx_int_t    max;
    ngx_uint_t   i;
    ...
}
```

注意变量 `clcf` 和其余的局部变量是如何被空行分开的。其余的局部变量仍然是垂直对其的。

局部变量声明之后也必须跟着一个空行，将它们与当前实际执行的 C 代码分开。例如：

```C
u_char * ngx_cdecl
ngx_sprintf(u_char *buf, const char *fmt, ...)
{
    u_char   *p;
    va_list   args;

    va_start(args, fmt);
    p = ngx_vslprintf(buf, (void *) -1, fmt, args);
    va_end(args);

    return p;
}
```

在局部变量定义之后跟着一个空行。