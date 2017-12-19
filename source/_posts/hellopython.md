---
title: Python入门(一):环境配置
date: 2017-12-19 12:48:06
tags:
- Python
---
# Python入门(一):环境配置
> Python最近很火,连文科生都咨询我能不能学Python了,亚历山大呀!看来也得与时俱进.于是找了本教材,利用周末的时间把书过了一遍,再利用两天的时间用Python的框架Django做了个小小的学生信息管理系统demo.在这里,把学习经历和开发过程做个总结.

先从环境配置开始把,我用的是Mac,所以讲的是Mac下开发环境的搭建.

## 安装Python
其实Mac已经自带了Python,我们可以打开终端,输入python即可进入Python模式.
``` bash
promote:~ kun$ python
Python 2.7.10 (default, Jul 15 2017, 17:16:57) 
[GCC 4.2.1 Compatible Apple LLVM 9.0.0 (clang-900.0.31)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
可以看到,Mac下的Python的版本是2.7.
[后面的学习中,我会安装其他的更新的版本,如Python3]

可以输入exit()退出Python模式.

## Python脚本
进入Python模式后,我们可以输入一下脚本进行测试.我们从最经典的"HelloWorld"开始.
输入如下命令:
``` bash
>>> print "Hello World!"
Hello World!
```
我们可以看到运行结果.

我们也可以新建个文本文档,命名为**hello.py**,将上面的脚本输入并保存,然后执行命令:
```
promote:~ kun$ python hello.py 
Hello World!
```
也可以得到相同的结果.

## 开发环境:VsCode
VsCode全名叫Visual Studio Code,是微软推出的一个代码编辑工具,正在变得越来越好用.
所以在VsCode下写Python也很方便,配置好环境后,还可以调试代码.

### VsCode安装Python扩展
切换到扩展页,输入python,搜索,安装排名第一的由微软推出的Python扩展即可,关闭VsCode再重新打开,以使配置生效.

#### 创建一个脚本文件并测试运行
* 新建工作区目录
* 用VsCode打开这个目录
* 新建一个test.py文件,输入下面脚本并保存
```
print "Hello World!"
```
* 左边切换到调试页,可以看到绿色运行按钮旁边显示没有配置,我们点击它,选择添加配置,VsCode会给自动生一个launch.json文件,里面已经包含了python运行所需要的配置信息.详情如下
```
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        
        {
            "name": "Python",
            "type": "python",
            "request": "launch",
            "stopOnEntry": true,
            "pythonPath": "${config:python.pythonPath}",
            "program": "${file}",
            "cwd": "${workspaceFolder}",
            "env": {},
            "envFile": "${workspaceFolder}/.env",
            "debugOptions": [
                "RedirectOutput"
            ]
        },
        {
            "name": "Python: Attach",
            "type": "python",
            "request": "attach",
            "localRoot": "${workspaceFolder}",
            "remoteRoot": "${workspaceFolder}",
            "port": 3000,
            "secret": "my_secret",
            "host": "localhost"
        },
        {
            "name": "Python: Terminal (integrated)",
            "type": "python",
            "request": "launch",
            "stopOnEntry": true,
            "pythonPath": "${config:python.pythonPath}",
            "program": "${file}",
            "cwd": "",
            "console": "integratedTerminal",
            "env": {},
            "envFile": "${workspaceFolder}/.env",
            "debugOptions": []
        },
        ......
}
```
点击保存.这时候,可以点击运行按钮来测试,默认是以Python配置运行的.在调试控制台可以看到运行的结果.

#### 如何测试有输入要求的脚本?
比如如下脚本,我们需要输入三个数进行测试.
``` bash
import math
a=input("input a:")
b=input("input b:")
c=input("input c:")
if(a==0):
    print "one root:",-c/float(b)
else:
    disc=b*b-4*a*c
    if(math.fabs(disc)<=1e-6):
        print "two equal roots:",-b/(2.0*a)
    else:
        if(disc>1e-6):
            x1=(-b+math.sqrt(disc))/(2.0*a)
            x2=(-b-math.sqrt(disc))/(2.0*a)
            print "two roots:%f,%f" % (x1,x2)
        else:
            print "no roots"
```
切换到调试页,点击调试按钮后的Python,弹出配置下拉框,选择Python: Terminal (integrated),表示用集成内置的终端窗口进行测试.

点击调试按钮进行调试,代码会运行并默认停在第一行,并且弹出debug工具栏,按照提示进行代码调试即可,也可以设置断点等.

在VsCode内置的终端窗口可以输入值进行测试.

我们也可以修改launch.json中的
```
"stopOnEntry": true,
```
将true修改为false,即调试代码时不会停在首行代码了.

## 开发环境:PyCharm
这部分放在下一个文中讲.


