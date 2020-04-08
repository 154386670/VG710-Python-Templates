<p align="center">
  <img width="600" src="https://www.inhandnetworks.com/upload/image/201904/28/0300230504.jpg">
</p>


简体中文 | [English](./README.md)

## I. Introduction

VG710-Python-Templates is an in-vehicle edge computing solution. It is based on python3 and IoT. It uses the latest IoT architecture technology, has built-in rich API interfaces, refined rich business modules, and provided rich component functions. , It can help you quickly build customized business functions, I believe that no matter what your Internet of Things needs, this project can help the master to you

### Development process description

<kbd>VS Code IDE</kbd>---(sftp connect)---><kbd>VG710</kbd>---><kbd>Import Templates</kbd>

<kbd>Python Program design</kbd>---><kbd>Online debugging</kbd>

<kbd>Package binaries in VG710</kbd>---><kbd>Download and install binaries on other vg710</kbd>

## 2、 Environmental preparation

To use this template to quickly develop your connected car application, you must have the following conditions

### `1、1. InVehicle Gateway710, the vehicle gateway of Yinghantong, referred to as VG710 for short`

### `2. Internet of things sim card capable of accessing the internet`

### `3. A PC computer, Windows / MacOS / Linux, and has access to the Internet`

### `4. Make sure the following software is installed on your PC:`

&emsp;&emsp;*(4.1).[MicroSoft VS code IDE](https://code.visualstudio.com/Download/)*

&emsp;&emsp;*(4.2).[Python3.7.X](https://www.python.org/downloads/)*

### `5. Verify that the PC environment meets the requirements:`

&emsp;&emsp;*(5.1).Press <kbd>Win</kbd>+<kbd>R</kbd> ，Bring up the command prompt, enter python, and press Enter. The following message pops up, indicating that the Python operating environment is ready*

```cmd
    Python 3.7.4 (v3.8.1:1b293b6006, Dec 18 2019, 14:08:53)
    [Clang 6.0 (clang-600.0.57)] on win64
    Type "help", "copyright", "credits" or "license" for more information.
    >>>
```

&emsp;&emsp;*(5.2). Confirm the vs Code environment, and install the plug-in in the "extensions" of the vs Code ide to continue using*

&emsp;&emsp;&emsp;*(5.2.1).Python*

&emsp;&emsp;&emsp;*(5.2.1).Project Templates*

&emsp;&emsp;&emsp;*(5.2.1).SFTP*

&emsp;&emsp;*(5.3). VS Code environment confirmation, to complete the installation of VS code, you need to install the plug-in in "Extensions" of VS Code IDE to continue using*

&emsp;&emsp;&emsp;*(5.3.1)make sure “Python: select Interpreter” is Python 3.7.x*



## 三、VG710-Python-Templates Directory

This project has generated a complete development framework for you. The following is the directory structure of the entire project.

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



## 4. Development


# Open a command prompt window

  Windows 10 ----> <kbd>Win</kbd>+<kbd>R</kbd>

  MacOS10.14 ----> <kbd>command</kbd>+<kbd>Space</kbd>，Inputterminal.app

  Linux      ----> <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>T</kbd>打开新终端


```
# Take MacOS as an example, store files in the "Documents /" directory

  cd Documents/

# Clone project

  git clone https://github.com/154386670/VG710-Python-Templates.git

```

# 5. Modify the project name

&emsp;Modify the cloned template project to the name of the self-built project，Take "HelloWorld" as an example，Change the name of the "VG710-Python-Templates" project folder to "HelloWorld"

&emsp;The file directory is as follows：
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

# 5、 Import vg710 Python templates project into vs Code

&emsp;*(5.1) modify the project name in the code:*
```python

./Documents/HelloWorld/setup.py，Code snippet:
..
...
    rom setuptools import setup, find_packages
    setup(name='helloworld',          #Change "appName" to "HelloWorld"
        sdk_version='0.2.0',
        version='0.0.0',
        author='Inhand',
...
..
---------------------------------------------------------------------------
./Documents/HelloWorld/src/main.py，代码片段：
..
...
    app = APPConfig(name="appname")   #Change "appName" to "HelloWorld"
    app_config_file = app.get_app_cfg_file()
...
..
---------------------------------------------------------------------------

```
&emsp;*(5.2) Configure Sftp connection information:*


```json
./Documents/HelloWorld/.vscode/sftp.json

{
    "name": "Debug Server",
    "host": "192.168.2.1",                    #Vehicle gateway Ethernet address
    "protocol": "sftp",
    "port": 222,
    "username": "pyuser",
    "password":"VF7101937000028",             #Car gateway serial number
    "remotePath": "/var/user/app/appname",    #Modify "appname" to "HelloWorld"
    "uploadOnSave": true,
    "ignore":[
        ".vscode",
        ".git",
        ".DS_Store"
    ]
}
```



Copyright (c) 2020-present Xiaopeng Gou
