# switch 语句

`switch` 语句风格与 [if 语句](./ch-10-if-statements.md)章节中的内容类似。在 `switch` 关键词，`{` 字符之后都要求有个空格符。此外，其余语句必须写在花括号内。以下是个例子：

```C
    switch (unit) {
    case 'K':
    case 'k':
        len--;
        max = NGX_MAX_SIZE_T_VALUE / 1024;
        scale = 1024;
        break;

    case 'M':
    case 'm':
        len--;
        max = NGX_MAX_SIZE_T_VALUE / (1024 * 1024);
        scale = 1024 * 1024;
        break;

    default:
        max = NGX_MAX_SIZE_T_VALUE;
        scale = 1;
    }
```

注意 `case` 标签与 `switch` 关键词是如何垂直对其的。

有时会在第一个 `case` 标签行前面留一个空行，如下：

```C
        switch (c->log_error) {

        case NGX_ERROR_IGNORE_EINVAL:
        case NGX_ERROR_IGNORE_ECONNRESET:
        case NGX_ERROR_INFO:
            level = NGX_LOG_INFO;
            break;

        default:
            level = NGX_LOG_ERR;
        }
```