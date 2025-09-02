

## 配置

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

## 工作区
```
- git clone  如果git服务器已支持git-lfs，对二进制文件进行了区分管理。克隆文件时，必须使用git lfs clone
- git init
- git remote add origin(远端仓库名) {url}
- git remote -v 查看远程仓库
```

## 分支管理  
```
git branch 查看分支 -r -vv
git switch 切换分支  
git checkout -b branch origin/origin_branch 新建分支并设置跟踪远程仓库分支
```

## 文件修改 
```
- add file 添加文件  
- rm 删除文件  
- mv 移动文件  
- restore 复原修改
- checkout file 回退未在暂存区的更改
```

## 日志&差异
```
git log [--oneline]查看commit日志
git reflog
git status 查看状态  
git diff 查看更改(工作区 vs 暂存区)  --name--status
git diff HEAD 工作区 vs 最新提交（HEAD）
git diff --cached 暂存区 vs 最新提交（HEAD）
git diff HEAD^ HEAD 查看上一个commit修改内容
```

## 工作命令 

### git add 将文件添加到暂存区
```
git add -A new、modified、deleted
git add -u modified、deleted
git add . new、modified、deleted当前目录及子目录下ls
git add * new、modified
```

### git commit 提交修改
```
git commit -m (commit消息，不加-m，默认打开编辑器)
git commit --amend(不新增commit节点，id和message发生变化，时间不变) 
git commit -a modified、deleted
```

### 回退修改
```
git reset HEAD^ 回退到上次commit提交(此次提交内容会保留,unstaged)
git reset --hard 直接回退最近一次修改
git revert HEAD 新建一次提交，撤销当前HEAD的更改  
```

### 合并commit记录
```
git rebase -i HEAD~N 合并最近N条修改记录
pick -> s
```

### 抽取修改
```
git cherry-pick {commit-id}
git format-patch -1 {commit-id} 打patch
git am *.patch
git merge branch 合并分支修改 
git rebase dst_branch  将分支修改 rebase到当前分支
```

### 解决冲突
```
解决完冲突后， git add/rm <conflicted_files> 标记已解决
git cherry-pick --continue
git rebase --continue
```

### 远程合作
```
git fetch [origin branch] 下载最新文件  
git pull [--rebase] 同步并更新本地代码，选择合并方式
git push -f 强制更新与 commit amend一起使用(amend后历史提交记录不重合)
git push [origin dst_branch] 指定远程分支
```  
