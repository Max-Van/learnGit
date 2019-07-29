# 最小配置
==============

## 知识点

* 查看配置
* 添加配置
* 区别

## 查看配置

* git config --list [--local | --global | --system]

## 添加配置

* git config [--local | --global | --system] user.name 'Your name'
* git config [--local | --global | --system] user.email 'Your email'

## 区别

* local：区域为本仓库
* global: 当前用户的所有仓库
* system: 本系统的所有用户

## 实战

###查看配置
~~~bash
$ git config --global --list
$ git config --local --list
$ git config --system --list
~~~

###修改配置
~~~bash
$ git config --global user.name 'fan'
$ git config --global user.email 'maxffq@me.com'
~~~


## 优先级

类似的，我们可以修改local的配置（当两者有冲突时，local的配置会覆盖global的设置）

local > global > system 