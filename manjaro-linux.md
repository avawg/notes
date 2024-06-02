## pacman
### 镜像源配置
配置文件 /etc/pacman.conf
添加清华镜像源
```
[archlinuxcn]
SigLevel = Optional TrustAll
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```
## pacman
### 镜像源配置
配置文件 /etc/pacman.conf
添加清华镜像源
```
[archlinuxcn]
SigLevel = Optional TrustAll
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```
### 软件
```
pacman -S安装软件， -s从仓库搜索软件包  
-y, --refresh 从服务器下载新的软件包数据库 
-u, --sysupgrade 升级所有已安装的软件包
-c, --clean 从缓存目录中删除旧软件包

pacman -R卸载
-n, --nosave 同时删除配置文件 
-s, --recursive 同时删除 (不会破坏其他软件包的) 依赖关系

pacman -Q查询已安装软件
-e, --explicit 列出所有单独指定安装的软件包 [过滤器]
-q, --quiet 在查询或搜索时显示较少的信息
pacman -Qdt显示不再被依赖的孤儿软件，pacman -R $(pacman -Qdtq)卸载这些软件
-d, --deps 列出所有作为依赖关系安装的软件包 [过滤器]  
-t, --unrequired 列出所有不被其他软件包要求的软件包 [过滤器]  

pacman有强大的AUR社区包管理器yay
yay 使用和pacman相同
```

## 目录
### 软件安装位置
系统级别软件安装在/usr目录下，相关目录/usr/bin, /usr/sbin, /usr/lib, /usr/include  
第三方软件/usr/share, /opt  

### 配置文件位置  
系统级别配置文件: /etc  

/etc/shells 所有注册的shell  
/etc/sudoers 注册普通用户可以执行特权用户的指令  

用户级别配置文件: ～/.config, ~/.bashrc, ~/.zshrc等  
软件安装目录下  

**软件安装**  
二进制包安装 | 源码包查看源码，编译，再安装  
脚本安装，执行sh文件  
**下载二进制程序包,无install.sh文件,添加应用程序启动图标**  
在/usr/share/applications/下创建*.desktop文件，编辑  
```
[Desktop Entry]  
Name=<application_name>  
Exec=<executable_path>  
Icon=<icon_path>  
Type=Application  
Terminal=false|true 
```
## 常用命令
### 开机关机
```
shutdown -h[alt] now 关机    
reboot | shutdown -r now 重启
```

### 进程关闭
```
ps aux | grep [process_name | service_name]  
kill -9 [id]  
```

### 服务
```
systemctl start [service_name] 开启服务
systemctl stop 关闭
systemctl restart 重启服务
systemctl enable [service_name]   服务开机启动
systemctl disable 取消服务开机自启动
```

### 服务自启动
```
在/etc/systemd/system/下添加|删除*.service配置文件  
添加如下内容
[Unit]  
Description=<service_description>  
[Service]  
Type=simple  
ExecStart=<executable_path>  
[Install]  
WantedBy=multi-user.target  
```

### netstat
```
-n list routes and do not resolve IP addresses to hostnames  
-a list all ports  
-p display PID and program names  
-t  list listening TCP ports  
-l  list all listening ports  
```

### 定时任务
crontab -e 分 时 日 月 周 指令，缺省时间用*  

### 设备挂载
```
mount [-t 文件系统] [设备名] [挂载点]  
umount [挂载点]

fdisk -l [fixed disk 固定磁盘]查看磁盘分区信息

❯ df -h  [disk free]查看磁盘分区使用情况
Filesystem      Size  Used Avail Use% Mounted on
dev             7.5G     0  7.5G   0% /dev
run             7.5G  1.9M  7.5G   1% /run
/dev/nvme0n1p6  295G   52G  228G  19% /
tmpfs           7.5G  126M  7.4G   2% /dev/shm
tmpfs           7.5G  206M  7.3G   3% /tmp
/dev/nvme0n1p1   96M   28M   69M  29% /boot/efi
tmpfs           1.5G  164K  1.5G   1% /run/user/1000
```  

### 压缩解压缩
```
tar -xvf 解包e[x]tract [v]erbose [f]ile  
tar -cvf 打包[c]reate  
-z tar.gz文件 
-b tar.bz2文件 
```
## 文件
### 查看
```
cat 
head -n number 输出前几行
tail -n number 输出最后几行 -f 跟踪文件输出
| grep pattern 仅输出匹配的行
```

