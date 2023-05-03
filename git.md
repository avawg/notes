## Git
如果git服务器已支持git-lfs，对二进制文件进行了区分管理。克隆文件时，**必须使用git lfs clone**。

### 配置
#### 基本信息配置
git config --global user.name "wang gang"  
git config --global user.email "1182834046@qq.com"  
#### 换行符
windows: git config --global core.autocrlf true  
linux | mac: git config --global core.autocrlf input  
#### 中文编码支持
git config --global i18n.commitencoding utf-8  
git config --global i18n.logoutputencoding utf-8  
#### 显示路径的中文
git config --global core.quotepath false  
#### ssh认证
ssh-keygen -t rsa -C 1182834046@qq.com  
测试是否配置成功 ssh -T git@github.com  

