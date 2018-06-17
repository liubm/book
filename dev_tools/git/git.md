## git 简介

git 功能大致可分为两部分，主要功能是版本管理，其次是分布式备份，总结起来就是分布式版本管理软件。

## git 教程

https://git-scm.com/docs
## git 安装
## git 常用命令

```sh
git init # 创建仓库
git remote add origin <server> # 如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器
git clone /path/to/repository #创建一个本地仓库的克隆版本
git clone username@host:/path/to/repository #从远端服务器检出仓库
git add <filename>
git add * #把它们添加到暂存区
git commit -m "代码提交信息" #你的改动已经提交到了 HEAD，但是还没到你的远端仓库。
git push origin master # 将这些改动提交到远端仓库,可以把 master 换成你想要推送的任何分支
git checkout -b feature_x #创建一个叫做“feature_x”的分支
git checkout master # 切换回主分支
git branch -d feature_x #删除分支
git push origin <branch> #推送分支到远端服务器
git pull # 从远端服务器更新本地仓库
git merge <branch> # 合并其它分支到当前分支
git diff <source_branch> <target_branch>  # 在合并改动之前，你可以使用如下命令预览差异
git add <filename> # 修改完冲突后，将文件标记为合并成功
git log # 取提交 ID
git tag 1.0.0 1b2e1d63ff # 为提交的ID创建一个叫做 1.0.0 的标签
git commit [-a]# 暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。-a:  自动执行git add 
git reset HEAD #暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。相当于撤消最后一次的 git add 操作
git rm --cached <file> #会直接从暂存区删除文件，工作区则不做出改变。
git checkout . # 会用暂存区全部文件替换工作区的文件
git checkout HEAD . # 会用 HEAD 指向的 master 分支中的全部文件件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。
git status [-s] #  查看在上次提交后是否有修改
git diff [--cached|--stat|HEAD] # 显示尚未缓存的改动|已缓存的改动|已缓存与未缓存的所有改动
```
## git 工作流
本地仓库由三个区域组成，第一个是你的 工作目录，它持有实际文件；第二个是 暂存区（Index），它像个缓存区域，临时保存你的改动；最后是 HEAD，它指向你最后一次提交的结果
* 工作区：就是你在电脑里能看到的目录。

* 暂存区：英文叫stage, 或index。一般存放在 ".git目录下" 下的index文件（.git/index）中，所* 以我们把暂存区有时也叫作索引（index）。

* 版本库：工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。版本库中的内容是最完整的，包含了所有的分支信息，工作区里最当前最新的版本，HEAD指向最后一次提交时的目录结构

  ![img](images/git_option_object.jpg)
## git 分支
分支是用来将特性开发绝缘开来的。在你创建仓库的时候，master 是“默认的”分支。在其他分支上进行开发，完成后再将它们合并到主分支上。


## git 更新与合并
## git 标签

## FAQ
1.  在工作区创建一个空的文件夹后，使用git status 显示版本没有变化
```sh
在空目录下新建.gitignore文件，内容如下

# Ignore everything in this directory  
*  
# Except this file  
!.gitignore  
```