### 编辑
```
cut -d [char] -f [number] 分割单词
wc [file] 文本统计 -l行数 -w单词数 -c字节数
vi [filename]
```

### 查找
```
find root_path -name "*pattern*"
-type f文件 d目录 l链接文件
-mmin -mtime 更改时间
-user 用户
-group 组
-perm  权限
```

###  grep 
global regular expression print 全局正则表达式搜索和打印  

参数:  
-v 过滤指定字符创内容的行  
-E(xtended-regexp) 使用扩展正则表达式  
-i(gnore-case) 忽略大小写  
-n 打印出行号  
-r 在目录下递归查找  

### awk
把文件逐行的输入，以空格为默认文件分割符将每行切片，切开的部分再进行各种分析处理  

awk [-F field-separator] 'pattern + action' {filename}  
```
ex: cat /etc/passwd | awk -F ':' 'BEGIN {print "name,shell"} {print $1","$7} END {print "blue,/bin/bash"}'  
```

NR表示行，$N表示第N列，下标从1开始  
（ ）条件语句，{print }输出内容  

### sed
流编辑器  
命令  
-n 安静模式  
-i 直接修改指定行内容

动作 
| | 功能 |
|-- | -- |
| a | 新增 |
| c  | 取代|
| d | 删除 | 
| i | 插入 |
| p | 打印 |
| s | 替换 |
1. 增  
a 追加文本到指定行后  
sed "2a abc" test.txt
i 插入文本到指定行前  
sed "2i abc" test.txt

2. 删  
删除指定的行
sed "/abc/d" test.txt

3. 改  
c 用新行取代旧行  
sed "2c abc"  test.txt  

文本替换  
sed 's/abc/123/g'  将出现的123替换成abc, /是分割符号，可以换成其他字符，如#、%，g表示全局，否则只替换每行第一处   
-E使用扩展正则表达式
sed 's/()/\U\1/g' 将第一个匹配组，字母大写替换

### 文件权限

文件类型(d目录,  -文件,  l软链接)  
权限分组：u所有者，g所有组，o其他人   

| | r=4| w=2| x=1|
| --- | :---: | :--: | :---: |
|文件|  cat | vi、echo (不包括删除文件)| 执行 |
|  目录| ls | touch、rm、cp、mv目录下的文件和目录 | cd |

文件的最高权限 x  
目录的最高权限 w, 有效权限 0 5 7  
修改权限：chmod 750 file

umask   查看文件默认权限  
文件默认最大权限 666  
目录默认最大权限 777   
新建文件或目录的权限=最大权限(换成rwx) - umask(换成rwx)  

ACL:解决用户身份不足的问题  
```
getfacl file
setfacl 选项 file  例:setfacl u:wg:rx file
mask 最大权限
```

suid
```
只有可执行的二进制程序才可以设定SUID权限  
命令执行者要对程序拥有x权限  
命令执行者在执行程序时获得该程序文件属主身份  

chmod 4755 file  
chmod u+s fie  
```
sgid 
```
对文件
只有可执行的二进制程序才可以设定SGID权限  
命令执行者要对程序拥有x权限  
命令执行者在执行程序时，组身份升级为该程序文件的组属主   

对目录
普通用户对此目录有r和x权限，才能进入此目录  
普通用户在此目录中的有效组会变成此目录的组属主，即若普通用户对此目录拥有w权限时，新建的文件的默认属组是这个目录的属主  
chmod 2755 file
chmod g+s file
```

SBIT权限
```
只对目录有效  
普通用户该目录rwx权限  
普通用户只能删除该目录下自己建立的文件，不能删除别人建立的文件  
chmod o+t file
chmod 1755 file
```

chattr权限
```
chattr + - = 
i(immutable): 对文件设置i属性，不允许对文件进行删除、改名，也不能添加和修改数据；对目录设置i属性，只能修改目录下文件的数据，不允许建立和删除文件。  
a(append-only)：对文件设置a属性，只能在文件中增加数据，也不能删除和修改数据；对目录设置a属性，只允许在目录下建立文件，不允许改名和删除。 
```


Capability尝试扩充RWX行为。把rwx 3组行为扩充成多组行为，扩充用户行为的细粒度权限管理。  
capability可分割root特权，把root特权分割成不同的能力，然后给不同的用户不同的能力。  