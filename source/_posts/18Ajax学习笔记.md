---
title: Ajax学习笔记
tags:
  - javascript
  - ajax
categories:
  - 学习笔记
  - ajax
date: 2021-11-07 13:14:14
---

## 前言

`Ajax` 前后端通信技术，简单学习并记录。

<!-- more -->
## `HTTP` 协议与请求内容

`HTTP` 协议，【超文本传输协议】，规定了浏览器和万维网之间相互通信的规则，

### 请求报文

重点是格式与参数

```markdown
行   POST  /s?ie=utf-8  HTTP/1.1
头   Host: baidu.com
     Cookies: name=guigu
     Content-type: text/html
     User-Agent: chrome 3
空行  (必须有，但为空)
体    username=admin&password=adimn
```

### 响应报文

```markdown
行      HTTP1.1(http版本)  200(相应状态码)  OK(状态字符串)
头      Content-type: text/html
  Content-length: 2048
  Content-encoding: gzip
空行     (必须有，但为空)
体    http 内容
```

## AJAX 请求的基本操作

```javascript
// 获取元素
const btn = document.getElementsByTagName("button")[0];
const result = document.getElementsById("result");
// 绑定事件
tn.onclick = function(){
// 1. 创建对象
const xhr = new XMLHttpRequest()
// 2. 初始化，设置请求方法和 url
xhr.open("GET", "http://127.0.0.1/server")
// 3. 发送
xhr.send()
// 4. 事件绑定 处理服务端返回的结果
// on when 当...时候
// readystate 是 xhr 对象中的属性，表示状态 0 1 2 3 4  通常是状态为 4 的时候做处理
// change 改变
xhr.onreadystatechange = function(){
// 判断（服务端返回的所有结果）
if(xhr.readyState === 4){
  // 判断响应的状态码 200
  2xx 都表示成功
  if(xhr.status >= 200 && xhr.status <= 300){
    // 处理结果
    // 1. 响应行
    console.log(xhr.status); // 状态码
    console.log(xhr.statusText); // 状态字符串
    console.log(xhr.getAllResponseHeaders()); // 所有响应头
    console.log(xhr.response) // 响应体
    
    // 设置 result 文本
    result.innerHTML = xhr.response
   }
  }
 }
}

```

**设置 url 参数**
在 `url` 后面加 `?a=100...`

## AJAX 发送 POST 请求

### 不带参数

```javascript
// 创建对象
const result.getElementById("result")
// 绑定事件
result.addEventListener("mouseover", function(){
 // 1. 创建对象
 // 2. 初始化，设置请求方法和 url
 // 3. 发送
 // 4. 事件绑定
  // 状态判断
  // 处理服务端响应的结果
  
})
```

### 带参数请求

```javascript
...
// 3. 发送
xhr.send("a=100&b=200&c=300");
xhr.send("a:100&b:200&c:300");
...
```

## AJAX 设置请求头信息

```javascript
// 2. 初始化，设置请求方法和 url
// 设置请求头，参数一：请求头名字；参数二：请求头的值
xhr.setRequestHeader("Content-Typt", "text/html");
```

## 服务端返回 JSON

```javascript
// 4. 事件绑定
 // 处理服务端响应的结果
 // 手动转换
 let data = JSON.parse(xhr.response);
 result.innerHTML = data.name;
 
 // 自动转换
 // 设置响应体数据的类型
 xhr.responseType = "json"
 ...
```

## 请求超时与网络异常

```javascript
// 设置超时后取消请求
// 超时设置 2s
xhr.timeout(2000)
// 超时回调
xhr.ontimeout = function(){
 ...
}

// 网络异常回调
xhr.onerror = function(){
 ...
}

// 手动取消
// 事件绑定中调用
xhr.abort()
```

## 防止重复发送请求

```javascript

```

## jQuery 发送 Ajax 请求

### GET 方法

```javascript
$("button").click(function(){
 // 参数1 url
 // 参数2 发送参数
 // 参数3 回调函数，接收的参数为响应体
 $.get("http://127.0.0.1:8000", {a: 100, b:200}, function(data){
  console.log(data);
 })
})
```

### POST 方法

```javascript
$("button").click(function(){
 // 参数1 url
 // 参数2 发送参数
 // 参数3 回调函数，接收的参数为响应体
 // 参数4 响应体类型
 $.post("http://127.0.0.1:8000", {a: 100, b:200}, function(data){
  console.log(data);
 }, "json")
})
```

### 通用型 AJAX 方法

```javascript
$.("button").click(function(){
 $.ajax({
  // url
  url: 127.0.0.7:8000,
  // 发送参数
  data: {a:100, b:200},
  // 请求类型
  type: "GET",
  // 响应体结果
  dataType: "json",
  // 成功后的回调
  success: funtion(data){
   console.log(data);
  }
  // 超时时间
  timeout: 2000
  // 失败后的回调
  error: funtion(){
   console_log("xxx")
  }
 })
});
```

## Axios 发送 AJAX 请求

{% note info %}
中文文档 【 [Axios 中文文档](https://www.axios-http.cn/) 】
{% endnote %}

{% note success %}
`<script src="https://cdn.bootcdn.net/ajax/libs/axios/0.21.1/axios.js"></script>`
{% endnote %}

### get 请求

```javascript
// 配置 baseURL
axios.defults.baseURL = "http://137.0.0.1:8080"

axios.get("http://127.0.0.7:8000", {
 // url 参数
 param: {
  id: 100,
  vip: 7,
 },
 // 请求头信息
 headers: {
  name: "xiaoming",
  age: 18
 },

})
```

### 数据返回和处理

```javascript
// 配置 baseURL
axios.defults.baseURL = "http://137.0.0.1:8080"

axios.get("http://127.0.0.7:8000", {
 // url 参数
 param: {
  id: 100,
  vip: 7,
 },
 // 请求头信息
 headers: {
  name: "xiaoming",
  age: 18
 },
}).then(value => {
 console.log(value);
})
```

### post 请求

```javascript
// 配置 baseURL
axios.defults.baseURL = "http://137.0.0.1:8080"

axios.get("http://127.0.0.7:8000", 
 // 请求体
 {
  username: "admin",
  password: "admin",
 }，
 // 其他配置
 {
  // url 参数
  param: {
   id: 100,
   vip: 7,
  },
  // 请求头信息
  headers: {
   name: "xiaoming",
   age: 18
  },
  data: 100
})
```

### ajax 请求

```javascript
axios.ajax({
 // 请求方法
 method: "GET",
 // url
 url: "127.0.0.7:8000",
 // url 参数
 params: {
  vip: 10,
  level: 60,
 },
 // 头信息
 headers： {
  a: 100,
  b: 200,
 },
 // 请求体参数
 data: {
  username: "admin",
  password: "admin",
 }
}).then(response => {
 console.log(response);
})
```

## fetch 函数发送 ajax 请求

### 使用方法

{% note warning %}
该方法使用较少
{% endnote %}

`fetch(input[, init])`

- `input`: 是一个 url
- `inti`: 可选的配置项，具体请看【 [`fethch` 的使用](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API/Using_Fetch) 】

```javascript
fetch("http://127.0.0.1:8000", {
 // 请求方法
 method: "POST",
 //请求头
 headers: {
  name: "xiaoming",
  age: 18,
 },
 // 请求体
 body: "username=admin&password=admin"}
}).then(response => {
 return response.json()
}).then(response => {
 console.log(response)
})
```

## 参考文章

{% linkgrid %}
参考文章 | # | 参考文章的描述 | /uploads/wechat.png
{% endlinkgrid %}
