# 类型转换

> [点击查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#type-casting)

将 void 指针 (`void *`) 赋值给非 void 指针，C 语言是不要求显式类型转换的。NGINX 编码风格中也不要求。例如：

```C
char *
ngx_http_types_slot(ngx_conf_t *cf, ngx_command_t *cmd, void *conf)
{
    char  *p = conf;
    ...
}
```

上面的 `conf` 变量是个 void 指针，NGINX 核心将它赋值给 `char *` 类型的局部变量 `p`，且没有任何的显式类型转换。

当需要显式类型转换时，请确保类型名称与 `*` 字符之间有个空格，`)` 字符之后有个空格符，例如：

```C
*types = (void *) -1;
```

在 `*)` 字符之前有空格符，`)` 之后也有空格符。这也适用于值类型转换的例子：

```C
if ((size_t) (last - buf) < len) {
    ...
}
```

或者连续的多类型转换：

```C
aio->aiocb.aio_data = (uint64_t) (uintptr_t) ev;
```

注意 `(uint64_t)` 和 `(uintptr_t)` 之间的空格符，以及 `(uintptr_t)` 之后的。