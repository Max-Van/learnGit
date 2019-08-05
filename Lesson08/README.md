# 工作区与暂存区
==============

## 知识点

* 比较HEAD和暂存区差异（git diff --cached）
* 比较工作区和暂存区差异
* 


### 比较HEAD和暂存区

vim 修改一些html, 比如添加config


修改后，再使用git add
~~~bash
$ git add index.html
~~~

最后比较，可以看到差异
~~~bash
$ git diff --cached
~~~


### 比较工作和暂存区

vim 修改一些html, 比如添加bare repo

使用 git diff : 比较的就是整个工作区和整个暂存区

如果仅仅想比较某个文件，可以加文件名

git diff -- [file name]

~~~bash
$ git diff -- index.html
~~~