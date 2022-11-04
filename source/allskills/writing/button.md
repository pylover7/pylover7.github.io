---
title: 按钮
comments: false
---



## 用法

```jinja
{% button url, text, icon [class], [title] %}
```

or

```jinja
{% btn url, text, icon [class], [title] %}
```

- `url`     : URL 的绝对或相对路径。
- `text`    : 按钮文本。如果没有指定图标，则为必需。
- `icon`    : 图标名称，如果没有指定文本，则为必须
- `[class]` : *可选参数* 按钮大小: `fa-fw` | `fa-lg` | `fa-2x` | `fa-3x` | `fa-4x` | `fa-5x`
- `[title]` : *可选参数* 鼠标提示。

## 例子

### 简单样式

```jinja
{% button #, Text %}
```

{% button #, Text %}

### 带有文本和标题的按钮

```jinja
{% btn #, Text %}{% btn #, Text & Title,, Title %}
```

{% btn #, Text %}{% btn #, Text & Title,, Title %}

```jinja
{% btn #, Text %} {% btn #, Text & Title,, Title %}
```

{% btn #, Text %} {% btn #, Text & Title,, Title %}

```jinja
{% btn #, Text %}
{% btn #, Text & Title,, Title %}
```

{% btn #, Text %}
{% btn #, Text & Title,, Title %}

### 带有图标的按钮

```html
<div>{% btn #,, home fa-5x %}{% btn #,, home fa-5x %}{% btn #,, home fa-5x %}</div>
<div>{% btn #,, home fa-4x %}{% btn #,, home fa-4x %}{% btn #,, home fa-4x %}</div>
<div>{% btn #,, home fa-3x %}{% btn #,, home fa-3x %}{% btn #,, home fa-3x %}</div>
<div>{% btn #,, home fa-2x %}{% btn #,, home fa-2x %}{% btn #,, home fa-2x %}</div>
<div>{% btn #,, home fa-lg %}{% btn #,, home fa-lg %}{% btn #,, home fa-lg %}</div>
<div>{% btn #,, home %}{% btn #,, home %}{% btn #,, home %}</div>
```

<div>{% btn #,, home fa-5x %}{% btn #,, home fa-5x %}{% btn #,, home fa-5x %}</div>
<div>{% btn #,, home fa-4x %}{% btn #,, home fa-4x %}{% btn #,, home fa-4x %}</div>
<div>{% btn #,, home fa-3x %}{% btn #,, home fa-3x %}{% btn #,, home fa-3x %}</div>
<div>{% btn #,, home fa-2x %}{% btn #,, home fa-2x %}{% btn #,, home fa-2x %}</div>
<div>{% btn #,, home fa-lg %}{% btn #,, home fa-lg %}{% btn #,, home fa-lg %}</div>
<div>{% btn #,, home %}{% btn #,, home %}{% btn #,, home %}</div>

### 带有文本和图标的按钮

```jinja
<p>{% btn #, Text & Icon (buggy), home %}
{% btn #, Text & Icon (fixed width), home fa-fw %}</p>
```

<p>{% btn #, Text & Icon (buggy), home %}
{% btn #, Text & Icon (fixed width), home fa-fw %}</p>


```jinja
<p>{% btn #, Text & Large Icon, home fa-fw fa-lg %}
{% btn #, Text & Large Icon & Title, home fa-fw fa-lg, Title %}</p>
```

<p>{% btn #, Text & Large Icon, home fa-fw fa-lg %}
{% btn #, Text & Large Icon & Title, home fa-fw fa-lg, Title %}</p>


### 文本中的按钮

```jinja
Lorem {% btn #, Lorem, home fa-fw fa-lg %} ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident {% btn #, Ipsum, home fa-fw fa-lg %}, sunt in culpa qui officia deserunt mollit anim id est laborum.
```

Lorem {% btn #, Lorem, home fa-fw fa-lg %} ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident {% btn #, Ipsum, home fa-fw fa-lg %}, sunt in culpa qui officia deserunt mollit anim id est laborum.

### 其他标签内的按钮

```jinja
{% note info %}
{% btn #, Text & Icon, home fa-fw %}

{% btn #,, home, Title %}{% btn #, Text %}

[Link](#)
{% endnote %}
```

{% note info %}
{% btn #, Text & Icon, home fa-fw %}

{% btn #,, home, Title %}{% btn #, Text %}

[Link](#)
{% endnote %}

### 按钮边距

```jinja
<div class="text-center"><div>{% btn #,, heading %}{% btn #,, fab fa-edge %}{% btn #,, times %}{% btn #,, far fa-circle %}</div>
<div>{% btn #,, italic %}{% btn #,, fab fa-scribd %}</div>
<div>{% btn #,, fab fa-google %}{% btn #,, fab fa-chrome %}{% btn #,, fab fa-opera %}{% btn #,, gem fa-rotate-270 %}</div></div>
```

<div class="text-center"><div>{% btn #,, heading %}{% btn #,, fab fa-edge %}{% btn #,, times %}{% btn #,, far fa-circle %}</div>
<div>{% btn #,, italic %}{% btn #,, fab fa-scribd %}{% btn #,, fas fa-globe %}</div>
<div>{% btn #,, fab fa-google %}{% btn #,, fab fa-chrome %}{% btn #,, fab fa-opera %}{% btn #,, gem fa-rotate-270 %}</div></div>


### 带有相对 URL 的按钮

```jinja
<div class="text-center">{% btn #, Previous Chapter, arrow-left fa-fw fa-lg, Previous Chapter (Full Image) %} {% btn #, Next Chapter, arrow-right fa-fw fa-lg, Next Chapter (Label) %}</div>
```

<div class="text-center">{% btn #, Previous Chapter, arrow-left fa-fw fa-lg, Previous Chapter (Full Image) %} {% btn #, Next Chapter, arrow-right fa-fw fa-lg, Next Chapter (Label) %}</div>

### 带有绝对 URL 的按钮

```jinja
<div class="text-center">{% btn https://github.com/next-theme/hexo-theme-next, NexT, fab fa-github fa-fw fa-lg, NexT source code %}</div>
```

<div class="text-center">{% btn https://github.com/next-theme/hexo-theme-next, NexT, fab fa-github fa-fw fa-lg, NexT source code %}</div>
