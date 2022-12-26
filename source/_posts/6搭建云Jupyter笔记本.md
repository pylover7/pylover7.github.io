---
title: 搭建云Jupyter笔记本
tags:
  - jupyter
  - 教程
categories: 
    - 学习笔记
    - jupyter
abbrlink: 57078
date: 2020-07-23 15:05:25
---



## 前言

最近学习`python`用到了`jupyter notebook`编辑器；但由于环境原因，并不能一直在自己的笔记本上完成学习，很多时候需要在**别的、没有`python`环境的、但是有网络的**地方，这时候我们想学习`python`的时候就比较犯难，没有工作环境，怎么办？当然是问度娘咯，于是小编这就找到了这个搭建云`jupyter`笔记本的方法，搭建完成以后，嗯~相当舒服，有浏览器有网络的地方就可以开始码代码了，，

<!-- more -->

## 前期准备工作

{% note success %}

这里的前期准备工作是用于介绍服务器相关的，如果已经有一台服务器的同学可以忽略不计直接跳到{% btn #安装, 下一节 %}去看。

{% endnote %}

首先，我们搭建一个云`jupyter`笔记本，就需要一台云服务器；目前比较大的厂商有阿里云、腾讯云和百度云，这里小编只是介绍一下小编是如何白嫖这些厂商的服务器的~

{% tabs fuwuqi %}

<!-- tab 阿里云 -->

为什么小编会把阿里云放在第一个呢，因为阿里云目前有一个{% btn https://developer.aliyun.com/adc/student/?utm_content=g_1000107876&from=groupmessage&share_source=wechat, 阿里云高校学生计划, fas fa-cloud-upload-alt fa-fw, %}，这个计划可以让在校大学生白嫖一台六个月的服务器，你说香不香呢~重点是，如果你在这六个月内没有毕业，通过他们相关的考核即可免费再嫖六个月！！！一共就是一年！这可是一大好机会呀。

{% note info %}

这里需要注意一点的就是，想领取这个服务器的必须目前该账号没有其他的服务器；如果有，那就是领取不了的。

{% endnote %}

领取后的服务器是固定配置，自选选项比较少，大家可以根据自己的需要选择；不过这个配置对于我们仅仅只是自己搞学习的学生党来说，还是不错的（毕竟我们自己买的话一般运行内存就买1G的，这个有2G）。

安装的系统小编选择的是`Ubuntu`，因为刚开始学的时候就是学的这个系统，用起来比较顺手一点；当然，其他的系统都可以，看个人。

其他的白嫖项呢，就是一个新用户可以免费使用指定范围内的服务器一个月还是三个月，不记得了，同学们可以自己去体验一下。

{% note info%}

领取这些试用的服务器都是要实名认证的哦。

{% endnote %}

<!-- endtab -->

<!-- tab 腾讯云 -->

同样，新用户注册可以免费领取一个月的免费服务器一台，不过值得一提的是，腾讯云的服务器学生价是真的低，就几块钱一个月~

<!-- endtab -->

<!-- tab 百度云 -->

这个小编注意的少，不过也是注册并实名认证就可以免费领取一个月的服务器了~

<!-- endtab -->

{% endtabs %}

## 安装

{% note info %}

### 温馨提示

本次我们要搭建的是云笔记本，所以大家需要有一台云服务器哦；关于云服务器的获取{% btn #前言, 上一节 %}有介绍，有需要的小伙伴可以看看。

{% endnote %}

`jupyter notebook`的安装方式有两个选择，一个是安装`Anaconda`，里面会自带有`jupyter`工具；或者直接使用`python`中的`pip`安装。

{% tabs anzhuang %}

<!-- tab Anaconda -->

{% subtabs anacondaanzhuang %}

<!-- tab 下载 -->

在{% btn https://www.anaconda.com/products/individual%, Anaconda 官网 %}中下载安装脚本，然后上传到服务器内，或者直接在服务器终端中使用命令下载：

`wget https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh`

<!-- endtab -->

<!-- tab 安装 -->

切换到刚才下载了`anaconda`脚本的目录下，运行脚本：

`bash Anaconda3-2020.02-Linux-x86_64.sh`

后面就是有`Enter`的按`Enter`，有需要输入`yes`的输入`yes`；当看到

`Thank you for installing Anaconda3!`

就表示你已经安装成功了！

<!-- endtab -->

<!-- tab 检验 -->

在终端中输入：

`conda --version`

若显示了`conda`的版本信息，则表示安装成功了，但如果系统提示：

`conda: command not found`

那就执行一下以下命令：

`source /root/.bashrc`

就可以了，然后再进行版本信息验证。

<!-- endtab -->

{% endsubtabs %}
<!-- endtab -->

<!-- tab Python -->

最新版的`Ubuntu`系统已经预装了`Python2.7`和`Python3.5`版本了，若是小伙伴们还需要其他的版本，可以自行问问度娘，这里我们就不多加赘述了。

有了`python`，安装`jupyter`便是非常简单的事情了，执行以下命令：

`pip install jupyter`

等待一小会儿，就可以安装好了。

{% note warning %}

### jupyter command not found

可能有些小伙伴在安装完成后回出现这个问题，这里我们就一并解决了吧~当然，没有出现这个问题更好。

首先我们寻找`juputer`是否存在，使用命令：

`find -name jupyter`

小编这里的返回结果如下：

{% code %}

./.local/share/jupyter
./.local/bin/jupyter
./.local/etc/jupyter

{% endcode %}

{% note info %}

这里的`bin`目录即是存放命令的目录，所以我们只要把这个加入环境变量即可.

{% endnote %}

这就表示我们已经安装好了`jupyter`了的，因此就需要把它加入到环境变量中，

打开配置文件：

`sudo vim /etc/profile`

添加如下信息：

`export PATH=$PATH:~/.local/bin`

退出编辑：

`Esc`+`:wq`+`Enter`

执行配置：

`source  /etc/profile`

这个时候再在终端中输入`jupyter`即可返回一大段的命令提示符，这时候输入`jupyter notebook`即可打开。

{% endnote %}

<!-- endtab -->
{% endtabs %}

## 配置

{% tabs jupyterpeizhi %}

<!-- tab 生成配置文件 -->

在终端中执行以下命令：

`jupyter notebook --generate-config`

即可生成`jupyter notebook`的配置文件，并且会返回这个文件所在的路径，小编的路径如下：

`/home/deepin/.jupyter/jupyter_notebook_config.py`

<!-- endtab -->

<!-- tab 修改配置文件 -->

执行命令：

`vi /home/deepin/.jupyter/jupyter_notebook_config.py`

在文件最上面添加如下代码：

{% code %}

c.NotebookApp.ip = '*'  # 允许访问此服务器的 IP，星号表示任意 IP
c.NotebookApp.open_browser = False # 运行时不打开本机浏览器
c.NotebookApp.port = 8888 # 使用的端口
c.NotebookApp.enable_mathjax = True # 启用 MathJax
c.NotebookApp.notebook_dir = '/root/jupyter'      # 存放文件的目录
c.NotebookApp.allow_remote_access = True     # 允许远程访问

{% endcode %}

修改完成后保存推出即可；

小伙伴们可以参考如上代码进行修改，若有其他需求则可以自行阅读配置文件进行修改。

<!-- tab 设置密码并启动服务 -->

密码设置命令：

`jupyter notebook password`

然后输入密码回车再次确认即可，

最后输入`jupyter notebook`启动服务。

<!-- endtab -->

{% endtabs %}

至此我们搭建云`Jupyter`笔记本的教程就大概结束了，没有别的需求的小伙伴们就可以通过访问`http://服务器IP地址:8888`来访问你的`jupyter`啦（记得去服务器控制台将8888端口打开~），而且是随时随地的访问，是不是很方便呢，又可以开心的继续写代码了呢：）

## 修改语言

小伙伴们打开`jupyter`后会发现，这个编辑器的默认语言是英语，，，可能某些英语底子不大好的同学看着就有点头疼（小编就是。。。），所以，小编在网络上疯狂寻找如何修改`jupyter`编辑器的语言教程，终于在某个深山老林里面找到了此等秘籍！

{% note success %}

`jupyter notebook`的默认语言是跟随启动`jupyter`时终端的语言。

{% endnote %}

因此，我们只需要将我们服务器的终端语言修改，那么启动后的`jupyter`就是我们想要的了；

这里，我们当然是将语言修改成中文咯，不然第一次用这个编辑器的小伙伴可能都不知道咋整~

{% tabs xiugaiyuyan %}

<!-- tab 查看本地语言包 -->

查看本地语言包命令：

`locale -a`

寻找是否有`zh_CN.utf8`

如果没有，首先需要安装中文语言包，命令如下：

`sudo apt-get install language-pack-zh-hans`

然后添加中文支持：

`locale-gen zh_CN.UTF-8`

<!-- endtab -->

<!-- tab 修改配置 -->

打开文件：

`vim /etc/default/locale`

将配置文件修改为：

{% code %}

LANG="zh_CN.UTF-8"
LANGUAGE="zh_CN:zh:en_US:en"
LC_NUMERIC="zh_CN.UTF-8"
LC_TIME="zh_CN.UTF-8"
LC_MONETARY="zh_CN.UTF-8"
LC_PAPER="zh_CN.UTF-8"
LC_IDENTIFICATION="zh_CN.UTF-8"
LC_NAME="zh_CN.UTF-8"
LC_ADDRESS="zh_CN.UTF-8"
LC_TELEPHONE="zh_CN.UTF-8"
LC_MEASUREMENT="zh_CN.UTF-8"
LC_ALL=zh_CN.UTF-8

{% endcode %}

保存退出。

<!-- endtab -->

<!-- tab 重启 -->

重启服务器：

`reboot`

<!-- endtab -->

{% endtabs %}

## 配置个性域名

我们搭建好的云`jupyter`如果只是用我们服务器的IP地址来访问，显的确实有点点不大好看，因此，我们将介绍一下如何给我们的云`jupyter`配置一个个性域名。

{% tabs gexingyuming %}

<!-- tab 购买域名 -->

小伙伴们可以前往各大厂商（阿里云，百度云，腾讯云等）进行购买，很多域名的首年只需要个位数的价格，买来玩还是可以的~

![图片1](https://image.pylover.net/img/202110280019025.png)

有自己的域名感觉倍儿有格调~

<!-- endtab -->

<!-- tab 申请SSL证书（可选） -->

{% note info %}

可能有些小伙伴不知道`SSL`证书是什么东西，用来干啥的，这里小编简单的解释一下，就是在访问你的域名的时候让你的域名前面有一个（绿色的）小锁头：

![图片2](https://image.pylover.net/img/202110280020664.png)

表示访问你这个网站是安全的。

{% endnote %}

`SSL`证书的种类：

{% subtabs zhengshuzhonglei %}

<!-- tab 单域名 -->

**保护一个**单页面网站，例如 `domain.com、ssl.domain.com、ssl.ssl.domain.com`

若是小伙伴们只是想弄个小锁头耍耍就只要申请一个这个即可。

{% note success %}

### 白嫖方法

以腾讯云为例（阿里云也有，百度云目前没发现白嫖方法）：

**登陆阿里云控制台** –>  **SSL证书** –> **购买证书**

![图片3](https://image.pylover.net/img/202110280025282.png)

![图片4](https://image.pylover.net/img/202110280025074.png)

以上即可购买一份免费的单域名证书了。

{% endnote %}

<!-- endtab -->

<!-- tab 通配符域名 -->

**大量子域名的超值**选择！一张证书可以同时保障多个子域名的安全加固！

例如：`*.aliyun.com`的通配符证书只能对`a.aliyun.com、b.aliyun.com`域名进行保护。如果存在`a.b.aliyun.com`的域名需要购买`*.b.aliyun.com`的通配符证书。

通配符域名证书基本上都需要购买，这个就是属于有需求且有能力的小伙伴选择购买了，毕竟也不便宜，，，

但是！！！

{% note warning %}

### 依旧能白嫖

有兴趣并且喜欢折腾的小伙伴们，给你们一个传送门：{% btn https://www.hi-linux.com/posts/6968.html, Let's Encrypt 免费通配符 SSL 证书申请教程 %}

同时，感谢这位作者，撒花~

{% endnote %}

<!-- endtab -->

<!-- tab 多域名 -->

**一张证书可以为多个独立域名提供安全保障。**

例如：一个多域名证书可以同时保障 aliyun.com、aliyunShop.com 和 taobao.com 的网站安全。

这个就是属于，，，反正不是属于小编这样子的人能购买的，，，而且，，，没有白嫖！

<!-- endtab -->

{% endsubtabs %}

<!-- endtab -->

<!-- tab 配置nginx -->

首先安装`nginx`：

`sudo apt-get install nginx`

安装完成后打开`nginx`配置文件所在目录：

`cd /etc/nginx`
`ls`

可以看到这里面已经有`nginx.conf`配置文件了

这里我们再新建一个配置文件：

`touch vhost.conf`

打开`nginx`配置文件：`sudo vim nginx.conf`，在`http`这个大花括号内最后一行添加一行：

`include /etc/nginx/vhost.conf; # 将我们刚才新建的配置文件包含进来`，然后保存；

再打开新建的配置文件：`sudo vim vhost.conf`，添加以下内容：

{% code %}

server {
    server_name xxx.com 123.123.123.123; # 服务器域名和 IP 地址
    listen 80;
    location / {
        root /var/www/notebook_ssl; # 此路径下放置一个 index.html，将连接转移到 https
    }
}

server {
    server_name xxx.com 123.123.123.123; # 服务器域名和 IP 地址
    listen 443;
    ssl on;
    ssl_certificate /etc/letsencrypt/live/xxx.com/fullchain.pem; # SSL 证书文件的路径
    ssl_certificate_key /etc/letsencrypt/live/xxx.com/privkey.pem; # SSL 密钥文件的路径
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;
    ssl_prefer_server_ciphers on;
    location / {
        proxy_pass http://127.0.0.1:8888/; # JUPYTER_PORT 为 Jupyter 运行端口
        proxy_set_header X-Real-IP $remote_addr;

​        proxy_set_header Host $host;

​        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

​  proxy_http_version 1.1;

​  proxy_set_header Upgrade $http_upgrade;
​        proxy_set_header Connection "upgrade";
​        proxy_redirect off;
​    }
}

{% endcode %}

保存退出后，执行命令：`service nginx restart`，重启`nginx`即可。

<!-- endtab -->

<!-- tab 域名解析 -->

打开**阿里云（百度云，腾讯云）控制台** –> **域名** –> **解析** –> **添加记录**

**记录类型**：A

**主机记录**：域名的前缀，随意选取，如`notebook`

**解析路线**：默认

**记录值**：你的服务器的IP地址

**TTL**：10分钟

<!-- endtab -->

{% endtabs %}

这样，我们就可以愉快的用自定义的域名地址：`https://notebook.域名`

来访问我们的`jupyter notebook`了

## 参考文献

{% cq %}感谢这些作者的无私奉献！{% endcq %}

{% linkgrid %}
CSDN | https://blog.csdn.net/ImAustin/article/details/103179826 | linux服务器安装Anaconda及配置Jupyter | /uploads/csdn.png
CSDN | https://blog.csdn.net/u012956394/article/details/88410416 | 在Google Cloud上部署深度学习环境，并为jupyter notebook配置域名https访问 | /uploads/csdn.png
CSDN | https://blog.csdn.net/BobYuan888/article/details/88662779 | Ubuntu修改终端下的语言（中文或英文） | /uploads/csdn.png
{% endlinkgrid %}
