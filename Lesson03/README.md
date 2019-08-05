# Git 基本命令
==============

## 知识点

* 了解 **暂存区**
* Git add 
* Git commit
* Git 分支
* Git push

## Git 暂存区

![git flow](https://cdn-std.dprcdn.net/files/acc_136293/31XpLG)

* git config --list [--local | --global | --system]

## Git add

* git add -u：将文件的修改、文件的删除，添加到暂存区。
* git add .：将文件的修改，文件的删除，文件的新建，添加到暂存区。
* git add -A：将文件的修改，文件的删除，文件的新建，添加到暂存区。
* git add -u 只能操作跟踪过的文件, git add -A 等同于git add -all
* git mv filename: 修改文件名称

## Git commit

* git commit -m '修改原因'：将文件的修改、文件的删除，添加到暂存区。

* git commit -ma '修改原因'：直接将修改推到暂存区（不需要add，不推荐这种做法）

* git commit --amend ： 如果刚才commit时候填写的内容有误，需要修改，可以使用--amend来修改

## Git 分支

* git branch -av : 查看分支
* git checkout branch_name : 创建分支 
* git checkout -b branch_name [commit_id] : 基于某一次提交创建分支并指向改分支

## Git reset

* git reset --hard  
清空暂存区


## Git log

* git log
* git log -n3 : 只显示最近三条的日志
* git log --oneline ：以短格式显示
* git log --all --graph：图形化显示所有分支
* git log --all --graph --oneline：图形化显示所有分支（简洁模式）


## Git help

* git help --web log



## Git push

* git push 讲缓冲区中的内容发送到仓库。 
