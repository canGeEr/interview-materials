# JavaScript的一些关键字和API的实现

## 使用setTimeout模拟setInterval
```javascript
//严格模式下
function setInterval(callback, delay) {//避免严格模式
    setTimeout(()=>{
        callback()
        setInterval()
    }, delay)
}

//非严格模式下
setTimeout(function(){
    //注意这里不能使用箭头函数，箭头函数无法访问arguments
    setTimeout(arguments.callee, delay)
}, delay)
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
```javascript
//借助new实现
Object.create = function(prototype, descriptors) {
    function Fun() {}
    Fun.prototype = prototype
    const obj = new Fun()
    Object.defineProperties(obj, descriptors)
    return obj
}
```

## 实现new原理
```javascript
//借助
{
    new: function (constructor, ...args) {
        const obj = Object.create(constructor.prototype)
        const result = constructor.call(result, ...args)
        return result instanceof Object ? result : obj
    }
}
```

## 实现instanceof
```javascript
{
    instanceof: function instanceof(obj, constructor) {
        let proto = obj.__proto__
        let prototype = constructor.prototype
        while(proto) {
            if(proto === prototype) return true
            proto = proto.__proto__
        }
        return false
    }
}
```

## 实现数组的map方法
```javascript
Function.prototype.map = function(callback) {
    let result = []
    for(let [index, value] of this.entries()) {
        result[index] = callback(value, index, this)
    }
    return result
}
```

## 实现数组reduce
```javascript
Function.prototype.reduce = function(callback, initValue) {
    let startIndex = 0
    let taget = initValue
    if(initValue === undefined) {//最好不用!initValue
        taget = this[0]
        startIndex = 1
    }
    for(; startIndex<this.length; startIndex++) {
        taget = callback(taget, this[startIndex], startIndex, this)
    }
    return taget
}
```

## rem使用JS实现
```javascript
function setRem() {
    let doc = document.documentElement;
    let width = doc.getBoundingClientRect().width;
    let rem = width / 75
    doc.style.fontsize = rem + 'px';
}
addEventListener("resize", setRem);//这是实现响应式的关键
```