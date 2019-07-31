# Git 基本命令
==============

## 知识点

* 了解暂存区
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

## Git 分支

* git checkout -av : 查看分支
* git checkout -b branch_name : 创建分支 

## Git push

* git push 讲缓冲区中的内容发送到仓库。 
