---
title: Pycharm部署项目
tags:
  - pycharm
  - 教程
categories:
  - 学习笔记
  - 教程
date: 2021-10-28 01:22:12
---

## 前言
`Pycharm` 作为一款优秀的编辑器，当让是自带的有将代码部署到服务器的功能了，特别是当我们遇到下面的情况时，相信它会给你带来惊喜~

<!-- more -->

当你面临下面三个问题的时候，你会怎么做呢？

 - 现在要运行一个耗时很长的代码，例如爬虫大量爬取，或者数据分析分析大量数据等，你是选择放自己电脑上跑，然后干等着还是...
 - 现在你想部署一个自己的小项目到服务器，但是目前还在开发中，随时会有很多的改动，你是准备每次改动都重新部署一次呢还是...
 - 现在你在做的一个项目只能运行于 `Unix` 系统，而你用的 `Windows` 系统，你想测试的时候是每次都手动上传到服务器还是...

上面这些类似的问题一般来说比较的费时间，麻烦；如果说，能让我们在自己的电脑上写代码，运行在服务器里面，那上面这些问题不久全部的解决了？正好， `Pycharm` 就有这样的功能！

## 工具与环境
 - 工具：`Pycharm` 专业版和 `python3.x`
 - 环境：`CentOS7.x / CentOS8.x` 或 `Ubuntu18.x` 等都可以，不过请预先装好所需要的 `python` 及其相关的模块

{% note warning %}
** `Pycharm` ** 一定要是专业版，社区版是不提供远程部署功能的
{% endnote %}

## 步骤
### 配置远程服务器信息
#### 打开配置界面
 - 打开 `Pycahrm`
 - 点击 `Tools` -> `Deployment` -> `configuration`

![202110281409124](https://image.pylover.net/img/202110281409124.png?imageMogr2/format/webp)

#### 新增一个配置
 - 这里我们添加一个 `SFTP`
![202110281411033](https://image.pylover.net/img/202110281411033.png?imageMogr2/format/webp)

 - 给自己远程环境起个名字

![202110281411049](https://image.pylover.net/img/202110281411049.png?imageMogr2/format/webp)

#### 开始配置
 - 开始配置信息

![202110281417420](https://image.pylover.net/img/202110281417420.png?imageMogr2/format/webp)

上面这张图都好说，不过要介绍一下这个新增 `SSH` 配置，点击那三个小点
{% note info no-icon 新增 `SSH` 配置 %}
##### 新增配置 (No icon)
![202110281430817](https://image.pylover.net/img/202110281430817.png?imageMogr2/format/webp)

 - 连接成功

![202110281432293](https://image.pylover.net/img/202110281432293.png?imageMogr2/format/webp)
{% endnote %}

 - `SSH` 配置成功

![202110281433106](https://image.pylover.net/img/202110281433106.png?imageMogr2/format/webp)

 - 路径映射配置

![202110281436119](https://image.pylover.net/img/202110281436119.png?imageMogr2/format/webp)

 - 排除路径配置

![202110281438582](https://image.pylover.net/img/202110281438582.png?imageMogr2/format/webp)

 - 配置成功后ok就行了

![202110281441432](https://image.pylover.net/img/202110281441432.png?imageMogr2/format/webp)

 - 浏览远程文件

![202110281447879](https://image.pylover.net/img/202110281447879.png?imageMogr2/format/webp)

### 配置远程python解释器
上述我们只是配置了远程服务器信息,但是并没有让 `pycharm` 指定 `python` 解释器

 - `File` -> `Setting` -> `Project:项目名称` -> `Python Interpreter` -> `Add`

![202110281452930](https://image.pylover.net/img/202110281452930.png?imageMogr2/format/webp)

 - 选择 `SSH Interpreter` 后，选择我们之前已经配置好的现成的 `SSH` 配置

![202110281453220](https://image.pylover.net/img/202110281453220.png?imageMogr2/format/webp)

 - 选择服务器上 `Python` 解释器的位置,,然后点击 `Finish`

![202110281455991](https://image.pylover.net/img/202110281455991.png?imageMogr2/format/webp)

 - 指定解释器为远程解释器,,然后点击Apply,ok

![202110281456827](https://image.pylover.net/img/202110281456827.png?imageMogr2/format/webp)



## 参考文章

{% linkgrid %}
微信文章 | https://mp.weixin.qq.com/s/ULatzjyeS433CrvSzpSY5Q | 手把手教你用Pycharm连接远程Python环境 | /uploads/wechat.png
{% endlinkgrid %}
