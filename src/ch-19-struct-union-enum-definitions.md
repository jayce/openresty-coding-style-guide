# 结构体/联合/枚举定义

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#structunionenum-definitions)

结构、联合、枚举它们的定义风格类似。其字段标识符应该纵向对其，与[局部变量定义](./ch-07-local-variables.md)章节中的描述相同。我们将从 NGINX 核心中选一些真实的例子来演示：

```C
typedef struct {
    ngx_uint_t           http_version;
    ngx_uint_t           code;
    ngx_uint_t           count;
    u_char              *start;
    u_char              *end;
} ngx_http_status_t;
```

与局部变量定义的情况相同，也应该用空行将字段组分开，如下：

```C
struct ngx_http_request_s {
    uint32_t                          signature;         /* "HTTP" */

    ngx_connection_t                 *connection;

    void                            **ctx;
    void                            **main_conf;
    void                            **srv_conf;
    void                            **loc_conf;

    ngx_http_event_handler_pt         read_event_handler;
    ngx_http_event_handler_pt         write_event_handler;
    ...
};
```

在这样的情况下，每组的成员标识符必须纵向对其，但不同的组不要求对其（虽然也可以像上面演示的例子那样）。

联合定义如下：

```C
typedef union epoll_data {
    void         *ptr;
    int           fd;
    uint32_t      u32;
    uint64_t      u64;
} epoll_data_t
```

枚举定义如下：

```C
typedef enum {
    NGX_HTTP_INITING_REQUEST_STATE = 0,
    NGX_HTTP_READING_REQUEST_STATE,
    NGX_HTTP_PROCESS_REQUEST_STATE,

    NGX_HTTP_CONNECT_UPSTREAM_STATE,
    NGX_HTTP_WRITING_UPSTREAM_STATE,
    NGX_HTTP_READING_UPSTREAM_STATE,

    NGX_HTTP_WRITING_REQUEST_STATE,
    NGX_HTTP_LINGERING_CLOSE_STATE,
    NGX_HTTP_KEEPALIVE_STATE
} ngx_http_state_e;
```