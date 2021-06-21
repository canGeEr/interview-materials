## jsonp的实现
```javascript
function jsonp(url, callbackName, successFun) {
    const jsonpScript = document.createElement('script')
    jsonpScript.async = true
    jsonpScript.src = url
    jsonpScript.type = 'text/javascript'
    window[callbackName] = function(data) {
        successFun && successFun(data)
    }
    document.body.appendChild(successFun)
}
```