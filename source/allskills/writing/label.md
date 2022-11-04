---
title: 文字标记
comments: false
---


## 用法
```jinja
{% label [class]@text %}
```

 - `[class]` 可选的参数，支持的值： `default ` | `primary ` | `success` | `info ` | `warning ` | `danger` ，如果未指定，将使用浏览器的默认样式，在不同的浏览器中可能会有所不同。
 - `text` : `@text` 可以指定带空格或不带空格，例如：`success @text` 和 `success@text` 是一样的。


## 例子

```jinja
Lorem {% label @ipsum %} {% label primary@dolor sit %} amet, consectetur {% label success@adipiscing elit, %} sed {% label info@do eiusmod %} tempor incididunt ut labore et dolore magna aliqua.

Ut enim *{% label warning @ad %}* minim veniam, quis **{% label danger@nostrud %}** exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

Duis aute irure dolor in reprehenderit in voluptate ~~{% label default @velit %}~~ <mark>esse</mark> cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```

Lorem {% label @ipsum %} {% label primary@dolor sit %} amet, consectetur {% label success@adipiscing elit, %} sed {% label info@do eiusmod %} tempor incididunt ut labore et dolore magna aliqua.

Ut enim *{% label warning @ad %}* minim veniam, quis **{% label danger@nostrud %}** exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.

Duis aute irure dolor in reprehenderit in voluptate ~~{% label default @velit %}~~ <mark>esse</mark> cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
