# JavaScript的一些关键字和API的实现

## 使用setTimeout模拟setInterval
```javascript
function setInterval(callback, delay) {//避免严格模式
    setTimeout(()=>{
        callback()
        setInterval()
    }, delay)
}
```

## 实现call
```javascript
Function.prototype.call = function (context, ...args) {
    if(typeof this !=== 'function') throw '非函数对象调用错误'
    const tempName = Symbol('callFun')
    context[tempName] = this
    const result = context[tempName](...args);
    delete context[tempName];
    return result;
}
```

## 实现Object.create