---
title: Python异常处理
date: 2021-10-21 23:54:50
tags: 
    - python
    - retrying
categories: 
    - 学习笔记
    - python
---

## 前言

在写程序时，我们会经常碰到程序出现异常，这时候我们就不得不处理这些异常，以保证程序的健壮性。

处理异常的版本有以下几种，你通常的做法是哪种？

<!-- more -->

## 异常处理的各个版本

### 不负责的版本

这种情况下，不作任何处理，任由程序报错，从而导致程序中断。

针对简单的程序，这样做没什么问题，大不了我遇到问题之后把问题解决，然后重新运行。但是如果是复杂的系统就会很麻烦了，可能你一个异常阻塞了系统的运行，带来灾难性的后果。

### 简单处理版本

简单处理版本，就是加上异常捕获，在发生异常时记录日志，时候可以通过日志来定位异常。

```python
def do_something():
    pass
def log_error(xxx):
    pass

try:
   do_something()
except:
    log_error(xxxx)
```

### 改进处理版本

对于简单处理版本做了改进，增加重试次数。这个在爬虫程序中比较常见，第一次请求超时，可能过一会再请求就成功了，所以重试几次可能会消除异常。

```python
attempts = 0
success = False
while attempts < 3 and not success:
    try:
        do_something()
        success = True
    except:
        attempts += 1
        if attempts == 3:
            break
```

{% note warning %}
**但是这样做仍然不够的，你可能要在很多地方去写这种重试的硬编码，程序看起来乱糟糟的。**
{% endnote %}

### 优雅的版本

使用 `retrying` 模块，让你的异常处理变得优雅起来！

#### 安装

```bash
pip install retrying
```

#### 使用

##### 无限重试

报错就重试

`retrying` 提供一个装饰器函数 `retry`，被装饰的函数会在运行失败的情况下重新执行，默认一直报错就一直重试。

```python

import random
from retrying import retry

@retry
def do_something_unreliable():
    if random.randint(0, 10) > 1:
        print("just have a test")
        raise IOError("raise exception!")
    else:
        return "good job!"

print(do_something_unreliable())
```

运行这个程序，大家可以看到每次打印“just have a test”这句话的次数都不一样。这是由于我们程序中只要随机整数大于1就会打印并且抛出异常。但是由于我们有装饰器函数 retry，所以在发生异常就会重新再次执行方法，直到随机整数大于1，就会打印“good job！”。

##### 有限重试

上面这种无休止地重试，简直是浪费生命，浪费资源。我们要建设绿色家园，所以不妨加点限制：

```python
# 最大重试次数
@retry(stop_max_attempt_number=5)
def do_something_limited():
    print("do something several times")
    raise Exception("raise exception")

do_something_limited()
```

##### 时间限制

一寸光阴一寸金，寸金难买寸光阴。我们要珍惜有限的时间，所以不妨给我们的重试加个时间限制：

```python
# 限制最长重试时间（从执行方法开始计算）
@retry(stop_max_delay=5000)
def do_something_in_time():
    print("do something in time")
    raise Exception("raise exception")

do_something_in_time()
```

```python
# 设置固定重试时间
@retry(wait_fixed=2000)
def wait_fixed_time():
    print("wait")
    raise Exception("raise exception")

wait_fixed_time()
```

```python
# 设置重试时间的随机范围
@retry(wait_random_min=1000,wait_random_max=2000)
def wait_random_time():
    print("wait")
    raise Exception("raise exception")

wait_random_time()
```

##### 根据异常重试

我们自己定义一个函数，判断异常类型，然后将函数作为参数传给装饰函数 retry ，如果异常类型符合，就会进行重试。

```python
# 根据异常重试
def retry_if_io_error(exception):
    return isinstance(exception, IOError)

# 设置特定异常类型重试
@retry(retry_on_exception=retry_if_io_error)
def retry_special_error():
    print("retry io error")
    raise IOError("raise exception")

retry_special_error()
```

##### 重定向重试

这里我们定义了一个判断返回值的函数，然后将这个函数作为参数传给 `retry` 装饰函数。当结果返回是“111”时，就会一直重试执行 `might_return_none` 函数。

```python
# 通过返回值判断是否重试
def retry_if_result_none(result):
    """Return True if we should retry (in this case when result is None), False otherwise"""
    # return result is None
    if result =="111":
        return True


@retry(retry_on_result=retry_if_result_none)
def might_return_none():
    print("Retry forever ignoring Exceptions with no wait if return value is None")
    return "111"

might_return_none()
```

{% note success %}

#### 参数组合使用

以上介绍的这些参数都是可以自定义组合使用的
{% endnote %}

## 参考文章

{% linkgrid %}
微信文章 | https://mp.weixin.qq.com/s/AE21Qaz6M-pkwEZpSAJJ6g | Python异常还能写得如此优雅！ | /uploads/wechat.png
{% endlinkgrid %}
