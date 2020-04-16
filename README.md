<p align="center">
  <img width="600" src="https://www.inhandnetworks.com/upload/image/201904/28/0300230504.jpg">
</p>


简体中文 | [English](./README.md)

# 1、Introduction

The VG710-Python-Templates is an in-vehicle edge computing solution. It is based on Python3 and the latest IoT architecture technologies. It has rich built-in APIs, a wealth of business modules and functional components to help you quickly build customized business functions. No matter what you IoT needs are, this solution can provide help.

# 2、System Requirements

## 2.1 Hardware Requirements

&emsp;&emsp;*--> InVehicle Gateway710, or VG710 in short

&emsp;&emsp;&emsp;<font color=#ff000>★</font>VG710 firmware: [VG7-V1.0.0.rxxxx.bin](https://github.com/154386670/VG710-Python-Templates/releases)

&emsp;&emsp;&emsp;<font color=#ff000>★</font>VG710 Python SDK:[py3sdk-V1.x.x_Edge-VG9.zip](https://github.com/154386670/VG710-Python-Templates/releases)

&emsp;&emsp;&emsp;<font color=#ff000>★</font>Ensure that “Enable IDE debugging” is checked in <kbd>APP Management</kbd> in the VG710 configuration interface. 

&emsp;&emsp;&emsp;Note: For the purpose of device security, debugging mode will be automatically disabled after the device restarts. If you need to reconnect, please check “Enable IDE debugging” again.

&emsp;&emsp;*--> A computer, with Windows, MacOS or Linux, that is connected to VG710 via RJ45 or Wi-Fi.*

*<font color=#ffff4>&emsp;&emsp;&emsp;For better programming experience, it is recommended to insert an IoT SIM card in the VG710 and connect it to the Internet.</font>*

## 2.2 Software Requirements of PC

