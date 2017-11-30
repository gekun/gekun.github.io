---
title: 如何去备份hexo博客
date: 2017-11-30 08:02:01
tags:
---

博客搭建好后，在git里面的只有静态文件，没有.md源文件。所以不备份的话，以后换电脑或者换个环境是个问题。通用的方法是使用git分支来备份源文件。
以下是步骤：

* 1.在git上创建一个分支取名hexo，这个取名可以随意的。

* 2.设置hexo为默认分支。

* 3.在本地新建个文件夹，将hexo仓库clone至本地，将之前源文件夹中的内容复制到此目录，即username.github.io，public目录可以不用复制，因为它是生成的静态文件;

* 4.如果之前的目录内，如主题等，里面有.git，要将其删除掉，否则无法push。

* 5.在username.github.io目录下，执行**npm install** , **npm install hexo-deployer-git**。

* 6.执行**git add**，**git commit -m "消息内容"**，**git push origin hexo**提交源文件。

* 7.执行hexo g -d生成静态文件部署到git上。