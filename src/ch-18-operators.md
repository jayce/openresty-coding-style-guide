# 运算符

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#operators)

## 二元运算符

在大多数 C 的二元运算符前后，都要加个空格符，比如：四则运算符、位运算符、关系运算符、逻辑运算符。以下是些例子：

```C
 yday = days - (365 * year + year / 4 - year / 100 + year / 400);
```

还有

```C
if (*p >= '0' && *p <= '9') {
```

对于结构体、联合成员运算符 `->` 和 `.`的前后，是不允许有空格符的。例如：

```C
ls = cycle->listening.elts;
```

至于逗号，应该在它的后面加个空格符：

```C
for (p = pool, n = pool->d.next; /* void */; p = n, n = n->d.next) {
```

NGINX 通常只在 `for` 语句条件上下文、多个类型相同的变量声明当中使用逗号。而在其他情况下，最好将逗号表达式拆分成独立的语句。

## 一元运算符

通常在前缀一元运算符的前后是不加空格的。以下是些例子：

```C
for (p = salt; *p && *p != '$' && p < last; p++) { /* void */ }
```

```C
#define SET(n)      (*(uint32_t *) &p[n * 4])
```

请注意，我们没有在一元运算符 `*` 或 `&` 的前后加任何空格符（在上面第二个例子中 `&` 之前加空格符，是因为类型转换表达式而添加的，见[类型转换](./ch-09-type-casting.md)）。

这规则同样适用于后缀一元运算符：

```C
for (value = 0; n--; line++) {
```

## 三元运算符

三元运算符也要求在运算符的前后加个空格符，就像二元运算符那样。例如：

```C
node = (rc < 0) ? node->left : node->right;
```

正如在这个例子中看到的那样，三元运算符的条件部分是个表达式时，可以给它加一对圆括号。
虽然不要求这样，但这么做可使逻辑更为清晰。