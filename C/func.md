
## 字符串拷贝函数
| 函数名| 处理 | 
|--- | --- |
| strcpy(dst, src)| 拷贝原字符串到目标字符串，尾部添加'\0'，可能越界 |
| strcpy(dst,  n, src)| 目标字符串的最大长度为n（包含尾部'\0'），否则写入失败，不会占用非法空间 |
| strncpy(dst,src, n)| 从原字符串最多读n个字符写到目标字符串，**写入目标字符串长度>=strlen(dst)则不填充尾部'\0’** |
| strncpy_s(dst, m, src, n)| 从原字符串最多读n个字符，写到目标字符串，目标字符串最大允许写入长度为m，否则写入失败 |
| sprintf(dst, "%s%d", src)| 将原字符串填充到模式串中，再写到目标字符串，尾部追加'\0'，可能越界 |
| sprintf_s(dst, n, "%s%d", src)| 目标字符串的最大长度为n（包含尾部'\0'），否则写入失败，不会占用非法空间 |

