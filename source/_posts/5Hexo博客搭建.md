---
title: Hexo博客搭建
tags:
  - Hexo
  - 教程
categories:
  - 学习笔记
  - Hexo
abbrlink: 41646
date: 2020-07-17 16:49:51
---

## 前言

搭建这个网站的最开始的理由就是想找一个清净点的地方记录自己想记录的一些东西，并且不用有任何的担心文章会不会被删除之类的；所以不惜花费一点时间来搭建一个属于自己的主页，这样就可以~为所欲为~好好写博客了~

<!-- more -->

---

## Hexo搭建本地博客

Hexo是一个快速、简洁且高效的博客框架。Hexo使用Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

[hexo官方文档](https://hexo.io/zh-cn/docs/)

### 安装[git](https://git-for-windows.github.io/)

- 安装时一直下一步即可，若出现加入系统环境变量的选项，则需要勾选上，否则需要自己手动加入；
- 检验是否成功添加到环境变量：打开cmd，输入`git version`，若出现`git`的版本，则说明成功添加。

### 安装[nodeJs](https://nodejs.org/en/)(LTS为长期维护版本，Current为最新版)

- 安装时一直下一步，不过在 Custom Setup 这一步记得选`Add to PATH`，否则就需要自己手动添加到系统环境变量；
- 检验：打开cmd，输入`node`，若出现`node`的简介，则表示安装成功且成功添加到系统环境变量。

### 安装Heox

- 打开cmd；
- 输入`npm install -g hexo-cli`（通过`npm`安装`hexo`，`-g`为全局安装）；
- 等待安装成功即可。

### 创建博客

- 博客的初始化：`hexo init Blog` (这里的Blog为用于存放博客文件的地方，名字随意)；
  ![1M3ZOP](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102522.png)
- `cd Blog`；
- 安装npm相关组件：`npm inistall`；
  ![1M8Xb6](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102550.png)
- 生成静态页面：`hexo generate`或`hexo g`；
- 启动服务：`hexo server`或`hexo s`；
  此时就可以打开浏览器，输入`http://localhost:4000`查看效果，本地博客搭建成功。
  ![1MGeIS](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102628.png)

---

## 桥接到github

### 创建仓库

http://test.github.io
新建一个名为<你的用户名>.github.io的仓库，比如说，如果你的github用户名是test，那么你就新建test.github.io的仓库（必须是你的用户名，其它名称无效），将来你的网站访问地址就是 <http://test.github.io> 了，是不是很方便？

由此可见，每一个github账户最多只能创建一个这样可以直接使用域名访问的仓库。
![1MJwtS](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102712.png)

**几个注意的地方**：

- 注册的邮箱一定要验证，否则不会成功；
- 仓库名字必须是：username.github.io，其中username是你的用户名；
- 仓库创建成功不会立即生效，需要过一段时间，大概10-30分钟，或者更久。

创建成功后，默认会在你这个仓库里生成一些示例页面，以后你的网站所有代码都是放在这个仓库里啦。

### 配置github的 SSH key

为什么要配置这个呢？因为你提交代码肯定要拥有你的github权限才可以，但是直接使用用户名和密码太不安全了，所以我们使用ssh key来解决本地和服务器的连接问题。

**注意：本文是用 git bash 输入所有命令，用 cmd 可能会出错**
$ cd ~/. ssh

- 检查本机已存在的ssh密钥：`$ cd ~/. ssh` 如果提示：No such file or directory 说明你是第一次使用git。
- 创建SSH：`ssh-keygen -t rsa -C "邮件地址"` **注意：这里的邮件地址指的是你注册 github 的邮箱**;
- 然后连续3次回车，最终会生成一个文件在用户目录下，打开用户目录即`c:\Users\你的电脑用户名`，找到.ssh文件夹下的id_rsa.pub文件，记事本打开并复制里面的内容;
- 打开你的github主页，进入`个人设置 -> SSH and GPG keys -> New SSH key`

![1l0isU](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102734.png)

- 将刚复制的内容粘贴到key那里，title随便填，保存。
- 打开cmd，输入`ssh -T git@github.com`# 测试是否成功；

如果提示`Are you sure you want to continue connecting (yes/no)?`，输入`yes`，然后会看到：`Hi h0ryit! You've successfully authenticated, but GitHub does not provide shell access.`看到这个信息说明SSH已配置成功！

此时你还需要配置：

```bash
git config --global user.name "liuxianan"// 你的github用户名
git config --global user.email  "xxx@qq.com"// 填写你的github注册邮箱
```

### 修改站点配置

打开你的blog文件，找到_config.yml文件。修改：

```bash
deploy: 
    type: git  
    repository:https://github.com/YourgithubName/YourgithubName.github.io.git 
    branch: master
```

然后在站点文件夹目录下执行命令`npm install hexo-deployer-git --save`

这样，你的本地博客就可以通过`hexo d`命令部署到`github`上了。

## 第一篇博客

执行命令：

`hexo new Hexo博客搭建`

即会在目录`hexo\source\_posts`目录下看见文件`Hexo博客搭建.md`文件，编辑这个文件，写下你想写的内容，完成后再执行命令：

`hexo clean && hexo g && hexo d`

稍后即可在你的博客中看到自己写的文章啦。

---

## 后续

之前的博客搭建之初，对各个方面都不是很懂，因此对于博客的搭建以及美化优化做的并不是特别好；在经过一番思考过后，决定将博客的文件储存到服务器里，将博客的撰写以及上传工作都放到服务器里面，这样就不用担心文件的突然丢失了。同时也对博客的部署以及`NexT`模板的版本进行了更改，让我们有更好的体验~

## 桥接到Coding

由于`github`是国外网站，我们将博客部署到那里时，对其进行访问会很慢，所以我们将博客的托管平台进行了更改，国内小编知道的比较大的代码托管平台就只知道`Gitee`和`Coding`了，目前`Gitee`平台的企业版本才可以免费支持`Pages`服务中的自动部署以及自定义域名服务，而`Coding`平台中这些都免费支持（虽然他的缺点也有一些，但是这个符合我们的要求，所以就选择了它~）。

将博客托管到`Coding`平台其实和`Github`差不多，大概也就下面三步：

{% tabs qiaojiedcoding %}
<!-- tab 创建仓库 -->
这个应该不用多说了，很简单的，不过`Coding`里面有一点不一样的就是，首先是创建项目，项目里面可以创建个仓库，所以小伙伴们可以先创建一个项目，然后再创建相应的仓库，这里还有一点和`Github`不一样的就是，这里的仓库名字可以随意起~
<!-- endtab -->

<!-- tab 配置 SSH key -->

如图，

**代码仓库** –> **设置** –> **部署公钥**

![Ucl8eO](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102810.png)

在这里面配置好自己的公钥即可，公钥的生成方法以及查看方法前面有介绍到。

<!-- endtab -->

<!-- tab 开启静态网站服务 -->

如图，

**持续部署** –> **静态网站**

![U6vFAJ](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102844.png)

若是没有这个选项的话，则需要手动开启：

**项目设置** –> **项目与成员** –> **功能开关** –> **持续集成** –> **打开开关**

![U6xvLT](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730102912.png)

静态网站初始设置：

**网站名称**：随意

**部署来源**：本项目仓库

- **选择项目**：刚才创建的项目
- **选择仓库**：刚才创建的项目中的仓库

其他的选项都选择默认

![U6v9nU](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730103016.png)

确定后就你的博客就搭建完成啦，赶紧去它给你的网址去看看吧~

![UclmFJ](https://gitee.com/shuoshuoyun/picbed/raw/master/img//20200730103039.png)

这里小编的访问地址有两个，是因为小编自己绑定了域名~

{% note info icon %}

### 个性域名

大家可以自己去购买一个个性域名，这样会显得很不一样，而且也不用多少q~
{% endnote %}

<!-- endtab -->

<!-- tab 修改站点配置 -->
打开文件`blog/_config.yml`，修改：

```_config..yml
deploy: 
    type: git  
    repository: git@e.coding.net:YourTeamName/YourProjectName/YourRepositoryName.git 
    branch: master
```

最后，在`blog/`目录下执行命令`npm install hexo-deployer-git --save`

这样，你的本地博客就可以通过`hexo d`命令部署到`Coding`上了，从此再也不用担心国内访问速度啦。

<!-- endtab -->
{% endtabs %}

---

## 个性化设置

小编这次的个性化设置基本上参照`NexT`主题的官方文档设置的，传送门如下：

{% linkgrid %}
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
% Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
{% endlinkgrid %}

### 常规配置

`hexo/_config.yml`

```_config.yml
# Site
title:  # 博客标题
subtitle: ''  # 副标题
description: ''  # 描述
keywords:  # 关键字
author:  # 作者
language: zh-CN  # 语言 
timezone: ''  # 时区
```

## 更换主题

默认的主题感觉还是不喜欢，所以这里小编选用的是`NexT`主题；安装方式如下：

{% tabs genghuanzt %}
<!-- tab 最新版 -->

在`next/`下打开终端：

{% code %}
cd hexo
git clone https://github.com/next-theme/hexo-theme-next themes/next
{% endcode %}

<!-- endtab -->

<!-- tab 稳定版 -->

1. 前往`NexT`主题的版本发布页面前往选择下载：{% btn https://github.com/next-theme/hexo-theme-next/releases, NexT-Releases,  home fa-fw fa-lg, Hexo&NexT%}你需要的版本源代码（zip文件），例如： v8.0.0-rc.3

2. 将zip文件解压到主题文件夹目录下并重命名为`next`即可。

<!-- endtab -->

{% endtabs %}

安装完成主题后即可在文件`blog/_config.yml`中启用主题：

```_config.yml
theme: next
```

启用完成后就可以在命令端执行：`hexo s --debug`，然后在浏览器中打开网址：`http://localhost:4000`就可以看到修改完成后的`next`主题啦。

## ~~更换主题方案~~

**NexT官方主题配置更改方案已经更新，Next主题修改请移步至[官网文档](https://theme-next.js.org/)**

`next/_config.yml`

```_config.yml
# Schemes
# scheme: Muse
#scheme: Mist
#scheme: Pisces
scheme: Gemini
```

这里有四种主题方案，各位同学可自行选择~

## 精简静态文件

`next/_config.yml`

```_config.yml
# 生成静态文件后移除不必要的文件。
minify: true
```

## 更换网站图标

`next/_config.yml`

```_config.yml
favicon:
  small: /images/favicon-16x16-next.ico
  medium: /images/favicon-32x32-next.ico
  apple_touch_icon: /images/apple-touch-icon-next.png
  safari_pinned_tab: /images/logo.svg
  #android_manifest: /images/manifest.json
  #ms_browserconfig: /images/browserconfig.xml
```

将自己喜欢的图片在网站：{% btn http://www.bitbug.net/t, 比特虫, fas fa-bug fa-fw fa-lg, icon制作网站 %} 制作成`ico`图标，制作两个，一个16X16的，一个32X32的，放在`next/source/images`中，用其相对文件路径替换`favicon`中的`small`和`medium`后的默认路径。

## 网站底部

`next/_config.yml`

### 建站年份

```_config.yml
footer:
  # 建站年份，如果未启用，则默认未当前年份。
  since: 2019
```

### 底部图标

```_config.yml

  # 底部图标相关信息
  icon:
    # Icon 图标名字，详情见: https://fontawesome.com/icons
    name: fa fa-heartbeat
    # 设置图标是否开启动画
    animated: true
    # 改变图标颜色
    color: "#ff0000"

  # If not defined, `author` from Hexo `_config.yml` will be used.
  copyright:

```

### Powered by Hexo & NexT

```_config.yml
  # 是否开启：Powered by Hexo & NexT
  powered: true
```

### 备案信息

```_config.yml
  # 我们特有的备案信息选填项~详情见: http://www.beian.miit.gov.cn, http://www.beian.gov.cn
  # 网站备案
  beian:
    enable: true
    icp: 京ICP备1234567890号-1
    # The digit in the num of gongan beian.
    gongan_id: 1234567890
    # The full num of gongan beian.
    gongan_num: 京公网安备 1234567890号
    # The icon for gongan beian. See: http://www.beian.gov.cn/portal/download
    gongan_icon_url: /images/beian.png
```

## 深色模式

`next/_config.yml`

```_config.yml
# Dark Mode
darkmode: true
```

{% note warning %}

### Warning

请确保您的浏览器支持暗模式。
{% endnote %}

## 菜单栏设置

### 启用默认菜单栏

在`next/_config.yml`启用：

```_config.yml
menu:
  home: / || fa fa-home
  #about: /about/ || fa fa-user
  #tags: /tags/ || fa fa-tags
  #categories: /categories/ || fa fa-th
  #archives: /archives/ || fa fa-archive
  #schedule: /schedule/ || fa fa-calendar
  #sitemap: /sitemap.xml || fa fa-sitemap
  #commonweal: /404/ || fa fa-heartbeat
```

{% note warning %}

### Warning2

除了`home`和`archives`，其他的菜单启用时，都要手动添加其页面；如：

{% code %}
hexo new page about
{% endcode %}

{% endnote %}

### 添加自定义菜单

{% tabs tianjiazdycd %}
<!-- tab 第一步 -->

创建新的页面：

{% code %}
cd hexo-site
hexo new page custom-name
{% endcode %}

<!-- endtab -->

<!-- tab 第二步 -->
将自定义菜单添加进`hexo/_config.yml`的`menu`中：

{% code %}
menu:
  home: / || fa fa-home
  archives: /archives/ || fa fa-archive
  custom-name: /custom-name/ || fa fa-user
{% endcode %}

{% note success %}

#### 温馨提示

自定义菜单相应显示的小图标，如`home`的`fa fa-home`，同学们可以前往{% btn https://fontawesome.com/, Font Awesome, fas fa-flag fa-lg, Font Awesome 官网%}寻找自己喜欢的小图标换上。

{% endnote%}

<!-- endtab -->

<!-- tab 第三步 -->
为你的`custom-name`添加译文：

在`next/languages/zh-CN.yml`文件中的`menu`中添加：

{% code %}
menu:
	custom-name: 自定义名字
{% endcode %}

{% note info %}

因为我们启用的语言为`zh-CN`，因此需要在这里面添加`custome-name`相应的翻译，这样在博客中才会正确的显示我们自定义菜单的中文；否则就只会显示英文。

{% endnote%}

<!-- endtab -->

{% endtabs %}

### 添加二级子菜单

添加子菜单方式如下：

`next/_config.yml`

```_config.yml
menu:
  home: / || fa fa-home
  archives: /archives/ || fa fa-archive
  sub-menu:                                       # 一级子菜单
    default: /sub-menu/ || fa fa-book             # 一级子菜单的配置
    sub-sub-menu-1: /sub-sub-menu || fa fa-plug   # 二级一号子菜单的配置
    sub-sub-menu-2:                               # 二级二号子菜单
      default: /sub-suub-menu-2/ || fa fa-plug    # 二级二号子菜单配置
      sub-sub-sub-menu: /sub-sub-sub-menu || fa fa-search-plus
```

{% tabs tianjiaejzcd %}
<!-- tab 添加中文译文 -->
这里和添加自定义菜单时一样的，传送按钮{%btn #tianjiazdycd-3, 添加译文, , %}
<!-- endtab -->

<!-- tab 添加子菜单文件 -->
在目录`hexo/source/`下创建如下文件树：
{% code %}
sub-menu
    |
    |— index.md
    |— sub-sub-menu-1.md
    |— sub-sub-menu-2
             |
             |— index.md
             |— sub-sub-sub-menu.md

{% endcode %}

这里解释一下这些文件

- `index.md`：当前文件目录下的默认博客文件
- `sub-sub-menu-1.md`：二级一号子菜单的博客文件
- `sub-sub-sub-menu.md`：三级子菜单的博客文件

{% note primary %}

#### 温馨提示2

这些文件小编暂时没有找到使用`hexo`命令来生成二级及其以下子菜单级文件目录及文件的方法，所以同学们可以自己手动创建~

{% endnote%}

<!-- endtab -->
{% endtabs %}

### 链接持久化

在`Hexo`中当我们创建的博客名包含中文的名的时候，`url`链接地址经常会变成一串很长字符串，不利于博客的链接分享，以及搜索引擎搜索，我们可以通过安装其他的插件来解决这个问题。

1. 安装`url`地址持久化插件:

   `npm install hexo-abbrlink --save`

2. 配置文件`hexo/_config.yml`

   `permalink: :year/:month/:day/:abbrlink/`

## 参考文献

{% cq %}感谢这些作者的无私奉献！{% endcq %}

{% linkgrid %}
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /uploads/csdn.png
CSDN | https://blog.csdn.net/fake_hydra/article/details/82414965 | GitHub Pages自定义域名后每次hexo d都会失效解决 | /uploads/csdn.png
CSDN | https://blog.csdn.net/weixin_38788347/article/details/78154487 | hexo+github搭建免费个人博客 | /uploads/csdn.png
CSDN | https://blog.csdn.net/destinytaoer/article/details/78400023 | hexo + next主题高级配置 | /uploads/csdn.png
CSDN | https://blog.csdn.net/weixin_39345384/article/details/80785373 | Hexo框架下用NexT(v7.0+)主题美化博客 | /uploads/csdn.png
CSDN | https://blog.csdn.net/weixin_41800884/article/details/103750672 | 快速搭建博客：写作技巧 | /uploads/csdn.png
CSDN | https://blog.csdn.net/panchao888888/article/details/80666352 | Hexo博客NexT主题终极配置 | /uploads/csdn.png
CSDN | https://blog.csdn.net/loze/article/details/94210320 | Hexo+NexT（三）：Next主题配置详解 | /uploads/csdn.png
% Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /uploads/apple-touch-icon-next.png
{% endlinkgrid %}
