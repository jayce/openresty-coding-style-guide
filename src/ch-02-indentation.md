# 代码缩进

NGINX 世界仅使用空格符控制缩进，不使用制表符。一般情况下使用 4 个空格符缩进，除了一些特殊对其要求或其他要求的情况下（稍后将详细描述这些情况）。

始终保持正确的缩进。

## 80 行宽限制

All the source code lines should be kept within the 80 column limit (some code in the NGINX core even keep at 78 columns, but I suggest 80 columns as the hard limit). Different contexts will have different indentation rules for the indentations used in the continued lines. We will discuss each cases below in detail.

## 行尾空格符

There should never be any spaces or tabs at the end of source lines, not even blank lines. Many editors support highlighting or trimming such white-space characters automatically on the user's behalf. Make sure you configure your editor or IDE properly.