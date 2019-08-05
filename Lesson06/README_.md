#  分离头指针
  
==============
  
##  知识点
  
  
* 分离头指针
* HEAD 含义
* git diff
  
###  分离头指针 (Detached HEAD)
  
  
有时候想尝试性修改某些内容（实验），也许并不会真的提交到分支，这时候可以使用分离头指针，修改的内容不会进入任何分支。
  
当修改内容的头指针没有与任何branch挂钩时，如果这时将头指针指向了某个分支（master），刚刚做的修改会被git当作垃圾废弃。
  
  
~~~bash
<img src="https://latex.codecogs.com/gif.latex?max%20@%20Maxs-MBP-2016%20in%20~&#x2F;Develop&#x2F;learnhtml%20on%20git:master%20o"/> git checkout 5009f3a5f4
Note: checking out '5009f3a5f4'.
  
You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.
  
If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:
  
  git checkout -b <new-branch-name>
  
HEAD is now at 5009f3a Add index.html
  
~~~
  
修改README 文件（添加一行即可）
  
~~~bash
<img src="https://latex.codecogs.com/gif.latex?max%20@%20Maxs-MBP-2016%20in%20~&#x2F;Develop&#x2F;learnhtml%20on%20git:5009f3a%20o"/> ls
README.md  index.html
  
<img src="https://latex.codecogs.com/gif.latex?max%20@%20Maxs-MBP-2016%20in%20~&#x2F;Develop&#x2F;learnhtml%20on%20git:5009f3a%20o"/> vim README.md
~~~
  
如果这时再将HEAD指向master，刚才做的修改会被废弃（可以进入gitk --all 查看）
  
~~~bash
<img src="https://latex.codecogs.com/gif.latex?max%20@%20Maxs-MBP-2016%20in%20~&#x2F;Develop&#x2F;learnhtml%20on%20git:5009f3a%20x"/> git checkout master
~~~
  
  
###  HEAD 
  
  
HEAD归根到底其实还是指向了一个commit，并且可以指代那个commit
  
  
###  git diff
  
  
git diff 用来比较两次commit的不同
可以使用HEAD指代当前分支最后一次commit或者
HEAD~1 , HEAD~2 分别表示倒数一次，倒数二次
  
~~~bash
<img src="https://latex.codecogs.com/gif.latex?max%20@%20Maxs-MBP-2016%20in%20~&#x2F;Develop&#x2F;learnhtml%20on%20git:master%20x"/> Git diff a8a599a4dd07 0434ef25597
<img src="https://latex.codecogs.com/gif.latex?Git%20diff%20HEAD%20HEAD~1"/> Git diff HEAD HEAD~2
~~~
  
  