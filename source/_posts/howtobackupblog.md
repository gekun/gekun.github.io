---
title: 如何去备份hexo博客
date: 2017-11-30 08:02:01
tags:
- hexo
- 备份
- hexo命令
category:
- 技术
---
## 备份

博客搭建好后，在git里面的只有静态文件，没有.md源文件。所以不备份的话，以后换电脑或者换个环境是个问题。通用的方法是使用git分支来备份源文件。
以下是步骤：

* 1.在git上创建一个分支取名hexo，这个取名可以随意的。

* 2.设置hexo为默认分支。

* 3.在本地新建个文件夹，将hexo仓库clone至本地，将之前源文件夹中的内容复制到此目录，即username.github.io，public目录可以不用复制，因为它是生成的静态文件;

* 4.如果之前的目录内，如主题等，里面有.git，要将其删除掉，否则无法push。

* 5.在username.github.io目录下，执行
```
npm install
npm install hexo-deployer-git
```

* 6.执行提交源文件。
```
git add .
git commit -m "文件提交"
git push origin hexo
```

* 7.生成静态文件部署到git上。
```
hexo g -d
```

## 发布、修改
以后在本地username.github.io内对博客内容进行修改后，做以下两步即可：

* 1.备份源文件
```
git add .
git commit -m "文件提交、修改"
git push //如果不放心，可以指定git push origin hexo
```

* 2.生成静态网页并部署
```
hexo g -d
```
以后重复这两步即可。

## 从备份恢复
* 1.目标电脑安装git
* 2.安装node.js和npm
* 3.将仓库从git克隆之本地
* 4.执行命令
```
npm install hexo-cli -g
npm install
npm install hexo-deployer-git
```

## 附录
Hexo的源文件说明：
1、*_config.yml*站点的配置文件，需要拷贝；
2、*themes/*主题文件夹，需要拷贝；
3、*source*博客文章的.md文件，需要拷贝；
4、*scaffolds/*文章的模板，需要拷贝；
5、*package.json*安装包的名称，需要拷贝；
6、*.gitignore*限定在push时哪些文件可以忽略，需要拷贝；
7、*.git/*主题和站点都有，表示这是一个git项目，不需要拷贝；
8、*node_modules/*是安装包的目录，在执行npm install的时候会重新生成，不需要拷贝；
9、*public*是hexo g生成的静态网页，不需要拷贝；
10、*.deploy_git*同上，hexo g也会生成，不需要拷贝；
11、*db.json*文件，不需要拷贝。

## hexo命令补充说明
```
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #将.deploy目录部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本
hexo deploy -g  #生成加部署
hexo server -g  #生成加预览
命令的简写
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy
```

## 参考
[怎么去备份你的hexo博客](http://www.jianshu.com/p/baab04284923)

[搭建Hexo博客中碰到的坑](http://www.jianshu.com/p/a2fe56d11c4f)