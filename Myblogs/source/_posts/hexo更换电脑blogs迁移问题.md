---
title: hexo更换电脑blogs迁移问题
date: 2018-12-04 14:24:42
tags:
---
前言
---
现在我们要讨论一下当我们更换电脑时，我们的hexo博客怎么办？哈哈哈~~这就是说你已经成功利用hexo和github发布博客，如果还没有，可以看一下[教程](https://smalljianfan.github.io/2018/03/26/Hexo在Mac上的搭建过程/)。为了解决在不同时间，不同地点，不同电脑上写文章，我们就来看看下面的步骤吧~

具体的思路是：在生成的已经推到github上的hexo静态代码处建立一个分支，利用这个分支来管理自己的hexo源文件。

具体操作：

克隆github上面生成的静态文件到本地

>git clone https://github.com/yourname/hexo-test.github.io.git

把克隆到本地的文件除了git的文件都删掉，找不到git的文件的话可以都删掉。不要用`hexo init`初始化。

将之前使用hexo写博客时候的整个目录（所有文件）搬过来。把该忽略的文件忽略了

> touch .gitignore

创建一个叫hexo的分支并切换到hexo分支

>     git checkout -b hexo

提交复制过来的文件到暂存区

> 		git add --all

提交

> 	git commit -m "新建分支源文件"

推送分支到github

> 	git push --set-upstream origin hexo

到这里基本上就搞定了，以后再推就可以直接git push了，hexo的操作跟以前一样。

今后无论什么时候想要在其他电脑上面用hexo写博客，就直接把创建的分支克隆下来，npm install安装依赖之后就可以用了。

克隆分支的操作

> 	git clone -b hexo https://github.com/yourname/hexo-test.github.io.git

因为上面创建的是一个名字叫hexo的分支，所以这里-b后面的是hexo，再把后面的gitHub的地址换成你自己的hexo博客的地址就可以了。

这样做完了以后，每次写完博客发布之后不要忘了还要git push把源文件推到分支上。


github创建新分支过程
---

一、clone Repository（上面已经给大家介绍过了/或者说大家已经clone过了）

二、管理分支

1、查看分支

a.查看本地分支

cd 到你clone的文件的目录下，使用 git branch命令，如下：

>      $ git branch 
> 
>      * master

*标识的是你当前所在的分支。

b.查看远程分支

>     git branch -r

c.查看所有分支
>     git branch -a


2、本地创建新的分支
>      git branch [branch name]
> for example :
>      
>      git branch hexo

3、切换到新的分支

>    	git checkout [branch name]

4、将新分支推送到github

> 		git push origin [branch name]


详细的创建分支的方法大家可以参考[Github创建分支](https://blog.csdn.net/top_code/article/details/51931916)