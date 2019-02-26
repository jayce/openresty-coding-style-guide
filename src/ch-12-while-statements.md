# while 语句

`while` 语句风格与 [if 语句](./ch-10-if-statements.md)章节中的内容类似。
在 `while` 关键词之后，`{` 字符之后都要求有个空格符。此外，必须用花括号包含它的语句。以下是个例子：

```C
    while (log->next) {
        if (new_log->log_level > log->next->log_level) {
            new_log->next = log->next;
            log->next = new_log;
            return;
        }

        log = log->next;
    }
```

`do-while` 语句也是类似：

```C
        do {
            p = h2c->state.handler(h2c, p, end);

            if (p == NULL) {
                return;
            }

        } while (p != end);
```

注意 `do` 和 `{` 之间的空格符，以及 `while` 前后的空格符。