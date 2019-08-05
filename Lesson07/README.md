# 分支与commit
==============

## 知识点

* 删除分支
* 对历史上的commit修改commit message（变基操作）
* 合并多个commit为一个commit

### 删除分支

git branch -d <分支名>

如果遇到报警：将修改内容合并到主分支，加入我们不需要合并，可以将-d 改为-D

git branch -D <分支名>

### 变基（rebase）

git rebase -i <选择需要改变的上一个commit ID>

假设需要修改 ‘Add javascript’ 为 ‘Introduce js folder’

~~~bash
9391244 (HEAD -> master) rename css.02 to css.02.backup
0d38c85 (origin/master, origin/HEAD) Add logo
`a8a599a Add javascript`
c7e0c93 (tag: TagForCssfile) Add css file
5009f3a Add index.html
d000057 Initial commit
~~~

进入rebase
~~~bash
$git rebase -i c7e0c93
~~~

Change pick to reword 

~~~bash
reward a8a599a Add java script 
~~~

then :wq to save and quit

change descritpion 

~~~bash
Introduce js folder 
~~~


then :wq to save and quit

Verify it again 

~~~bash
$git log --oneline
~~~

~~~bash

26e4a77 (HEAD -> master) Change README.md
90d49b0 rename css.02 to css.02.backup
4d1e03f Add logo
`5b9bc74 Introduce js folder`
c7e0c93 (tag: TagForCssfile) Add css file
5009f3a Add index.html
d000057 Initial commit
~~~

please note: **the commit id changes**


### 合并多个commit 为一个commit

假设需要将 5009f3a - 90d49b0 合并为一个commit

~~~bash
26e4a77 (HEAD -> mypr1, master) Change README.md
90d49b0 rename css.02 to css.02.backup
4d1e03f Add logo
5b9bc74 Introduce js folder
c7e0c93 (tag: TagForCssfile) Add css file
5009f3a Add index.html
d000057 Initial commit
~~~

需要从d000057开始rebase

~~~bash
$git rebase -i d000057
~~~

~~~bash
pick 5009f3a Add index.html
s c7e0c93 Add css file
s 5b9bc74 Introduce js folder
s 4d1e03f Add log
s 90d49b0 rename css.02 to css.02.backup
pick 26e4a77 Change README.md
~~~

:wq! and continue 

insert one line to indicate the merge reason

~~~bash

Create one start web page index.html

Add index.html
Add css file
Introduce js folder
Add logo
Rename css.02 to css02.backup

~~~

:wq! and continue 

git log 校验 : 合并成功

~~~bash
$ max @ Maxs-MBP-2016 in ~/Develop/learnhtml on git:d000057 o [1:30:10] C:1
$* commit 884094893fd57e254d36f24474ca0d715149f710 (HEAD -> mypr1)
| Author: max <maxffq@gmail.com>
| Date:   Mon Aug 5 00:58:43 2019 +0800
|
|     Change README.md
|
|* commit d80a81ae6e2c04209b3839db2dc30c2dc8ef753b
| Author: max <maxffq@gmail.com>
| Date:   Tue Jul 30 16:47:44 2019 +0800
|
|     Create one start web page index.html
|     Add index.html
|     Add css file
|     Introduce js folder
|     Add logo
|     rename css.02 to css.02.backup
|
| commit d000057b45d478475052e49399e8d724c23c5932
  Author: Max-Van <35359341+Max-Van@users.noreply.github.com>
  Date:   Tue Jul 30 16:36:52 2019 +0800

      Initial commit
~~~