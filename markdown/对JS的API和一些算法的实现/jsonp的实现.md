## jsonp的实现
```javascript
function jsonp({url, callbackName, successFun, params}) {
    const jsonpScript = document.createElement('script')
    //防止首屏阻塞DOM
    jsonpScript.async = true
    //告知后端需要回调什么函数名
    params.callback = callbackName
    jsonpScript.src = serialize({url, params})
    jsonpScript.type = 'text/javascript'
    window[callbackName] = function(data) {
        successFun && successFun(data)
    }
    //真正到页面上才会发出请求
    document.body.appendChild(successFun)
}

//反序列化
function deSerialize(url) {
    let temp = url.split('?')
    let prefixUrl = temp[0]
    let paramsArr = temp[1].split('&')
    let params = {}
    for(let item of paramsArr) {
        temp = item.split('=')
        params[temp[0]] = temp[1]
    }
    return {
        params,
        url: prefixUrl
    }
}

//序列化
function serialize({url, params}) {
    let str = url + '?'
    for(let pro in params) {
        str += pro + '=' + params[pro] + '&'
    }
    return str.slice(0, -1)
}
```