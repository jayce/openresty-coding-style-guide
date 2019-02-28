# 工具

> [查看英文原文](https://github.com/openresty/openresty.org/blob/9fa7554feee056304cd788d4584d6cf21442fd3f/v2/en/c-coding-style-guide.md#tools)

OpenResty 团队维护的 [ngx-releng](https://github.com/openresty/openresty-devel-utils/blob/master/ngx-releng) 工具，以静态扫描的方式检查当前 C 源代码树，解决本指南中涉及的许多（但不是全部）风格问题。
它是 OpenResty 核心开发人员必备的，对所有的 NGINX 模块开发人员和 NGINX 核心黑客也有所帮助。
我们一直为此工具添加更多的检查器，我们也欢迎您的贡献。

Clang 静态代码分析器对捕获细微的编码问题也非常有帮助，因此可使用 gcc 的高优化标志来编译所有内容。

现在许多编辑器都有高亮或自动删除行尾空格符、制表符转空格符的功能。在 VIM 编辑器中，我们可以将以下代码写入 `~/.vimrc` 文件中，以高亮显示任意行尾空白符：

```vim
highlight WhiteSpaceEOL ctermbg=darkgreen guibg=lightgreen
match WhiteSpaceEOL /\s$/
autocmd WinEnter * match WhiteSpaceEOL /\s$/
```

还有正确地设置缩进功能：

```vim
set expandtab
set shiftwidth=4
set softtabstop=4
set tabstop=4
```