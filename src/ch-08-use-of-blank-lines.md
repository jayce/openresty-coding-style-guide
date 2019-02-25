# 空行使用

> [点击查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#use-of-blank-lines)

连续的 C 函数定义、多行全局/静态变量、结构体/联合/枚举定义必须使用 2 个空行分隔。以下是连续的 C 函数定义示例：

```c
void
foo(void)
{
    /* ... */
}


int
bar(...)
{
    /* ... */
}
```

连续的静态变量定义示例：

```C
static ngx_conf_bitmask_t  ngx_http_core_keepalive_disable[] = {
    ...
    { ngx_null_string, 0 }
};


static ngx_path_init_t  ngx_http_client_temp_path = {
    ngx_string(NGX_HTTP_CLIENT_TEMP_PATH), { 0, 0, 0 }
};
```

单行变量定义可以紧靠在一起，如下：

```C
static ngx_str_t  ngx_http_gzip_no_cache = ngx_string("no-cache");
static ngx_str_t  ngx_http_gzip_no_store = ngx_string("no-store");
static ngx_str_t  ngx_http_gzip_private = ngx_string("private");
```

以下是连续的结构体定义示例：

```C
struct ngx_http_log_ctx_s {
    ngx_connection_t    *connection;
    ngx_http_request_t  *request;
    ngx_http_request_t  *current_request;
};


struct ngx_http_chunked_s {
    ngx_uint_t           state;
    off_t                size;
    off_t                length;
};


typedef struct {
    ngx_uint_t           http_version;
    ngx_uint_t           code;
    ngx_uint_t           count;
    u_char              *start;
    u_char              *end;
} ngx_http_status_t;
```

它们全由 2 个空行分隔。

如果它们附近有些不同类型的顶级对象定义，也要用 2 个空行分隔，例如：

```C
#if (NGX_HTTP_DEGRADATION)
ngx_uint_t  ngx_http_degraded(ngx_http_request_t *);
#endif


extern ngx_module_t  ngx_http_module;
```

静态函数声明遵循 C 全局变量声明规则，也使用 2 个空行分隔。但连续的 C 函数声明无需如此，例如：

```C
ngx_int_t ngx_http_discard_request_body(ngx_http_request_t *r);
void ngx_http_discarded_request_body_handler(ngx_http_request_t *r);
void ngx_http_block_reading(ngx_http_request_t *r);
void ngx_http_test_reading(ngx_http_request_t *r);
```

即便有些 C 函数声明跨多行也是如此，例如：

```C
char *ngx_http_merge_types(ngx_conf_t *cf, ngx_array_t **keys,
    ngx_hash_t *types_hash, ngx_array_t **prev_keys,
    ngx_hash_t *prev_types_hash, ngx_str_t *default_types);
ngx_int_t ngx_http_set_default_types(ngx_conf_t *cf, ngx_array_t **types,
    ngx_str_t *default_type);
```

有时也会用 2 个空行，按照语义进行分隔，以提高代码的可读性，例如：

```C
ngx_int_t ngx_http_send_header(ngx_http_request_t *r);
ngx_int_t ngx_http_special_response_handler(ngx_http_request_t *r,
    ngx_int_t error);
ngx_int_t ngx_http_filter_finalize_request(ngx_http_request_t *r,
    ngx_module_t *m, ngx_int_t error);
void ngx_http_clean_header(ngx_http_request_t *r);


ngx_int_t ngx_http_discard_request_body(ngx_http_request_t *r);
void ngx_http_discarded_request_body_handler(ngx_http_request_t *r);
void ngx_http_block_reading(ngx_http_request_t *r);
void ngx_http_test_reading(ngx_http_request_t *r);
```

前者大多与**响应头**相关，后者与**请求体**相关。