&emsp;&emsp;*--> [Python3.7.X](https://www.python.org/downloads/)*

&emsp;&emsp;*--> [MicroSoft VS code IDE development tool](https://code.visualstudio.com/Download/)*

&emsp;&emsp;VS Code must-have plugins:：

&emsp;&emsp;&emsp;*<1>.Python*

&emsp;&emsp;&emsp;*<2>.SFTP*

&emsp;&emsp;&emsp;[*VS Code plugin installation method *](https://code.visualstudio.com/docs/editor/extension-gallery)

# 3、Get the VG710-Python-Templates Example Project

&emsp;&emsp;Take MacOS for example, the file is stored in the "Documents/" directory.
```
cd Documents/
```
&emsp;&emsp;Clone the project.
```
git clone https://github.com/154386670/VG710-Python-Templates.git
```

## VG710-Python-Templates File Description

This project has generated a complete development framework for you. The following is the directory structure of the entire project.
```
VG710-Python-Templates         # Project name
├── .vscode                    # VS Code configuration folder
│  └── sftp.json               # SFTP plugin configuration file
├── build                      # App release package folder
├── src                        # App source code folder
│  │── main.py                 # App program entrance
│  └── parse_config.py         # Parse App configuration file
├── config.yaml                # App configuration file
└── setup.py                   # App version, SDK version and other information
```

# 4、Modify the File

## You need to modify the following three files with the actual project content.

&emsp;<font color=#ffff4>Note: There must be no space in contents in the quotation marks.</font>

```python
1.VG710-Python-Templates/setup.py，# Code snippet：
..
...
    rom setuptools import setup, find_packages
    setup(name='VG710-Python-Templates',          #Project name
        sdk_version='0.2.0',
        version='0.0.0',
        author='Inhand',
...
..
2.VG710-Python-Templates/src/main.py，# Code snippet：
..
...
    app = APPConfig(name="VG710-Python-Templates")   #Project name
    app_config_file = app.get_app_cfg_file()
...
..

3.VG710-Python-Templates/.vscode/sftp.json. # Code snippet：
{
    "name": "Debug Server",
    "host": "192.168.2.1",                            # VG710 IP address
    "protocol": "sftp",
    "port": 222,
    "username": "pyuser",                             # SFTP username, the default is pyuser, please do not change
    "password":"VF7101937000028",                     # SFTP password
    "remotePath": "/var/app/VG710-Python-Templates",  # Project name
    "uploadOnSave": true,
    "ignore":[
        ".vscode",
        ".git",
        ".DS_Store"
    ]
}
```
*<font color=#ffff4>Note: SFTP password is the 15-digit serial number of the VG710.</font>*

# 5.Establish SFTP Connection：

In the VS Code toolbar, click <kbd>View</kbd> in the menu bar, select <kbd>Command Palette</kbd>, and enter the following in the pop-up box:

```
>SFTP:Open SSH in Terminal    # Start SFTP service
```

Press <kbd>enter</kbd> on the keyboard, then the drop-down list will prompt the following information:

```json
Debug Server 192.168.2.1              # IP address is the "host" address in file "sftp.json" in the previous step.
```
After confirming that it is correct, press <kbd>enter</kbd>, and then follow the steps below on the VS Code "Terminal" interface:

&emsp;1. When connecting for the first time, the "Terminal" will prompt you whether you want to continue to connect, enter "yes" and press <kbd>enter</kbd> on the keyboard;

&emsp;2.Then the “Terminal” window will prompt you to enter the password, the password is the 15-digit serial number of the VG710;

&emsp;3. After entering the password, click <kbd>enter</kbd>. When the "Terminal" prompts the following information, it means that VS Code has successfully established an SFTP connection with the VG710.

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
/tmp/app $                  # This directory is the VG710 file directory.

```
# 6、Upload the Debugger to VG710

After completing code modification, right click the mouse in the blank area of "EXPLORER" on the left side of VS Code, select <kbd>Sync Local->Remote</kbd> to synchronize the code to VG710. As shown below:

<p align="center">
  <img width="800" src="https://github.com/154386670/VG710-Python-Templates/blob/master/picture/Remote_file.png">
</p>

```
cd /var/app/
/tmp/app $ ls
```
The returned information contains the project directory, as follows:
```python
VG710-Python-Templates
```
Go to "VG710-Python-Templates" project directory, enter the following information to run the program in VG710
```
tmp/app #~> cd VG710-Python-Templates/src/
tmp/app/VG710-Python-Templates/src #~>python main.py

```

Enter <kbd>ctrl</kbd>+<kbd>C</kbd> on the keyboard to terminate the debugger.

After the program passes the test, it can be packaged into a binary file for use on the other VG710.


# 7、Compile and Build

## 7.1 Package the VG710-Python-Templates Project in VG710

After the development is completed, the source code needs to be compiled into a binary file for installation in other VG710 gateways in the project. The compilation and packaging process are to be completed in VG710. The packaging path and commands are as follows:

terminal show：

```python
/tmp/app/VG710-Python-Templates $ cd ..               # Return to previous directory
/tmp/app $ build_py_app.sh VG710-Python-Templates     # Perform build compilation
build APP:VG710-Python-Templates pkg!                 # Start building
generate APP pkg:
build APP:VG710-Python-Templates pkg finished!        # Finish building
/tmp/app $ cd VG710-Python-Templates/build/           # Go to the build folder in VG710-Python-Templates
/tmp/app/VG710-Python-Templates/build $ ls            # Check whether the binary package is generated
VG710-Python-Templates-V0.2.0.tar.gz                  # Binary package successfully built
/tmp/app/appname/build $ 
```

As show below: 
<p align="center">
  <img width="800" src="https://github.com/154386670/VG710-Python-Templates/blob/master/picture/Download_file.png">
</p>

## 7.2 Get the Binary Package and Install the Application in Another VG710

Right click the mouse in the blank area of "EXPLORER" on the left side (as shown in the figure above) and select <kbd>Download Folder</kbd> to transfer the binary file back to the local computer. After transferring successfully, a * .tar.gz file will be added to the project directory, as show below:


```json
  VG710-Python-Templates
  ├── .vscode
  │  └── sftp.json
  ├── build
  ├──└──VG710-Python-Templates-V0.2.0.tar.gz      # Binary file
  ├── src
  │  │── main.py
  │  └── parse_config.py
  ├── config.yaml
  ├── setup.py
```

The above completes the connection, development, debugging, and packaging of VG710 secondary development through Python. The VG710-Python-Templates-V0.2.0.tar.gz application binary package can be installed in other VG710 gateways, please refer to the "VG710 User Manual" for detailed steps.

Copyright (c) 2020-present XiaoPengGOU