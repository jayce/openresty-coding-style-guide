# 80 行宽限制

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#the-80-column-limit)

每一行源码都应保持在 80 个字符宽度以内（NGINX 核心中一些代码保持在 78，而我建议将 80 作为硬性限制）。在连接多行的情况中，不同的上下文将有不同的缩进规则。我们将在接下来的内容中详细讨论每个案例。