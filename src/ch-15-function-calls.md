# 函数调用

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#function-calls)

C 函数调用时，不应该在参数列表的括号周围加空格符。以下是个例子：

```C
sa = ngx_palloc(cf->pool, socklen);
```

在函数调用超过 80 个字符宽度时，应该将参数列表拆成独立的行。而后续的行必须与第一个参数垂直对其，如下：

```C
        buf->pos = ngx_slprintf(buf->start, buf->end, "MEMLOG %uz %V:%ui%N",
                                size, &cf->conf_file->file.name,
                                cf->conf_file->line);
```