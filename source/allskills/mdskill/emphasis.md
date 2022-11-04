---
title: 强调语法
comments: false
---

## Markdown 强调语法
通过将文本设置为粗体或斜体来强调其重要性。
### 粗体（Bold）
要加粗文本，请在单词或短语的前后各添加两个星号（asterisks）或下划线（underscores）。如需加粗一个单词或短语的中间部分用以表示强调的话，请在要加粗部分的两侧各添加两个星号（asterisks）。

{% tabs markdown emphasis %}
<!-- tab 语法 -->
```
I just love **bold text**.
I just love __bold text__.
Love**is**bold
```
<!-- endtab -->

<!-- tab HTML -->
```
I just love <strong>bold text</strong>.
I just love <strong>bold text</strong>.
Love<strong>is</strong>bold
```
<!-- endtab -->

<!-- tab 预览 -->
I just love **bold text**.
I just love __bold text__.
Love**is**bold
<!-- endtab -->
{% endtabs %}

### 粗体（Bold）用法最佳实践
Markdown 应用程序在如何处理单词或短语中间的下划线上并不一致。为兼容考虑，在单词或短语中间部分加粗的话，请使用星号（asterisks）。

{% note success %}
#### 正确做法
```
Love**is**bold
```
{% endnote %}

{% note danger %}
#### 错误做法
```
Love__is__bold
```
{% endnote %}
