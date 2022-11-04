---
title: Hexo编辑技巧
date: 2020-07-17 11:01:20
comments: false
---

{% note info %}

这些编辑技巧仅仅只用于`NexT`主题，版本为：`8.11.0`，其他主题以及其他版本是否适用小编就不得而知了。

{% endnote %}

## 单句引用

该标记将在引号前后加上两行，引号的文本将居中。 使用居中引号时，如果我们有多行文本，并且每行的长度不同，则引号不会对称，因此建议仅使用单行文本时使用。 例如文章前的所有文章后做一个总结。

### 用法

```jinja
{% centerquote %}Something{% endcenterquote %}
```
或
```jinja
{% cq %}Something{% endcq %}
```

### 例子

```jinja
{% cq %}Elegant in code, simple in core{% endcq %}
```

{% cq %}Elegant in code, simple in core{% endcq %}