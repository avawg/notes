### 软件
**软件安装位置**  
系统级别软件安装在/usr目录下，相关目录/usr/bin /usr/bin /usr/lib /usr/include  
第三方软件 /usr/share, /opt  
～/用户个人配置及软件  

*配置文件位置**  
系统级别配置文件 /etc  
用户级别配置  ～/.config  ~/.bashrc ~/.zshrc等  
软件安装目录下  

二进制包安装 | 源码包查看源码，编译，再安装  
脚本安装，执行sh文件  

### pacman
pacman -S安装软件 -y从仓库源获取最新软件信息  -yy强制获取 -u刷新 -s从仓库搜索软件包  
pacman -Sc清理安装包  
pacman -R卸载 -s同时卸载依赖 -n删除全局配置  
pacman -Q查询已安装软件 -e用户安装软件 -q不带具体版本号   
-Qdt显示不再被依赖的孤儿依赖 pacman -R $(pacman -Qdtq)卸载这些软件

**sh** the standard command language interpreter  

### 下载安装包,无install.sh文件,自行安装
在/usr/share/applications/下创建*.desktop文件，编辑  
```
[Desktop Entry]  
Name=<application_name>  
Exec=<executable_path>  
Icon=<icon_path>  
Type=Application  
Terminal=false|true 
```
### 设备挂载
mount [设备名] [挂载点]  
umount [挂载点]

### shell
tab 提示补全  
ctrl + A: 光标移到行首  
ctrl + E: 光标移到行尾  
ctrl + U: 删除光标前的整行内容  

#### 服务自启动
在/etc/systemd/system/下添加|删除*.service配置文件  
```
添加如下内容:  
[Unit]  
Description=<service_description>  
[Service]  
Type=simple  
ExecStart=<executable_path>  
[Install]  
WantedBy=multi-user.target  
```
systemctl enable | start | stop | disable [服务名]  
后台执行  
nohup默认将输出信息到nohup.txt文件中  
& 后台执行，程序输出到控制台上   
\> *.txt 输出重定向，覆盖写，2 >&1将标准错误重定向到标准输出  

**服务关闭**
ps aux | grep [进程|服务名]  
kill -9 [id]  

#### 定时任务
crontab -e 分 时 日 月 周 指令，缺省时间用*  

**压缩解压缩**  
tar -xvf 解包e[x]tract [v]erbose [f]ile  
tar -cvf 打包[c]reate  
z tar.gz b tar.bz2  

**关机**  
shutdown -h now  
**重启**  
reboot | shutdown -h[alt] now

**grep** 全局正则表达式搜索和打印  
--extended-regexp 使用扩展正则表达式  
--ignore-case 忽略大小写  
--with-filename --line-number 匹配的文件名和行号  
--only-matching 只输出匹配的文本  
--fixed-strings 不使用正则表达式  

**awk**对行列进行筛选，格式化输出  
NR表示行，$N表示第N列，下标从1开始。  
（ ）条件语句，{print }输出内容  

**sed** 对文本进行替换，使用正则表达式  
sed 's/abc/123/g'  将出现的123替换成abc  
-E使用扩展正则表达式，-i对文件内容进行替换  
sed 's/()/\U\1/g' 将第一个匹配组，字母大写替换
--extended-regexp 使用扩展正则表达式  
--ignore-case 忽略大小写  
--with-filename --line-number 匹配的文件名和行号  
--only-matching 只输出匹配的文本  
--fixed-strings 不使用正则表达式  

