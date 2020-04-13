<p align="center">
  <img width="600" src="https://www.inhandnetworks.com/upload/image/201904/28/0300230504.jpg">
</p>


简体中文 | [English](./README.md)

## 一、简介

VG710-Python-Templates是一个车载边缘计算解决方案，它基于python3和IoT实现，它使用了最新的物联网架构技术，内置了丰富的API接口，提炼了丰富的业务模块，提供了丰富的组件功能，它可以帮助你快速搭建定制化业务功能，相信不管你的物联网需求是什么，本项目都能够帮主到你

### 开发流程说明

<kbd>VS Code IDE</kbd>---(sftp connect)---><kbd>VG710</kbd>---><kbd>Import Templates</kbd>

<kbd>Python Program design</kbd>---><kbd>Online debugging</kbd>

<kbd>Package binaries in VG710</kbd>---><kbd>Download and install binaries on other vg710</kbd>

## 二、环境准备

要使用该模板快速开发您的车联网应用，你必须具备以下条件

### `1、映翰通的车载网关InVehicle Gateway710，简称VG710`

### `2、能够接入internet的物联网卡`

### `3、一台PC电脑，Windows/MacOS/Linux,并且已经接入Internet`

### `4、确保您的PC已经安装了以下软件：`

&emsp;&emsp;*(4.1).[MicroSoft VS code IDE开发工具](https://code.visualstudio.com/Download/)*

&emsp;&emsp;*(4.2).[Python3.7.X](https://www.python.org/downloads/)*

### `5、验证PC环境是否满足要求：`

&emsp;&emsp;*(5.1).按 <kbd>Win</kbd>+<kbd>R</kbd> 键，调出命令提示符，输入python，回车，弹出如下信息则说明python运行环境已经准备好*

```cmd
    Python 3.7.4 (v3.8.1:1b293b6006, Dec 18 2019, 14:08:53)
    [Clang 6.0 (clang-600.0.57)] on win64
    Type "help", "copyright", "credits" or "license" for more information.
    >>>
```

&emsp;&emsp;*(5.2).VS Code环境确认，完成VS code安装，需要在VS Code IDE的“Extensions”中安装插件才能继续使用*

&emsp;&emsp;&emsp;*(5.2.1).Python*

&emsp;&emsp;&emsp;*(5.2.1).Project Templates*

&emsp;&emsp;&emsp;*(5.2.1).SFTP*

&emsp;&emsp;*(5.3).VS Code环境确认，完成VS code安装，需要在VS Code IDE的“Extensions”中安装插件才能继续使用*

&emsp;&emsp;&emsp;*(5.3.1)make sure “Python: select Interpreter” is Python 3.7.x*



## 三、VG710-Python-Templates目录结构

本项目已经为你生成了一个完整的开发框架，下面是整个项目的目录结构。
```
├── .vscode                    # VS Code配置文件夹
│  └── sftp.json               # SFTP插件的配置文件，用于与InVehicleG710建立SFTP连接
├── build                      # App发布包文件夹
├── src                        # App源码文件夹
│  │── main.py                 # App程序入口
│  └── parse_config.py         # 解析App配置文件
├── config.yaml                # App配置文件
├── setup.py                   # App版本、SDK版本等信息说明
```



## 四、开发


### PC中打开命令提示符窗口

  Windows 10 ----> <kbd>Win</kbd>+<kbd>R</kbd>键

  MacOS10.14 ----> <kbd>command</kbd>+<kbd>空格</kbd>，输入terminal.app

  Linux      ----> <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>打开新终端


```
# 以MacOS为例，将文件存储在“Documents/”目录中

  cd Documents/

# 克隆项目

  git clone https://github.com/154386670/VG710-Python-Templates.git

```

# 五、修改项目名称

&emsp;将克隆的模板项目修改为自建项目名称，以“HelloWorld”为例，修改“VG710-Python-Templates”项目文件夹名称为“HelloWorld”

&emsp;文件目录如下：
```
  HelloWorld
  ├── .vscode
  │  └── sftp.json
  ├── build
  ├── src
  │  │── main.py
  │  └── parse_config.py
  ├── config.yaml
  ├── setup.py
```

# 五、将VG710-Python-Templates项目导入VS Code

&emsp;*（5.1）修改代码中的项目名称：*<font color=#FF0000>注意：Python App名称中不能包含空格。</font>
```python

./Documents/HelloWorld/setup.py，代码片段：
..
...
    rom setuptools import setup, find_packages
    setup(name='helloworld',          #修改“appname”为“HelloWorld”
        sdk_version='0.2.0',
        version='0.0.0',
        author='Inhand',
...
..
---------------------------------------------------------------------------
./Documents/HelloWorld/src/main.py，代码片段：
..
...
    app = APPConfig(name="appname")   #修改“appname”为“HelloWorld”
    app_config_file = app.get_app_cfg_file()
...
..
---------------------------------------------------------------------------

```
&emsp;*（5.2）配置Sftp连接信息：*


```json
./Documents/HelloWorld/.vscode/sftp.json

{
    "name": "Debug Server",
    "host": "192.168.2.1",                    #车载网关IP地址
    "protocol": "sftp",
    "port": 222,
    "username": "pyuser",
    "password":"VF7101937000028",             #车载网关序列号
    "remotePath": "/var/user/app/appname",    #修改“appname”为“HelloWorld”
    "uploadOnSave": true,
    "ignore":[
        ".vscode",
        ".git",
        ".DS_Store"
    ]
}
```

&emsp;*（5.3）建立Sftp连接：*

在建立与VG710连接之前，需要确保VG710已开启“IDE调试模式”，如下。注意：为了设备安全性，该调试模式将在设备重启后自动关闭

在VG710配置界面中：选择<kbd>APP</kbd>,点击<kbd>APP管理</kbd>选项卡，打开“开启IDE调试”

在VS Code工具栏点击菜单栏中的“View”，选择“command palette",在弹出框中输入：
```
>SFTP:Open SSH in Terminal    #启动SFTP服务
```
点击键盘<kbd>enter</kbd>按钮，下拉列表会提示以下信息：

```
Debug Server 192.168.2.1              #ip地址为上一步“sftp.json”中的“host”地址，
```
确认无误后，点击<kbd>enter</kbd>按钮，完成VS Code与VG710的SFTP连接，用于开发者代码设计与调试。

&emsp;首次连接时，“终端”会提示您是否要继续连接，此时键盘输入“yes”并点击<kbd>enter</kbd>按钮;

&emsp;接着“终端”窗口会提示您输入密码，密码为VG710的15为序列号;

&emsp;输入密码后，点击<kbd>enter</kbd>按钮，当“终端”提示如下信息时，说明VS Code以成功与VG710建立SFTP连接，并且VS Code已通过SFTP登入VG710系统中。

```json
BusyBox v1.26.2 (2020-03-30 13:58:08 CST) built-in shell (ash)

#     #  #####  #######    #      ###
#     # #     # #    #    ##     #   #
#     # #           #    # #    # #   #
#     # #  ####    #       #    #  #  #
 #   #  #     #   #        #    #   # #
  # #   #     #   #        #     #   #
   #     #####    #      #####    ###

---------------------------------------------------------------
   Vehicle Gateway from InHand Networks
---------------------------------------------------------------
/tmp/app $ 
```

&emsp;*（5.4）将程序upload至VG710：*

完成代码修改后，在左侧“EXPLORER”空白处点击鼠标右键，选择<kbd>Sync Local->Remote</kbd>将代码同步到VG710中。
在终端中输入如下信息，确保已经成功upload实例程序至VG710系统中：

```
cd /var/user/app/
ls -l
```
返回如下信息，说明成功将程序实例上传至VG710
```python
drwxrwxrwx		4	pyuser pyuser			0 Apr 8 2020 HelloWorld
```
进入到“HelloWorld”项目目录中，输入如下信息，即可在VG710中运行实例
```
tmp/user/app #~> cd HelloWorld/src/
tmp/user/app/HelloWorld/src #~>python main.py

```
键盘输入<kbd>ctrl</kbd>+<kbd>C</kbd>,终止调试程序

实例测试无误后，即可将程序打包成二进制文件用于其他VG710使用

&emsp;*（5.5）将程序构建为二进制文件：*

终端退回至app目录，并输入&emsp;<kbd>build_py_app.sh HelloWorld</kbd>&emsp;如下：
```
tmp/user/app/HelloWorld/src #~>cd /tmp/user/app
tmp/user/app#~>build_py_app.sh HelloWorld

```
输入<kbd>build_py_app.sh HelloWorld</kbd>，当提示如下信息时，构建完成
```
~ $ build_py_app.sh HelloWorld
build APP:HelloWorld pkg!
generate APP pkg:
build APP:HelloWorld pkg finished
```
&emsp;*（5.6）将程序回传至开发者PC：*

在左侧“EXPLORER”空白处点击鼠标右键，选择<kbd>Download Folder</kbd>将二进制文件回传到本地PC中。成功回传后项目目录会新增*.tar.gz文件，如下：
```
  HelloWorld
  ├── .vscode
  │  └── sftp.json
  ├── build
  ├──└──*.tar.gz      #二进制文件
  ├── src
  │  │── main.py
  │  └── parse_config.py
  ├── config.yaml
  ├── setup.py
```

Copyright (c) 2020-present Xiaopeng Gou
