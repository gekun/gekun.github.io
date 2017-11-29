---
title: MacOs系统下使用VSCode对Cpp进行debug
date: 2017-11-29 20:27:13
tags: 
- Mac
- VSCode
- C++
- debug
---

## 1.下载安装**VSCode**

## 2.安装cpptools
``` bash
    cpptools
```
## 3.安装clang++
``` bash
    clang++
```

## 4.Comd+Q,退出VSCode，重新打开VSCode。

## 5.生成c_cpp_properties.json
按fn+F1调出命令行模式，选择[C/Cpp: Edit Configurations]，会自动生成c_cpp_properties.json，在mac节点中，会自动选择xcode自带的相关include和lib等路径【所以，事先要安装好xcode】。

## 6.生成一个tasks.json
调出命令行，选择[Tasks: Configure Task]，生成一个tasks.json。内容参考如下：
``` bash
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "0.1.0",
    "command": "clang++", //使用clang++编译Cpp文件，如果你使用C开发，改成clang
    "isShellCommand": true,
    "args": ["test.cpp", "-g"],//如果使用的是C，则改成test.c或者相对应的c入口文件。如果需要支持C++11，添加"-std=c++11"
    "showOutput": "always"
}
```

## 7.生成launch.json
进入命令行，选择[Debug: Open launch.json]，内容参考如下：
``` bash
{
        "version": "0.2.0",
        "configurations": [
            {
                "name": "C++ Launch (GDB)",
                "type": "cppdbg",
                "request": "launch",
                "targetArchitecture": "x86_64",
                "program": "${workspaceRoot}/a.out",
                "args": [],
                "stopAtEntry": false,
                "cwd": "${workspaceRoot}",
                "environment": [],
                "externalConsole": true,
                "MIMode": "lldb",
                "preLaunchTask": "clang++" //如果使用的是C，改为clang
            }
        ]
    }
```
## 8.测试，编写一个test.cpp
``` bash
#include <iostream>
using namespace std;
int main(void)
{
    cout<<"Hello World!"<<endl;
    return 0;
}
```
使用shift+command+b，编译生成a.out。
Fn+F5进行debug调试。可以设断点，单步调试。

最后，调试时，VSCode会挡住终端窗口，害的我以为在VsCode里面的输出里面看结果。