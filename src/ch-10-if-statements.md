# if 语句

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#if-statements)

NGINX 在使用 C `if` 语句的时候会有一些风格要求。

首先，`if` 关键词之后必须有一个空格符，条件的右圆括号和左花括号之间也有空格符。如下，

```C
if (a > 3) {
    ...
}
```

注意 `if` 之后和 `{` 之前**有空格符**，`(` 之后或 `)` 之前**没有空格符**。

另外，左花括号必须与 `if` 关键词写在同一行，除非超过 80 个字符。
在这种情况下我们应将条件分成多行，并把左花括号单独写成一行。
以下示例演示了这点：

```C
            if (ngx_http_set_default_types(cf, prev_keys, default_types)
                != NGX_OK)
            {
                return NGX_CONF_ERROR;
            }
```

注意 `!= OK` 与条件部分是如何垂直对齐的。（不包括 `if` 语句的 `(` 字符）

当逻辑运算符涉及长条件的某一部分时，我们应该确保逻辑运算符在后续行的开头，并且缩进反映了条件表达式的嵌套结构，如下：

```C
        if (file->use_event
            || (file->event == NULL
                && (of->uniq == 0 || of->uniq == file->uniq)
                && now - file->created < of->valid
#if (NGX_HAVE_OPENAT)
                && of->disable_symlinks == file->disable_symlinks
                && of->disable_symlinks_from == file->disable_symlinks_from
#endif
            ))
        {
            ...
        }
```

我们可以忽略中间的宏指令，它们与 `if` 语句编码风格无关。

如果 `if` 语句块之后有其他语句，我们应该在它们之间留一个空行。例如：

```C
        if (rc != NGX_OK && (of->err == 0 || !of->errors)) {
            goto failed;
        }

        if (of->is_dir) {
            ...
        }
```

请注意如何使用空行来分隔连续的 `if` 语句块。或者其他语句：

```C
        if (file->is_dir) {

            /*
             * chances that directory became file are very small
             * so test_dir flag allows to use a single syscall
             * in ngx_file_info() instead of three syscalls
             */

            of->test_dir = 1;
        }

        of->fd = file->fd;
        of->uniq = file->uniq;
```

同样的，在 `if` 语句之前通常也会有个空行，如下：

```C
        rc = ngx_open_and_stat_file(name, of, pool->log);

        if (rc != NGX_OK && (of->err == 0 || !of->errors)) {
            goto failed;
        }
```

在这些代码块周围使用空行，使得代码没那么拥挤。这同样适用于 `while`, `for` 等语句。

`if` 语句必须始终使用花括号，即使 "then" 分支只有一条语句。例如：

```C
            if (file->is_dir || file->err) {
                goto update;
            }
```

即使在标准 C 语言允许的情况下，我们也不能忽略花括号。

## else 语句

当 `if` 语句使用 `else` 分支时，它也必须用花括号来对包含的语句进行分组。同样的，空行必须在 `} else {` 之前。例如：

```C
    if (of->disable_symlinks == NGX_DISABLE_SYMLINKS_NOTOWNER
        && !(create & (NGX_FILE_CREATE_OR_OPEN|NGX_FILE_TRUNCATE)))
    {
        fd = ngx_openat_file_owner(at_fd, p, mode, create, access, log);

    } else {
        fd = ngx_openat_file(at_fd, p, mode|NGX_FILE_NOFOLLOW, create, access);
    }
```

注意 `} else {` 是如何放在同一行上的，并且在 `} else {` 之前有一个空行。