<p align="center">
  <img width="600" src="https://www.inhandnetworks.com/upload/image/201904/28/0300230504.jpg">
</p>


简体中文 | [English](./README.md)

# 1、简介

VG710-Python-Templates是一个车载边缘计算解决方案，它基于python3和IoT实现，它使用了最新的物联网架构技术，内置了丰富的API接口，提炼了丰富的业务模块，提供了丰富的组件功能，它可以帮助你快速搭建定制化业务功能，相信不管你的物联网需求是什么，本项目都能够帮主到你

# 2、环境准备

## 2.1 硬件环境

&emsp;&emsp;*--> 映翰通的车载网关InVehicle Gateway710，简称VG710*

&emsp;&emsp;&emsp;&emsp; <font color=#ff000>★★★</font>确保VG710配置界面中<kbd>APP管理</kbd>已勾选“开启IDE调试”模式，注意：为了设备安全性，调试模式将在设备重启后自动关闭，若需重新连接，请再次勾选“开启IDE调试”

&emsp;&emsp;*--> PC电脑，Windows/MacOS/Linux三选一,已通过RJ45或者WiFi连接到VG710*

*<font color=#ffff4>建议将VG710中插入物联网SIM卡连接到Internet，提高程序设计体验</font>*

## 2.2 PC软件环境

&emsp;&emsp;*--> [Python3.7.X](https://www.python.org/downloads/)*

&emsp;&emsp;*--> [MicroSoft VS code IDE开发工具](https://code.visualstudio.com/Download/)*

&emsp;&emsp;VS Code必装插件：

&emsp;&emsp;&emsp;*<1>.Python*

&emsp;&emsp;&emsp;*<2>.SFTP*

# 3、VG710-Python-Templates文件说明

本项目已经为你生成了一个完整的开发框架，下面是整个项目的目录结构。
```
VG710-Python-Templates         # 项目名称
├── .vscode                    # VS Code配置文件夹
│  └── sftp.json               # SFTP插件的配置文件
├── build                      # App发布包文件夹
├── src                        # App源码文件夹
│  │── main.py                 # App程序入口
│  └── parse_config.py         # 解析App配置文件
├── config.yaml                # App配置文件
├── setup.py                   # App版本、SDK版本等信息说明
```


# 4、修改文件内容

## 首次开发需要修改以下3个文件为实际项目内容

&emsp;<font color=#ffff4>注意：引号中的内容不能有空格。</font>

以HelloWorld项目为例

```python
1.VG710-Python-Templates/setup.py，#代码片段：
..
...
    rom setuptools import setup, find_packages
    setup(name='VG710-Python-Templates',          #项目名称
        sdk_version='0.2.0',
        version='0.0.0',
        author='Inhand',
...
..
2.VG710-Python-Templates/src/main.py，#代码片段：
..
...
    app = APPConfig(name="VG710-Python-Templates")   #项目名称
    app_config_file = app.get_app_cfg_file()
...
..

3.VG710-Python-Templates/.vscode/sftp.json. #代码片段：
{
    "name": "Debug Server",
    "host": "192.168.2.1",                            #VG710 IP地址
    "protocol": "sftp",
    "port": 222,
    "username": "pyuser",                             # SFTP用户名
    "password":"VF7101937000028",                     # SFTP密码
    "remotePath": "/var/app/VG710-Python-Templates",  #项目名称
    "uploadOnSave": true,
    "ignore":[
        ".vscode",
        ".git",
        ".DS_Store"
    ]
}
```
*<font color=#ffff4>注意：SFTP密码为VG710网关15位序列号”</font>*

# 5、程序开发

&emsp;&emsp;以MacOS为例，将文件存储在“Documents/”目录中
```
cd Documents/
```
&emsp;&emsp;克隆项目
```
git clone https://github.com/154386670/VG710-Python-Templates.git
```


&emsp;*建立Sftp连接：*


在VS Code工具栏点击菜单栏中的“View”，选择“command palette",在弹出框中输入：
```
>SFTP:Open SSH in Terminal    #启动SFTP服务
```
按下键盘<kbd>enter</kbd>按钮，下拉列表会提示以下信息：

```
Debug Server 192.168.2.1              #ip地址为上一步“sftp.json”文件中的“host”地址，
```
确认无误后，按下<kbd>enter</kbd>按钮,之后再VS Code ”终端"界面按照如下步骤操作：

&emsp;1、首次连接时，“终端”会提示您是否要继续连接，此时键盘输入“yes”并按下<kbd>enter</kbd>按钮;

&emsp;2、接着“终端”窗口会提示您输入密码，密码为VG710的15位序列号;

&emsp;3、输入密码后，点击<kbd>enter</kbd>按钮，当“终端”提示如下信息时，说明VS Code以成功与VG710建立SFTP连接.


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
/tmp/app $                  #该目录问VG710文件目录

```
# 6、将调试程序upload至VG710：

完成代码修改后，在VS Code左侧“EXPLORER”空白区域点击鼠标右键，选择<kbd>Sync Local->Remote</kbd>将代码同步到VG710中。

```
cd /var/app/
ls -l
```
返回如下信息，说明成功将程序实例上传至VG710
```python
drwxrwxrwx		4	pyuser pyuser			0 Apr 8 2020 VG710-Python-Templates
```
进入到“HelloWorld”项目目录中，输入如下信息，即可在VG710中运行实例
```
tmp/app #~> cd VG710-Python-Templates/src/
tmp/app/VG710-Python-Templates/src #~>python main.py

```
键盘输入<kbd>ctrl</kbd>+<kbd>C</kbd>,终止调试程序

实例测试无误后，即可将程序打包成二进制文件用于其他VG710使用


# 6、编译构建

在完成项目开发后，需要将源代码编译成二进制用于安装在工程项目中其他VG710网关中，编译打包过程在VG710中完成，打包路径及命令如下：

terminal show：

```python
/tmp/app/VG710-Python-Templates $ cd ..               # 返回到上一级目录
/tmp/app $ build_py_app.sh VG710-Python-Templates     # 执行构建编译
build APP:VG710-Python-Templates pkg!                 # 构建开始
generate APP pkg:
build APP:VG710-Python-Templates pkg finished!        # 完成构建
/tmp/app $ cd VG710-Python-Templates/build/           # 进入到VG710-Python-Templates中build文件夹
/tmp/app/VG710-Python-Templates/build $ ls            # 查看是否生成二进制包
VG710-Python-Templates-V0.2.0.tar.gz                  # 构建成功的二进制包
/tmp/app/appname/build $ 
```
# 6、获取二进制包并在另一台VG710中安装应用程序

在左侧“EXPLORER”空白处点击鼠标右键，选择<kbd>Download Folder</kbd>将二进制文件回传到本地PC中。成功回传后项目目录会新增*.tar.gz文件，如下：

```json
  VG710-Python-Templates
  ├── .vscode
  │  └── sftp.json
  ├── build
  ├──└──VG710-Python-Templates-V0.2.0.tar.gz      #二进制文件
  ├── src
  │  │── main.py
  │  └── parse_config.py
  ├── config.yaml
  ├── setup.py
```

以上完成了对VG710通过python进行二次开发的连接，开发，调试，打包；可将*.tar.gz应用程序二进制包安装在其他VG710网关中，详细步骤请参考“VG710用户手册”