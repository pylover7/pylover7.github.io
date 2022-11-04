---
title: 奇妙的Python库
tags:
  - python
  - package
categories:
  - 学习笔记
  - python
date: 2021-10-30 13:33:54
---

## 前言
`Python` 中有很多奇妙且好用的第三方库，可以让你的任务变得更为容易，下面给大家收集一些好用的 `Python` 库，每一个都很不错的哟~
<!-- more -->

## 酷酷的库
### socket
获取本机的局域网 `IP` 地址
```python
import socket as f

hostn = f.gethostname()
Laptop = f.gethostbyname(hostn)
print("你的电脑本地IP地址是：" + Laptop)

# 你的电脑本地IP地址是：192.168.2.101
```

当然我们的目的是获取本机的公网 `IP`，不过这个已经和这个库没有什么关系了，是借助一个  {% btn https://jsonip.com, 其他网站, fas fa-globe %}  来实现的
```python
import json
from urllib.request import urlopen

# 全局取消证书验证
import ssl
ssl._create_default_https_context = ssl._create_unverified_context


with urlopen(r'https://jsonip.com') as fp:
    content = fp.read().decode()

ip = json.loads(content)['ip']
print("你的电脑公网IP地址是：" + ip)

# 你的电脑公网IP地址是：120.236.128.201
```

### pyshorteners
`pyshorteners` 是一个简单的 URL 缩短的库，提供了18种短链根域名供使用。

![](https://image.pylover.net/img/202110301403572.png?imageMogr2/format/webp)

这里以 `clck.ru` 格式为例。

```python
import pyshorteners as psn

url = "http://www.shuhai.com/"
u = psn.Shortener().clckru.short(url)
print(u)

# https://clck.ru/WPJgg
```

### fabulous
添加文本颜色，如果你是在命令行上运行Python程序，那么输出都是相同颜色，不方便观察。

使用 `Fabulous`，则可以添加图像、彩色文本来凸显输出。

![](https://image.pylover.net/img/202110301407629.png?imageMogr2/format/webp)

示例：
```python
from fabulous.color import bold, magenta, highlight_red

print(bold(magenta(
    """
    hello world
    this is some new line
    and here is the last line. :)
    """
)))
```

结果如下，输出字体加粗且有颜色。
![](https://image.pylover.net/img/202110301410131.png?imageMogr2/format/webp)


## 参考文章

{% linkgrid %}
微信文章 | https://mp.weixin.qq.com/s/5RZYPySM0GYSTwbvqyxK1A | 这10个奇妙的Python库，你必须要试试！ | /uploads/wechat.png
{% endlinkgrid %}
