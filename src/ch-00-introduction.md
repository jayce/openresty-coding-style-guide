# 序言

> 这本手册是在阅读 [OpenResty® C Coding Style Guide](http://openresty.org/en/c-coding-style-guide.html) 文章后翻译的。因英语阅读理解能力不好，借此机会学习理解英语、编码风格。

OpenResty C 语言组件中遵循 NGINX 的编码风格，如 OpenResty 自己的 NGINX 模块和 Lua 库的 C 语言部分。遗憾的是，即使是 NGINX 自己的核心 C 源码也没能严格的遵守与其他基础代码相同的约定。所以希望准备一份正式指南，以避免任何歧义。

贡献给 OpenResty 核心项目的补丁应始终遵循这份指南，否则无法通过代码检查，也无法按原样合并。在使用 C 开发自己的模块和库时，OpenResty 和 NGINX 社区始终鼓励遵循这份指南。