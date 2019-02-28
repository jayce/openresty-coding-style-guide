# goto 语句

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#goto-statements-and-code-labels)

NGINX 谨慎地使用 `goto` 语句进行错误处理。这是对臭名昭着的 `goto` 语句来说是一个很好的用例。
许多没有经验的 C 程序员可能会对 `goto` 语句的用法感到害怕，这是有点不合理的。
使用 `goto` 语句向后跳是一件坏事，其他情况下通常没问题，特别是错误处理。
NGINX 要求 goto 标签行前后加空行，如

```C
        p = ngx_pnalloc(pool, len);
        if (p == NULL) {
            goto failed;
        }

        ...

        i++;
    }

    freeaddrinfo(res);
    return NGX_OK;

failed:

    freeaddrinfo(res);
    return NGX_ERROR;
```