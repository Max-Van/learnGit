# .git简介
==============

## 知识点

* 了解 `.git 目录`
* HEAD
* config
* refs
* objects
* commit,tree,blob 关系

### .git 目录

- HEAD ： 标识了当前指向的分支
- config ： 本地的配置信息


#### HEAD

修改分支，观察HEAD内容的变化

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:master x [16:30:38] C:1
$ git branch temp

$max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:master x [16:30:45] 
$ git checkout temp
M       Lesson03/README.md
Switched to branch 'temp'

$ max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:temp x [16:30:52] 
$ cat .git/HEAD
ref: refs/heads/temp

$ max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:temp x [16:30:59] 
$ git checkout master
M       Lesson03/README.md
Switched to branch 'master'
Your branch is up to date with 'origin/master'.

$ max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:master x [16:31:07] 
$ cat .git/HEAD      
ref: refs/heads/master

~~~


#### config

修改config文件的用户名，观察变化

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:master x 
$ cat .git/config                                 
[core]
        repositoryformatversion = 0
        filemode = true
        bare = false
        logallrefupdates = true
        ignorecase = true
        precomposeunicode = true
[remote "origin"]
        url = https://github.com/Max-Van/learnGit.git
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
        remote = origin
        merge = refs/heads/master
[user]
        name = max
        email = maxffq@gmail.com
$max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:master x 

$ vim .git/config 
将用户名从max改为maxfan

$ max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:master x
$ git config --local --list

core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
core.ignorecase=true
core.precomposeunicode=true
remote.origin.url=https://github.com/Max-Van/learnGit.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.master.remote=origin
branch.master.merge=refs/heads/master
user.name=maxfan
user.email=maxffq@gmail.com
~~~

最后再将用户名改回

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnGit on git:master x 
$ git config --local user.name 'max'
~~~


#### refs

* heads
* tags
* remote

##### heads

heads 中存放着所有的分支,可以把分支看作独立的工作空间，在一定时间内保持各自研发的独立性，等分支开发的模块成熟后再合体到集成分支。

heads 下有两个文件：master and temp

~~~bash

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/heads on git:temp o 
$ ls -lh
total 16
-rw-r--r--  1 max  staff    41B Aug  4 17:32 master
-rw-r--r--  1 max  staff    41B Aug  4 17:38 temp

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/heads on git:temp o 
$ cd master
cd: not a directory: master

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/heads on git:temp o  C:1
$ cat master
8ac7ea2ae8d265c665490afaf7bd9910d5964a0a

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/heads on git:temp o [18:27:49]
$ git cat-file -t 8ac7ea2ae8d2
commit
~~~


##### tags

Tag存储的是一个里程碑，里面指向了一个commit

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/tags on git:temp o 
$ ls
TagForCssfile


$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/tags on git:temp o 
$ cat TagForCssfile
c6939ed60cd2c37b1838581be606e2c739c768f5

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/tags on git:temp o 
$ git cat-file -t c6939ed60cd
tag

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/refs/tags on git:temp o 

$ git cat-file -p c6939ed60cd
object c7e0c93593ed1d3e8f6ac5e6c08c18d309e72ca6
type commit
tag TagForCssfile
tagger max <maxffq@gmail.com> 1564913891 +0800

i create temp another branch temp based on this.
~~~


### objects

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/objects on git:temp o [18:40:09]
$ ls
04   20   5b   7f   87   96   a9   ac   b9   c7   cd   d4   dd   fe   pack
0d   50   6a   84   8a   a8   ab   b7   c6   c8   d0   da   f9   info
~~~

这两位+进去后的哈希值合在一起就是一棵树（Tree）

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/objects on git:temp o [18:40:16]
$ cd fe

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/objects/fe on git:temp o [18:42:35]
$ ls
cf7e88657d195ec3a45becd06d7383281876ca

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/objects/fe on git:temp o [18:42:36]
$ git cat-file -t fecf7e88657d19
tree

~~~

继续进入这棵树

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/objects/fe on git:temp o 
$ git cat-file -p fecf7e88657d19
100644 blob 7f40755ba1ea37aab9e1486bf26db55a7ce8dc48	README.md
100644 blob 6ad4c68d567a1a5b415dcfce2010fce1a60b245f	index.html
040000 tree a9424a073da3c077e48045696e4742b6def97702	styles

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/objects/fe on git:temp o [18:43:53]
$ git cat-file -t 7f40755b
blob

$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml/.git/objects/fe on git:temp o [18:44:58]
$ git cat-file -p 7f40755b
 learnhtml
html
add this for branch temp
~~~

任何文件的内容相同，其实就是同一个blob

### commit,tree and blob 的关系(demo)

![relationship](https://cdn-std.dprcdn.net/files/acc_136293/AX6EUC)
