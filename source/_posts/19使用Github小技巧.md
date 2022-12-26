---
title: 使用Github小技巧
tags:
  - github
categories:
  - 学习笔记
  - 小技巧
date: 2021-12-29 22:15:08
---

## 前言

在我们学习编程的过程中，一种比较高效的学习方法便是寻找一个合适当前的项目来练手，但是该怎么找呢？并且在这个知识日新月异的时代保持自己的知识不过时该怎么办呢？，下面我们就来介绍一下。

<!-- more -->

## 在 github 上高效的寻找项目

### 寻找

进入 `github` 官网，怎么搜索如下：
![图片1](https://image.pylover.net/img/202112292144375.png?imageMogr2/format/webp)

这里以搜索 `wechat` 为例：
![图片2](https://image.pylover.net/img/202112292147945.png?imageMogr2/format/webp)

在左边的语言分类中我们可以筛选自己学习的语言，这里我们以 `python` 为例：
![图片3](https://image.pylover.net/img/202112292149375.png?imageMogr2/format/webp)

这样我们搜出来的就全是关于 `python` 相关的项目

### 观察

下面是在看到一个项目的时候我们大概可以看一些一下的东西（随机挑选一个项目）：
![图片4](https://image.pylover.net/img/202112292152075.png?imageMogr2/format/webp)

![图片5](https://image.pylover.net/img/202112292153987.png?imageMogr2/format/webp)

上图可以看到，一个项目含有的基本信息，这些信息都可以通过搜索框来来匹配，从而更快的找到目标项目。通常星数，观看数，更新日期，表示了一个项目的火热程度。比如说我想搜索 readme 中含有 `web development` 关键字，主要编程语言为 `Python`，星数大于 3000 的项目，就可以这样搜索：

```re
"web development" in:readme language:python stars:>3000
```

搜索结果就只有 14 个，大大减轻了自己筛选的负担，结果如下：

![图片6](https://image.pylover.net/img/202112292156900.png?imageMogr2/format/webp)

### 搜索小技巧

#### 通过 `in` 关键字搜索

关键字 in 可以搜索出 GitHub 上的资源名称 name、说明 description 和 readme 文件中的内容。description 就是 About 那一块的信息。

比如说 `python in:name,description,readme` 其中，逗号分割表示或的意思，意思就是三者中只要有一个有 python 就行。

#### 通过 stars、fork 数量搜索

搜索 GitHub 时用 star 数量和 fork 数量判断这个项目是否优秀的标准之一，我们可以使用 大小，小于，范围等方式过滤：

`python in:name stars:>1000 forks:>500` 就表示星数大于 1000 且 forks 数大于 500，名字中含有 python 的项目。

如果要指定范围，可以这样：

`python in:name stars:5000..10000` 表示星数在 5000 到 10000 之间，名字中有 python 的项目。

#### 按创建、更新时间搜索

按创建、更新时间搜索可以把版本老旧的资源筛选出去，比如说:

- 按创建时间：`created:>=YYYY-MM-DD`

- 按更新时间：`pushed:>=YYYY-MM-DD`

比如说搜索 2021 年之后创建的 Python 项目：`python in:name created:>=2021-01-01 pushed:>=2021-01-01`

#### 按文件、路径内容搜索

在 GitHub 还可以按文件内容和文件路径搜索，不过有一定的限制，首先必须登录，此外项目的文件不能太多，文件不能太大，在需要搜索 fork 资源 时，只能搜索到 star 数量比父级资源多的 fork 资源，并需要加上 fork:true 查询，搜索结果最多可显示同一文件的两个分段，但文件内可能有更多结果，不能使用通配符。

语法格式：

- 按文件内容 `关键字 in:file`
- 按文件路径 `关键字 in:path`

比如：`python in:file,path`

#### 按文件名、大小、扩展名搜索

语法格式如下：

- 按文件名搜索：`关键字 filename:FILENAME`
- 按文件大小搜索：`关键字 size:>=大小`
- 按扩展名搜索：`关键字 extension:EXTENSION`

举个例子：`python filename:aaa size:>10 extension:py`
![图片7](https://image.pylover.net/img/202112292201595.png?imageMogr2/format/webp)

#### 按编程语言来搜索

语法格式：`关键字 language:LANGUAGE`

比如：`python language:javascript` 表示搜索 javascrip 语言中关于 python 的项目。

## 学习新技术

### 养成良好的习惯

感觉跟不上技术的进展，本质上还是离前沿太远，可能是因为业务繁忙，也有可能是因为找不到路子，但归根到底是因为没有养成良好的习惯。

每天给自己 15-30 分钟的 “扩展视野时间”，这个时间最好在早上。这个时间段你可以去访问 Github Trending 榜单，查看自己所在领域的技术进展：<https://github.com/explore>。

可以说 Github Trending 是一个类似今日头条的 Feed 流，你平时逛 Github 越多，关注的感兴趣的人越多，Star 的项目越多，你会发现这条 Feed 流会越智能，一旦你所在的领域有新鲜的技术项目出来，那么你只要刷一下这个 Feed 流，立马能够掌握到最新的前沿技术进展。

为什么让你刷 Trending 流，其实还有个原因就是，它不像抖音、今日头条是一个无限的黑洞，它是有限的，在一个时间段内它只会有几十条存在，而且可能绝大部分还一样，这样你就可以快速地了解最新的事情，不会因为 “日新月异” 而感到焦虑。

![图片8](https://image.pylover.net/img/202112292204508.png?imageMogr2/format/webp)

### 拓宽自己的“技术关系”

你喜欢 CSS 吗？CSS 领域最前沿的技术进展当属 TailwindCSS 这类 “实用类优先” 的 CSS 框架了，那我们可以做些什么来跟进它的技术进展呢？

首先，Star 这个项目。
![图片9](https://image.pylover.net/img/202112292207454.png?imageMogr2/format/webp)

然后，找到这个仓库的贡献者的前几名，关注他们！
![图片10](https://image.pylover.net/img/202112292207023.png?imageMogr2/format/webp)

可以看看大佬们是如何努力工作的，Github 几乎全绿！
![图片11](https://image.pylover.net/img/202112292207772.png?imageMogr2/format/webp)

当你关注他们之后，你一进入 Github 就可以在你自己的关注 Feed 流里面了解到这些人最近的动态，比如 Star 了哪些项目？Follow 了哪些人？发布了哪些包更新？久而久之，当你关注的人越来越多，你的个人关注 Feed 流就成为了你每天获取新技术信息的来源，站在这些 “巨人” 的肩膀上，获取高效的信息！
![图片12](https://image.pylover.net/img/202112292208052.png?imageMogr2/format/webp)

### 找到乐趣

这些大牛可能还会参与一些其他的项目，或者加入或创建了一些其他的 Github 组织，尝试顺着这些项目、组织，进行二次探索，继续 Star 更多的项目、Follow 更多的人，然后慢慢找到自己的兴趣点，并以此兴趣点为基础，在某 1 个开源项目驻足下来，尝试为其进行贡献，如改个文档的拼写问题，帮助翻译，或者开始尝试看源码，修复一些 BUG 或者提交一些代码贡献。

当你花了足够长的时间在这个上面之后，你会发现突然某一天，你的提交被某个大牛合并进了仓库，你成为了某知名开源项目的 Contributor ！🎉 这个幸福感是不言而喻的。

比如给 Vite 提交一些极小的改进：<https://github.com/vitejs/vite/pull/6083/files>。
![图片13](https://image.pylover.net/img/202112292208052.png?imageMogr2/format/webp)

### 开始耕耘自己的领地

如果你能坚持经历上面几个阶段，那么你现在可能 Follow 了很多 “技术明星”，Star 了很多感兴趣的项目，你的个人关注 Feed 流已经有了很多内容，同时也养成了良好的关注 Github Trending 榜单的习惯。更近一步，你可能通过一些很 “Hack” 的技巧成为了一些知名开源项目的 Contributor，当然我承认这需要一些耐心，并且你可能还需要一些机遇，但是当你长期 Focus 在 1 个或几个项目上时，这些机遇无疑会被放大，你已经在技术社区里面有了一点原始的积累了。

接下来你可以尝试去开拓自己的内容，尝试提交自己平时的项目代码在 Github 上，让自己的榜单开始 “绿” 起来。

至少先达到如下的地步：
![图片14](https://image.pylover.net/img/202112292209971.png?imageMogr2/format/webp)

然后开始向这样进军：
![图片15](https://image.pylover.net/img/202112292209994.png?imageMogr2/format/webp)

当然如果短时间内你并没有找到合适的想法去提交自己的 Github，那么你可以去尝试模仿大多数的 “一个文件” 的贡献，即整理一个 README.md，将自己平时看 Github Trending 时觉得好的内容记录下来，系统地分类并整理成一个榜单，随着你的坚持，你可能可以达到如下效果：<https://github.com/vuejs/awesome-vue>。
![图片16](https://image.pylover.net/img/202112292210237.png?imageMogr2/format/webp)

### 让事情再更有趣一点

当你持续输出内容之后，一开始你会经历一个比较艰难的适应期，比如坚持了几周因为事情太忙就搁置了，所以这个时候你需要找点乐子，让自己保持新鲜感。

你会发现 Github 已经可以写好看的自我介绍了：<https://github.com/anuraghazra/github-readme-stats>。

比如这个：
![图片16.5](https://image.pylover.net/img/202112292210771.png?imageMogr2/format/webp)

比如记录的语言使用情况：
![图片17](https://image.pylover.net/img/202112292211175.png?imageMogr2/format/webp)

比如记录你的 Star、Commits、PR、Issue 情况：
![图片18](https://image.pylover.net/img/202112292212926.png?imageMogr2/format/webp)

把介绍写成诗句：<https://github.com/anuraghazra>。
![图片19](https://image.pylover.net/img/202112292212107.png?imageMogr2/format/webp)

### 简化流程，让点击更便捷

如果你希望自己能够时刻被提醒，打开 Github 更便捷一点，同时又能兼顾项目与文章，那么掘金开发者插件会是一个很好的选择：<https://juejin.cn/extension>。

安装之后，每次打开一个新的浏览器窗口，都会展示插件的网页：
![图片20](https://image.pylover.net/img/202112292212841.png?imageMogr2/format/webp)

## 参考文章

{% linkgrid %}
微信文章 | https://mp.weixin.qq.com/s/xfgyl1n_KDY_kBXMf8ASXw | 如何高效地在网上找开源项目? | /uploads/wechat.png
微信文章 | https://mp.weixin.qq.com/s/ZwBQJJj0EwvPg-YktkUOOw | 都快 2022 年了，这些 Github 使用技巧你都会了吗？ | /uploads/wechat.png
{% endlinkgrid %}
