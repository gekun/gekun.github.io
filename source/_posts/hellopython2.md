---
title: Python入门(二):PyCharm开发环境
date: 2017-12-19 14:30:31
tags:
- Python
- PyCharm
---
> 开发Python的首选?那自然是PyCharm.来自于JetBrain家族的强大基因.😝

到这里去下载:[https://www.jetbrains.com/pycharm/download/](https://www.jetbrains.com/pycharm/download/)
下载免费的社区版即可.

## 新建Django项目
我们新建一个项目,项目名stuproject,app名称stu,其他默认如下图参数配置.
![配置](http://p066esquq.bkt.clouddn.com/1.png)
点击create创建.

在这个默认的情况下,创建项目最后会提示错误如下:
![错误](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2014.44.40.png)
创建的项目结构也是有问题的.
![错误](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2014.45.01.png)

产生这个错误的根本原因是:Mac内置的Python版本有点低,和项目自动获取到的最新的Django(目前是2.0)存在兼容问题.所以解决的办法有两种:
### 1.使用旧版本的Django,如1.9版本
- 进入终端,转到项目下bin目录,输入命令:
```
(venv) promote:bin kun$ pip install django==1.9
Collecting django==1.9
  Using cached Django-1.9-py2.py3-none-any.whl
Installing collected packages: django
Successfully installed django-1.9
```   

- 执行 django-admin.py startproject stuproject
```
(venv) promote:bin kun$ django-admin.py startproject
```

- 在当前目录内会生成startproject文件夹,进入文件夹可以看到目录结构
![结构](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2015.02.42.png)
    
* 执行 python managy.py runserver,看到服务器已经启动.在浏览器里输入网址访问http://127.0.0.1:8000/即可看到示例页面.
```
(venv) promote:stuproject kun$ python manage.py runserver
Performing system checks...
Django version 1.9, using settings 'stuproject.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

![itworks](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2015.12.55.png)

* 创建应用stu,终端下输入命令
```
python manage.py startapp stu
```

得到一个名为stu的项目应用.

![stuapp](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2015.17.11.png)


### 2.在Mac下安装一个新的Python版本
在这一节,我们来安装一个新的Python版本,我们需要在终端下输入一些命令来安装一些工具来进行安装.

- 安装HomeBrew[前提是要有xcode环境]
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

- 检查安装成功与否
```
brew doctor
```

- 安装Python3
```
brew install python3
```

- 检查python版本,安装的为Python3.6.3版本.
```
kun$ python3
Python 3.6.3 (default, Dec 17 2017, 22:42:13) 
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.39.2)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

- 打开PyCharm,新建Django项目,这次配置如下图,画红框处表示选择Python3.
![newconfig](http://p066esquq.bkt.clouddn.com/2.png)
> 注意:python3的目录是/usr/local/bin,而默认的python的目录为/usr/bin/

- 项目建好,目录结构如图
![jiegou](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2015.38.43.png)

- 点击运行,可以在浏览器里访问http://127.0.0.1:8000查看运行结果
![result](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2015.41.51.png)
> 如果运行按钮点不了,说明需要加如下运行配置.

![run](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2015.43.27.png)
或者
![run2](http://p066esquq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202017-12-19%2015.48.02.png)

至此,一个Django框架的Python项目已经建立起来.



