# for 语句

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#for-statements)

`for` 语句风格与 [if 语句](./ch-10-if-statements.md) 章节中的内容类似。
`for` 关键词之后，`{` 字符之后都要求有个空格符。此外，必须用花括号包含它的语句。而且，还要有个空格在 `for` 条件部分 `;` 之后。以下示例演示了这些要求：

```C
for (i = 0; i < size; i++) {
    ...
}
```

无限循环是个特殊情况，在 NGINX 世界中常用编码如下：

```C
    for ( ;; ) {
        ...
    }
```

或在 `for` 语句条件部分使用逗号表达式时：

```C
    for (i = 0, n = 2; n < cf->args->nelts; i++, n++) {
        ...
    }
```

或只忽略循环条件时：

```C
    for (p = pool, n = pool->d.next; /* void */; p = n, n = n->d.next) {
        ...
    }
```
