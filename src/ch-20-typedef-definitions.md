# 类型定义

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#typedef-definitions)

与[宏](./ch-16-macros.md)一样，要求在 `typedef` 指令定义主体部分之前有至少 2 个空格符。例如：

```C
typedef u_int  aio_context_t;
```

在把一组 `typedef` 定义放在一起时，需 2 个以上的空格符。另外，出于美观的角度将它们纵向对其会更好，如下：

```
typedef struct ngx_module_s          ngx_module_t;
typedef struct ngx_conf_s            ngx_conf_t;
typedef struct ngx_cycle_s           ngx_cycle_t;
typedef struct ngx_pool_s            ngx_pool_t;
typedef struct ngx_chain_s           ngx_chain_t;
typedef struct ngx_log_s             ngx_log_t;
typedef struct ngx_open_file_s       ngx_open_file_t;
```