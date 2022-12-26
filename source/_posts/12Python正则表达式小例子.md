---
title: Python正则表达式小例子
tags:
  - python
  - re
categories:
  - 学习笔记
  - python
date: 2021-10-24 16:29:01
---

## 前言

收集了 20 个 `re` 模块的小栗子，供大家参考学习~

<!-- more -->

## 例子

### 查找第一个匹配串

```python
import re

s = 'i love python very much'
pat = 'python' 
r = re.search(pat,s)
print(r.span()) #(7,13)
```

### 查找所有1

```python
import re

s = '山东省潍坊市青州第1中学高三1班'
pat = '1'
r = re.finditer(pat,s)
for i in r:
    print(i)

# <re.Match object; span=(9, 10), match='1'>
# <re.Match object; span=(14, 15), match='1'>
```

### `\d` 匹配数字 `[0-9]`

```python
import re

s = '一共20行代码运行时间13.59s'
pat = r'\d+' # +表示匹配数字(\d表示数字的通用字符)1次或多次
r = re.findall(pat,s)
print(r)
# ['20', '13', '59']
```

### `?` 表示前一个字符匹配0或1次

```python
import re

s = '一共20行代码运行时间13.59s'
pat = r'\d+\.?\d+' # ?表示匹配小数点(\.)0次或1次
r = re.findall(pat,s)
print(r)
# ['20', '13.59']
```

### `^` 匹配字符串的开头

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'^[emrt]' # 查找以
r = re.findall(pat,s)
print(r)
# [],因为字符串的开头是字符`T`，不在emrt匹配范围内，所以返回为空
```

### `re.I` 忽略大小写

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'^[emrt]' # 查找以
r = re.compile(pat,re.I).search(s)
print(r)
# <re.Match object; span=(0, 1), match='T'> 表明字符串的开头在匹配列表中
```

### 提取单词

{% note info %}
这是不准确版本，请参看第 [9](#补充上第一个单词) 个
{% endnote %}

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'\s[a-zA-Z]+'  
r = re.findall(pat,s)
print(r) #[' module', ' provides', ' regular', ' expression', ' matching', ' operations', ' similar', ' to', ' those', ' found', ' in', ' Perl']
```

### 捕获单词去掉空格

{% note info %}
使用 `()` 捕获，这是不准确版本，请参看第 [9](#补充上第一个单词) 个
{% endnote %}

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'\s([a-zA-Z]+)'  
r = re.findall(pat,s)
print(r) #['module', 'provides', 'regular', 'expression', 'matching', 'operations', 'similar', 'to', 'those', 'found', 'in', 'Perl']
```

### 补充上第一个单词

{% note info %}
上面第 [8](#捕获单词去掉空格)，看到提取单词中未包括第一个单词，使用 `?` 表示前面字符出现 0 次或 1 次，但是此字符还有表示贪心或非贪心匹配含义，使用时要谨慎
{% endnote %}

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'\s?([a-zA-Z]+)'  
r = re.findall(pat,s)
print(r) #['This', 'module', 'provides', 'regular', 'expression', 'matching', 'operations', 'similar', 'to', 'those', 'found', 'in', 'Perl']
```

### 使用 `split()` 直接分割单词

使用以上方法分割单词，不是简洁的，仅仅为了演示。分割单词最简单还是使用 `split()` 。

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'\s+'  
r = re.split(pat,s)
print(r) # ['This', 'module', 'provides', 'regular', 'expression', 'matching', 'operations', 'similar', 'to', 'those', 'found', 'in', 'Perl']
```

### 提取以m或t开头的单词，忽略大小写

{% note warning %}
下面出现的结果不是我们想要的，原因出在 `?` 上！
{% endnote %}

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'\s?([mt][a-zA-Z]*)' # 查找以
r = re.findall(pat,s)
print(r) # ['module', 'matching', 'tions', 'milar', 'to', 'those']
```

### 使用 `^` 查找字符串开头的单词

综合 [11](#提取以m或t开头的单词忽略大小写) 和 12 得到所有以 `m` 或 `t` 开头的单词

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'^([mt][a-zA-Z]*)\s' # 查找以
r = re.compile(pat,re.I).findall(s)
print(r) # ['This']
```

### 先分割，再查找满足要求的单词

使用 `match` 表示是否匹配

```python
import re

s = 'This module provides regular expression matching operations similar to those found in Perl'
pat = r'\s+'  
r = re.split(pat,s)
res = [i for i in r if re.match(r'[mMtT]',i)] 
print(res) # ['This', 'module', 'matching', 'to', 'those']
```

### 贪心匹配

尽可能多的匹配字符

```python
import re

content='<h>ddedadsad</h><div>graph</div>bb<div>math</div>cc'
pat=re.compile(r"<div>(.*)</div>")  #贪婪模式
m=pat.findall(content)
print(m) # ['graph</div>bb<div>math']
```

### 非贪心匹配

与 [14](#贪心匹配) 相比，仅仅多了一个问号 `(?)` ，得到结果完全不同

```python
import re

content='<h>ddedadsad</h><div>graph</div>bb<div>math</div>cc'
pat=re.compile(r"<div>(.*?)</div>")  #贪婪模式
m=pat.findall(content)
print(m) # ['graph', 'math']
```

与14比较可知，贪心匹配和非贪心匹配的区别，后者是字符串匹配后立即返回，见好就收。

### 含有多种分割符

使用 `split` 函数

```python
import re

content = 'graph math,,english;chemistry' # 这种
pat=re.compile(r"[\s\,\;]+")  #贪婪模式
m=pat.split(content)
print(m) # ['graph', 'math', 'english', 'chemistry']
```

### 替换匹配的子串

`sub` 函数实现对匹配子串的替换

```python
import re

content="hello 12345, hello 456321"    
pat=re.compile(r'\d+') #要替换的部分
m=pat.sub("666",content)
print(m) # hello 666, hello 666
```

### 爬取百度首页标题

```python
import re
from urllib import request

#爬虫爬取百度首页内容
data=request.urlopen("http://www.baidu.com/").read().decode()

#分析网页,确定正则表达式
pat=r'<title>(.*?)</title>'

result=re.search(pat,data)
print(result) <re.Match object; span=(1358, 1382), match='<title>百度一下，你就知道</title>'>

result.group() # 百度一下，你就知道
```

### 常用元字符总结

```bash
. 匹配任意字符  
^ 匹配字符串始位置 
$ 匹配字符串中结束的位置 
* 前面的原子重复0次1次多次 
? 前面的原子重复一次或者0次 
+ 前面的原子重复一次或多次
{n} 前面的原子出现了 n 次
{n,} 前面的原子至少出现 n 次
{n,m} 前面的原子出现次数介于 n-m 之间
( ) 分组,需要输出的部分
```

### 常用通用字符总结

```bash
\s  匹配空白字符 
\w  匹配任意字母/数字/下划线 
\W  和小写 w 相反，匹配任意字母/数字/下划线以外的字符
\d  匹配十进制数字
\D  匹配除了十进制数以外的值 
[0-9]  匹配一个0-9之间的数字
[a-z]  匹配小写英文字母
[A-Z]  匹配大写英文字母
```

## 后话

以上就是Python中正则模块的基本使用总结，里面有循序渐进的优化分析过程，这些虽然是中间过程，但是对于正则小白而言，了解这些很有必要。

## 原文链接

{% linkgrid %}
微信文章 | https://mp.weixin.qq.com/s/J8KvyEoZGWfnlKajPnAPYg | 学会Python正则表达式，就看这20个例子~ | /uploads/wechat.png
{% endlinkgrid %}
