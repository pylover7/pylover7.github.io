---
title: 段落
comments: false
---

## Markdown 段落
### 用法
要创建段落，请使用空白行将一行或多行文本进行分隔。

{% tabs markdown paragraphs %}
<!-- tab 语法 -->
{% code %}
I really like using Markdown.

I think I'll use it to format all of my documents from now on.
{% endcode %}
<!-- endtab -->

<!-- tab HTML -->
{% code %}
<p>I really like using Markdown.</p>

<p>I think I'll use it to format all of my documents from now on.</p>
{% endcode %}
<!-- endtab -->

<!-- tab 预览 -->
I really like using Markdown.

I think I'll use it to format all of my documents from now on.
<!-- endtab -->
{% endtabs %}

### 段落（Paragraph）用法的最佳实
不要用空格（spaces）或制表符（ tabs）缩进段落。

{% note success %}
#### 正确做法
{% code %}
Don't put tabs or spaces in front of your paragraphs.

Keep lines left-aligned like this.
{% endcode %}
{% endnote %}

{% note danger %}
#### 错误做法
{% code %}
    This can result in unexpected formatting problems.

  Don't add tabs or spaces in front of paragraphs.
{% endcode %}
{% endnote %}
