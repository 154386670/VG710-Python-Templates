<p align="center">
  <img width="600" src="https://www.inhandnetworks.com/upload/image/201904/28/0300230504.jpg">
</p>


简体中文 | [English](./README.md)

## 一、简介

VG710-Python-Templates是一个车载边缘计算解决方案，它基于python3和IoT实现，它使用了最新的物联网架构技术，内置了丰富的API接口，提炼了丰富的业务模块，提供了丰富的组件功能，它可以帮助你快速搭建定制化业务功能，相信不管你的物联网需求是什么，本项目都能够帮主到你

## 二、环境准备

要使用该模板快速开发您的车联网应用，你必须具备以下条件

### `1、映翰通的车载网关InVehicle Gateway710，简称VG710`

### `2、能够接入internet的物联网卡`

### `3、一台PC电脑，Windows/MacOS/Linux,并且已经接入Internet`

### `4、确保您的PC已经安装了以下软件：`

&emsp;&emsp;*(4.1).[MicroSoft VS code IDE开发工具](https://code.visualstudio.com/Download/)*

&emsp;&emsp;*(4.2).[Python3.7.X](https://www.python.org/downloads/)*

### `5、验证PC环境是否满足要求：`

&emsp;&emsp;*(5.1).按 Win+R 键，输入 cmd 调出命令提示符，输入python，回车，弹出如下信息则说明python运行环境已经准备好*

```
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


## 开发

```bash
# 克隆项目
git clone https://github.com/PanJiaChen/vue-element-admin.git

# 进入项目目录
cd vue-element-admin

# 安装依赖
npm install

# 建议不要直接使用 cnpm 安装依赖，会有各种诡异的 bug。可以通过如下操作解决 npm 下载速度慢的问题
npm install --registry=https://registry.npm.taobao.org

# 启动服务
npm run dev
```

浏览器访问 http://localhost:9527

## 发布

```bash
# 构建测试环境
npm run build:stage

# 构建生产环境
npm run build:prod
```

## 其它

```bash
# 预览发布环境效果
npm run preview

# 预览发布环境效果 + 静态资源分析
npm run preview -- --report

# 代码格式检查
npm run lint

# 代码格式检查并自动修复
npm run lint -- --fix
```

更多信息请参考 [使用文档](https://panjiachen.github.io/vue-element-admin-site/zh/)

## Changelog

Detailed changes for each release are documented in the [release notes](https://github.com/PanJiaChen/vue-element-admin/releases).

## Online Demo

[在线 Demo](https://panjiachen.github.io/vue-element-admin)

## Donate

如果你觉得这个项目帮助到了你，你可以帮作者买一杯果汁表示鼓励 :tropical_drink:
![donate](https://panjiachen.github.io/donate/donation.png)

[更多捐赠方式](https://panjiachen.gitee.io/vue-element-admin-site/zh/donate)

[Paypal Me](https://www.paypal.me/panfree23)

[Buy me a coffee](https://www.buymeacoffee.com/Pan)

## 购买贴纸

你也可以通过 购买[官方授权的贴纸](https://smallsticker.com/product/vue-element-admin) 的方式来支持 vue-element-admin - 每售出一张贴纸，本项目将获得 2 元的捐赠。

## Browsers support

Modern browsers and Internet Explorer 10+.

| [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/edge/edge_48x48.png" alt="IE / Edge" width="24px" height="24px" />](https://godban.github.io/browsers-support-badges/)</br>IE / Edge | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/firefox/firefox_48x48.png" alt="Firefox" width="24px" height="24px" />](https://godban.github.io/browsers-support-badges/)</br>Firefox | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/chrome/chrome_48x48.png" alt="Chrome" width="24px" height="24px" />](https://godban.github.io/browsers-support-badges/)</br>Chrome | [<img src="https://raw.githubusercontent.com/alrra/browser-logos/master/src/safari/safari_48x48.png" alt="Safari" width="24px" height="24px" />](https://godban.github.io/browsers-support-badges/)</br>Safari |
| --------- | --------- | --------- | --------- |
| IE10, IE11, Edge| last 2 versions| last 2 versions| last 2 versions

## License

[MIT](https://github.com/PanJiaChen/vue-element-admin/blob/master/LICENSE)

Copyright (c) 2017-present PanJiaChen
