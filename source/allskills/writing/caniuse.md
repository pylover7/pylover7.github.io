---
title: Caniuse
comments: false
---


## 用法
```jinja
{% caniuse feature @ [periods] %}
```
或
```jinja
{% can feature @ [periods] %}
```
 - **功能**：在 [Caniuse](https://caniuse.com/) 上搜索你想要的功能，然后单击搜索结果标题左侧的散列标志，就会得到该特性的唯一名称。
 - **可选参数**：选择要显示的浏览器的版本，支持值：`past_1`, `past_2`, `past_3`, `past_4`, `past_5`, `currentfuture_3`, `future_2`, `future_1` ;如果这些值是空的，那么默认将使用 `current`


## 例子
### 无参数的 Caniuse
```jinja
{% caniuse fetch %}
```

{% caniuse fetch %}

### 有 `current` 参数的 Caniuse
```jinja
{% caniuse sharedarraybuffer @ current %}
```

{% caniuse sharedarraybuffer @ current %}

### 有 `future` 参数的 Caniuse
```jinja
{% caniuse loading-lazy-attr @ future_3,future_2,future_1 %}
```

{% caniuse loading-lazy-attr @ future_3,future_2,future_1 %}

### 有 `past` 参数的 Caniuse
```jinja
{% caniuse link-rel-modulepreload @ past_1,past_2,past_3,past_4,past_5 %}
```

{% caniuse link-rel-modulepreload @ past_1,past_2,past_3,past_4,past_5 %}

