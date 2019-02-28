# 检查无效指针

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#checking-pointer-nullity)

在 NGINX 世界中，我们通常使用 `p == NULL` 替代 `!p` 来检查指针值是否为 `NULL`。尽可能遵循此约定。
另外，还建议使用 `p != NULL` 替代 `p` 来检查相反的情况，不过在这种情况下简单地用 `p` 进行检查也没关系。

以下是些例子：

```C
if (addrs != NULL) {
```

```C
if (name == NULL) {
```

对 `NULL` 的检查通常会更清楚地了解这个值的意思，从而有助于提高代码可读性。