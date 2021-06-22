## 原生的ajax
- 生成XMLHttpRequest对象
- 绑定响应函数onreadystatechange
- 调用open方法，设置对应的请求方式，请求路径，是否异步
- 使用实例的setRequestHeader方法设置一些请求头的信息
- 调用send方法，如果包含请求体，请求体数据传入，真正发出请求
```javascript
const xhr = new XMLHttpRequest()
xhr.setRequestHeader(property, value)
xhr.onreadystatechange = function() {

}
xhr.open(method, url, async)
xhr.send(data) // 发送的数据就是请求的实体内容
```
另外的：
XMLHttpRequest实例上的三个属性：
- responseText 获得字符串形式的响应数据。
- responseXML 获得XML 形式的响应数据
- readyState 用来标识当前XMLHttpRequest实例对象处于什么状态。
readyState总共有5个状态值，分别为0~4，每个值代表了不同的含义：
  - 0：未初始化 -- 尚未调用.open()方法；
  - 1：启动 -- 已经调用.open()方法，但尚未调用.send()方法；
  - 2：发送 -- 已经调用.send()方法，但尚未接收到响应；
  - 3：接收 -- 已经接收到部分响应数据；
  - 4：完成 -- 已经接收到全部响应数据，而且已经可以在客户端使用

## Axios
- Axios 是一个基于 promise 的 HTTP 库，可以用在浏览器和 node.js 中。前端最流行的 ajax 请求库
- 浏览器端/node 端都可以使用，浏览器中创建XMLHttpRequests，在node环境使用http对象发送ajax请求
- 支持请求／响应拦截器、支持请求取消
- 安全性更高，客户端支持防御 XSRF


## fetch 
[MDN fetch导航](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API)
fetch 实现了近乎 axios的所有功能（除了拦截器）

主要有四个核心概念：
- 请求/响应的主体：Body
- 请求：Request
- 响应：Response
- 头部字段：Headers

fetch不仅仅支持在浏览器主线程，同样的在Worker也支持：
WindowOrWorkerGlobalScope.fetch()

使用也非常简单：
fetch(url, initConfig)

相对于axios实现的各层配置的封装、响应拦截器、请求拦截器还是差一点意思，但是可以通过自己封装也是完全能够实现

```javascript
fetch(url, {
    body: JSON.stringify(data), // must match 'Content-Type' header
    cache: 'no-cache', // *default, no-cache, reload, force-cache, only-if-cached
    credentials: 'same-origin', // include, same-origin, *omit
    headers: {
      'user-agent': 'Mozilla/4.0 MDN Example',
      'content-type': 'application/json'
    },
    method: 'POST', // *GET, POST, PUT, DELETE, etc.
    mode: 'cors', // no-cors, cors, *same-origin
    redirect: 'follow', // manual, *follow, error
    referrer: 'no-referrer', // *client, no-referrer
  })
  .then(function(response) {
    if(response.ok) {
      return response;
    }
    throw new Error('Network response was not ok.');
  }).then(function(response) {
    // 操作
  }).catch(function(error) {
    // 请求失败
    console.log('There has been a problem with your fetch operation: ', error.message);
  });
```