## Vim 
**光标移动**  
| 命令 | 功能 |
| :---: | --- |
| h j k l | 左 下 上 右 |  
| w e b | word下一单词头 end下一单词尾 backword上一单词头 |  
| f{char} | 在行中向后快速移动到char字符上 |  
| 0 $ | 0表示行首，$表示行尾 | 
| g | 行跳转: gg跳到第一行， number + G/gg跳到指定行，G跳到最后一行 |    
| :set number | 显示行号 |

**页面移动**  
| 指令 | 功能 |
| :---: | --- |  
| ctrl + f / b | 向前/向后翻页 |  
| zz | 将当前行置于页面中央 |  

**插入** 
| 指令 | 功能 |
| :---: | --- |
| i | insert 在当前光标所在处插入 |
| a | append 在当前光标的后面插入 |  
| o | open a line below 从当前光标所在行的下面插入新的一行 |
| ESC | 退出编辑模式到一般模式 |

**删除修改** 
| 命令 | 功能 |
| :---: | --- |
| x | 删除光标所在处字符 |
| **d** | delete，也相当于剪切 |
| **c** | change 先删除后插入编辑 |
| r | replace r替换一个字符，R跟随光标一直替换 | 
| s | substitute 删除一个字符并进入插入模式 |  
| [number]\<command>[text object] | [number]\<d/c/y>[w/$/t{char}] |

**复制粘贴**
| 指令 | 功能 |
| :---: | --- |
| y | yank 复制 |
| p | put 粘贴从光标的下一行开始粘贴 |
| u |undo 复原上一个动作 |
| . | 重复上一个动作 |
| ctrl + R | redo undo |  

**搜索与替换**  
| 命令 | 功能 |
| :---: | --- |
| /word | 向光标之下搜索名为word的字符串 |
| n N | 重复前一个搜索动作， 与n相反方向搜索 |
| :[range] s/pattern/word/flags | 在range范围内将pattern串替换为word。其中range有：默认表示当前行，n1,n2表示两行之间，%表示全文；flags: g(global)全局范围 c(confirm)确认 n(number)统计匹配次数而不替换 |  
| ~ | 字符大小写转换 |

**文件保存** 
| 命令 | 功能 |
| :---: | :---: |
| :w | 将编辑的数据写入磁盘 |
| :wq | 保存数据，并退出vim |
| q! | 强制退出，不保存 |
| :w filename | 将编辑的数据另存为filename文件 |

**多文件编辑**  
| 命令 | 功能 |
| :---: | :---: |
| e | edit 打开文件 |  
| b | buffer 切换缓冲区 |  
| vs sp | 垂直分屏 水平分屏 |  
| ctrl + w | 切换窗口 |  
| ls | 缓冲区列表 | 

**代码补全**  
| 命令 | 功能 |
| :---: | :---: |
| ctrl + n/p | 代码补全 |  
| ctrl + f | 补全文件名 |  
| ctrl + x ctrl + o | 补全代码 |

