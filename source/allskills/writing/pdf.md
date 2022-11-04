---
title: PDF
comments: false
---



## 设置

`next/_config.yml`

```_config.next.yml
pdf:
  enable: true
  # Default height
  height: 500px
```

## 例子

```jinja
{% pdf https://example.com/sample.pdf %}
```

```jinja
{% pdf /path/to/your/file.pdf 600px %}
```

后面的`600px`为设置`pdf`的高度，单位为像素。