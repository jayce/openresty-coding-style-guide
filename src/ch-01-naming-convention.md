# 命名约定

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#naming-convention)

NGINX 源代码中的命名规则应该始终使用**完整名称**，包括源码文件名（`.c`, `.h`）、全局变量、全局函数、C struct/union/enum 名称、静态变量-函数以及 `.h` 头文件内的公共宏定义。这一点很重要，因为 C 没有像 C++ 中那样的显式名称空间的概念。使用**完整名称**有助于避免符号冲突和调试。例如： `ngx_http_core_module.c`, `ngx_http_finalize_request`, `NGX_HTTP_MAIN_CONF`。

在 Lua 库的 C 组件中，我们也应该使用类似 `resty_blah_`（如果库名为 `lua-resty-blah`）的字符作为 C 编辑单元中的所有 C 符号的前缀。

我们在 C 函数中定义局部变量的时候应该使用短名称。在 NGINX 核心代码中有大量常用的短名称，比如：`cl`, `ev`, `ctx`, `v`, `p`, `q` 等等。这些变量一般都是临时的、局部的。根据霍夫曼原则，我们应该在当前上下文环境中使用通用的短名称来避免单行干扰。即使是短名称也应该遵循 NGINX 的约定。除非必要，不要创建自己的约定。并使用有意义的名称。短名称 `p` 和 `q` 它们是字符串指针变量的通用名称，在字符串处理上下文环境当中使用。

C 语言结构体和联合的成员变量名称尽可能的使用单词的完整拼写形式（除非名称太长）。例如，NGINX 核心结构体 `ngx_http_request_s` 当中有像 `read_event_handler`, `upstream_states`, `request_body_in_persistent_file` 这样很长名称。

我们应该在 `typedef` 引用结构体类型时使用 `_t` 结尾，定义结构体名称时使用 `_s` 结尾，定义枚举类型时使用 `_e` 结尾。在函数作用域当中定义类型时不受此约束。以下是 NGINX 核心的一些例子：

```c
typedef struct ngx_connection_s      ngx_connection_t;
```

```c
typedef struct {
    WSAOVERLAPPED    ovlp;
    ngx_event_t     *event;
    int              error;
} ngx_event_ovlp_t;
```

```c
struct ngx_chain_s {
    ngx_buf_t    *buf;
    ngx_chain_t  *next;
};
```

```c
typedef enum {
    ngx_pop3_start = 0,
    ngx_pop3_user,
    ...
    ngx_pop3_auth_external
} ngx_pop3_state_e;
```