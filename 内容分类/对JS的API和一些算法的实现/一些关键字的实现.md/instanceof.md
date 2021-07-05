# 实现instanceof

```javascript
const Index = {
  instanceof(resurce, classConstructor) {
    while(resurce) {
      resurce = Object.getPrototypeOf(resurce)
      if(resurce === classConstructor.prototype) return true
    }
    return false
  }
}
```