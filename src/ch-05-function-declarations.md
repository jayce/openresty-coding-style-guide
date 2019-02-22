# 函数声明

C 函数声明（不是定义）尽可能编辑成一行，不论是在头文件或 `.c` 文件的头部中。以下是 NGINX 核心的例子：

```c
ngx_int_t ngx_http_send_special(ngx_http_request_t *r, ngx_uint_t flags);
```

如果一行太长，超过 80 个字符宽度，应该将它拆分成多行并保持 4 空格缩进。例如：

```c
ngx_int_t ngx_http_filter_finalize_request(ngx_http_request_t *r,
    ngx_module_t *m, ngx_int_t error);
```

如果函数返回类型是个指针，应在类型与 `*` 字符之间加入空格，如下：

```c
char *ngx_http_types_slot(ngx_conf_t *cf, ngx_command_t *cmd, void *conf);
```

注意函数定义的风格不同于函数声明。更多细节见[函数定义](./ch-06-function-definitions.md)。
