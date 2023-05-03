如果git服务器已支持git-lfs，对二进制文件进行了区分管理。克隆文件时，**必须使用git lfs clone**。

### 配置

配置文件: ~/.gitconfig  

查看配置
```
git config --global --list
```

用户名和邮箱配置  
```
git config --global user.name "wang gang"  
git config --global user.email "1182834046@qq.com"  
```

换行符  
```
windows: git config --global core.autocrlf true  
linux | mac: git config --global core.autocrlf input  
```

中文编码支持  
```
git config --global i18n.commitencoding utf-8  
git config --global i18n.logoutputencoding utf-8  
```
 
显示中文路径    
```
git config --global core.quotepath false  
```

生成ssh公私钥  
```
ssh-keygen -t rsa -b 3072
将公钥传到github上
测试是否配置成功 ssh -T git@github.com  
```

### 初始化工作区
```
- git clone  
- git init, git remote add origin , git push -u origin master  
```

### 记录修改 
```
- add file 添加文件  
- rm 删除文件  
- mv 移动文件  
- restore 复原修改  
```

### 日志&差异
```
git log 查看commit日志  
git status 查看状态  
git diff 查看更改  --name--status
```

### 分支管理  
```
git branch 查看分支
git checkout -b 切换分支  
git checkout -b branch origin_branch设置跟踪远程仓库
git checkout file 回退未在暂存区的更改
```

### 提交 合并分支  
```
git add 将文件添加到暂存区
git add -A new、modified、deleted
git add -u modified、deleted
git add .  new、modified、deleted当前目录及子目录下ls
git add *  new、modified
git commit -m 
git commit -a modified、deleted
git commit file -m "" 提交更改到本地仓库（只提交部分文件）  --amend(不新增commit节点，id和message发生变化，时间不变)  
git merge branch 合并分支  
git rebase dst_branch  合并分支   
git reset HEAD^ 回退到上次commit提交(此次提交内容会保留,unstaged)  
git reset HEAD file  
git revert HEAD 新建一次提交，撤销当前HEAD的更改  
```

### 远程合作
```
git push origin source_branch:dst_branch 向远程推送  
git push -f 强制更新与 commit amend一起使用
git fetch origin branch:local_branch 下载最新文件  
git pull 下载并更新  
```  