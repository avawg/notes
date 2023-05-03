# gdb

## gdb app

- set args | show args
- l(list) 查看代码， 文件名:行号  函数名
- b(break) 设置断点，文件名:行号 函数名
- i(info) 查看断点
- d(delete) | ena(enabel) | dis(disable) 删除断点 | 断点生效 | 断点失效，断点编号
- start 启动程序，阻塞在main函数的第一行，等待输入后续其它gdb命令
- run 如果程序设置了断点就会停在第一个断点的位置，如果没有断点，程序就执行完了
- p(print) 打印变量
- display 变量自动显示
- c(continue) 断点处继续执行
- step 单步调试，进入函数
- finish 跳出函数
- next 单步调试，不进入函数
- until 跳出循环 


## gdb attach pid

- disassamble 查看符号跳转
- bt 打印栈
- call