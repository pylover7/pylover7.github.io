---
title: 注意文本框
comments: false
---



## 设置

```_config.next.yml
note:
  # Note tag style values:
  #  - simple    bs-callout old alert style. Default.
  #  - modern    bs-callout new (v2-v3) alert style.
  #  - flat      flat callout style with background, like on Mozilla or StackOverflow.
  #  - disabled  disable all CSS styles import of note tag.
  style: simple
  icons: false
  # Offset lighter of background in % for modern and flat styles (modern: -12 | 12; flat: -18 | 6).
  # Offset also applied to label tag variables. This option can work with disabled note tag.
  light_bg_offset: 0
```

## 用法
```jinja
{% note [class] [no-icon] [summary] %}
Any content (support inline tags too).
{% endnote %}
```

 - `[class]`: 可选参数，支持的值： `default ` | `primary ` | `success ` | `info ` | `warning ` | `danger` 。
 - `[no-icon]`: 可选参数，是否显示图标。
 - `[summary]`: 可选参数，可选的说明摘要

 > 所有参数都是可选的。



## 例子

### 没有定义任何样式

```jinja
{% note %}
#### Header
{% endnote %}
```

{% note %}

#### Header

{% endnote %}

### 默认样式

```jinja
{% note default %}
#### Default Header
Welcome to [Hexo!](https://hexo.io)
{% endnote %}
```

{% note default %}

#### Default Header

Welcome to [Hexo!](https://hexo.io)
{% endnote %}

### 基本样式

```jinja
{% note primary %}
#### Primary Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}
```

{% note primary %}
#### Primary Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

### 信息样式

```jinja
{% note info %}
### Info Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}
```

{% note info %}
### Info Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

### 成功样式
```jinja
{% note success %}
#### Success Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}
```

{% note success %}
#### Success Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

### 警告样式
```jinja
{% note warning %}
#### Warning Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}
```

{% note warning %}
#### Warning Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

### 危险样式
```jinja
{% note danger %}
#### Danger Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}
```

{% note danger %}
#### Danger Header
**Welcome** to [Hexo!](https://hexo.io)
{% endnote %}

### 没有图标的注意样式

```jinja
{% note info no-icon %}
#### No icon note
Note **without** icon: `note info no-icon`
{% endnote %}
```

{% note info no-icon %}
#### No icon note
Note **without** icon: `note info no-icon`
{% endnote %}

### 折叠样式
#### 基本
```jinja
{% note primary This is a summary %}
#### Details and summary
Note with summary: `note primary This is a summary`
{% endnote %}
```

{% note primary This is a summary %}
#### Details and summary
Note with summary: `note primary This is a summary`
{% endnote %}

#### 无图标
```jinja
{% note info no-icon This is a summary %}
#### Details and summary (No icon)
Note with summary: `note info no-icon This is a summary`
{% endnote %}
```

{% note info no-icon This is a summary %}
#### Details and summary (No icon)
Note with summary: `note info no-icon This is a summary`
{% endnote %}

### 嵌套样式（代码块）

~~~jinja
{% note success %}
#### Codeblock in note
```
code block in note tag
code block in note tag
code block in note tag
```
{% endnote %}
~~~

{% note success %}

#### Codeblock in note

```jinja
code block in note tag
code block in note tag
code block in note tag
```
{% endnote %}

### 嵌套样式（列表）

```jinja
{% note default %}
#### Lists in note
* ul
* ul
  * ul
  * ul
* ul

1. ol
2. ol
  1. ol
  2. ol
3. ol
{% endnote %}
```

{% note default %}

#### Lists in note

* ul
* ul
  * ul
  * ul
* ul

1. ol
2. ol
   1. ol
   2. ol
3. ol
   {% endnote %}

### 嵌套样式（表格）

```jinja
#### Table in Note
{% note default %}
| 1 | 2 |
| - | - |
| 3 | 4 |
| 5 | 6 |
| 7 | 8 |
{% endnote %}
```

#### Table in Note

{% note default %}

| 1    | 2    |
| ---- | ---- |
| 3    | 4    |
| 5    | 6    |
| 7    | 8    |

{% endnote %}