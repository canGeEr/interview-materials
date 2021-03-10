## 数据劫持实现
```javascript
//monitor 数据劫持
function monitor(target, resource) {
    let newObj = null
    if(!isObject(resource)) {
        return resource
    }
    Reflect.ownKeys(resource).forEach((key)=>{
        if(isObject(resource[key])){
            newObj = {}
            monitor(newObj, resource[key])
        }else if(isArray(resource[key])) {
            newObj = []
            monitor(newObj, resource[key])
        }
        proxy(target, resource, key, newObj)
        newObj = null
    })
}
```

## 数据代理实现
```javascript
//数据代理
function proxy(target, resource, propertyName, deepObj) {
    Object.defineProperty(target, propertyName, {
        get() {
            return deepObj || resource[propertyName]
        },
        set(newValue) {
            resource[propertyName] = newValue
        },
        enumerable: true,
        configurable: true
    })
}
```

## 实现ES6 的Proxy
```javascript
class Proxy {
    constructor(target, handler) {
        this.handler = handler
        this.monitor(this, target)
    }
    //数据代理
    proxy(target, resource, propertyName, deepObj) {
        Object.defineProperty(target, propertyName, {
            get() {
                return deepObj || resource[propertyName]
            },
            set(newValue) {
                resource[propertyName] = newValue
            },
            enumerable: true,
            configurable: true
        })
    }

    //monitor 数据劫持
    monitor(target, resource) {
        let newObj = null
        if(!isObject(resource)) {
            return resource
        }
        Reflect.ownKeys(resource).forEach((key)=>{
            if(isObject(resource[key])){
                newObj = {}
                this.monitor(newObj, resource[key])
            }else if(isArray(resource[key])) {
                newObj = []
                this.monitor(newObj, resource[key])
            }
            this.proxy(target, resource, key, newObj)
            newObj = null
        })
    }
}
```