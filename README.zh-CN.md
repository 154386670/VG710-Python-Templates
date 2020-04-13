<p align="center">
  <img width="600" src="https://www.inhandnetworks.com/upload/image/201904/28/0300230504.jpg">
</p>


简体中文 | [English](./README.md)

# 1、简介

VG710-Python-Templates是一个车载边缘计算解决方案，它基于python3和IoT实现，它使用了最新的物联网架构技术，内置了丰富的API接口，提炼了丰富的业务模块，提供了丰富的组件功能，它可以帮助你快速搭建定制化业务功能，相信不管你的物联网需求是什么，本项目都能够帮主到你

# 2、环境准备

## 2.1 硬件环境

&emsp;&emsp;*--> 映翰通的车载网关InVehicle Gateway710，简称VG710*

&emsp;&emsp;&emsp;&emsp; <font color=#ff000>★★★</font>确保VG710配置界面中<kbd>APP管理已勾选</kbd>“开启IDE调试”模式

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

# 5、涉及的命令

在完成项目开发后，需要将源代码编译成二进制用于安装在工程项目中其他VG710网关中，编译打包过程在VG710中完成，打包路径及命令如下：
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