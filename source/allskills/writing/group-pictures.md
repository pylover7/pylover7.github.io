---
title: 图集
comments: false
---



## 用法

```jinja
{% grouppicture [group]-[layout] %}
{% endgrouppicture %}
```
或
```
{% gp [group]-[layout] %}
{% endgp %}
```
 - `[group]`  : 要添加到组中的图片总数。
 - `[layout]` : 默认显示组下的图片。
`
## 例子

```jinja
{% grouppicture 6-3 %}
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
{% endgrouppicture %}
```

{% grouppicture 6-3 %}
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
{% endgrouppicture %}

```jinja
{% gp 5-2 %}
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
{% endgp %}
```

{% gp 5-2 %}
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
  ![](./image/image.png)
{% endgp %}