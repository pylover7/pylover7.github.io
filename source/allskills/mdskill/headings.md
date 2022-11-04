---
title: 标题语法
comments: false
---

## Markdown标题语法
### 用法

要创建标题，请在单词或短语前面添加井号 (`#`) 。`#` 的数量代表了标题的级别。例如，添加三个 `#` 表示创建一个三级标题 (`<h3>`) (例如：`### My Header`)。

{% tabs markdown headings %}
<!-- tab 语法 -->
{% code %}
# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6
{% endcode %}
<!-- endtab -->

<!-- tab HTML -->
{% code %}
<h1>Heading level 1</h1>
<h2>Heading level 2</h2>
<h3>Heading level 3</h3>
<h4>Heading level 4</h4>
<h5>Heading level 5</h5>
<h6>Heading level 6</h6>
{% endcode %}
<!-- endtab -->

<!-- tab 预览 -->
<h1>Heading level 1</h1>
<h2>Heading level 2</h2>
<h3>Heading level 3</h3>
<h4>Heading level 4</h4>
<h5>Heading level 5</h5>
<h6>Heading level 6</h6>
<!-- endtab -->
{% endtabs %}

### 可选语法

还可以在文本下方添加任意数量的 == 号来标识一级标题，或者 -- 号来标识二级标题。

{% tabs markdown headings ext %}
<!-- tab 语法 -->
{% code %}
Heading level 1
===============

Heading level 2
---------------
{% endcode %}
<!-- endtab -->

<!-- tab HTML -->
{% code %}
<h1>Heading level 1</h1>

<h2>Heading level 2</h2>
{% endcode %}
<!-- endtab -->

<!-- tab 预览 -->
<h1>Heading level 1</h1>

<h2>Heading level 2</h2>
<!-- endtab -->
{% endtabs %}

{% note warning 注意事项 %}
#### 注意事项
不同的 Markdown 应用程序处理 `#` 和标题之间的空格方式并不一致。为了兼容考虑，请用一个空格在 `#` 和标题之间进行分隔。

{% note success %}
#### 正确做法
{% code %}
# Here's a Heading
{% endcode %}
{% endnote %}

{% note danger %}
#### 错误做法
{% code %}
#Here's a Heading
{% endcode %}
{% endnote %}

{% endnote %}
