# 实现promise相关

## 手写实现Promise
```javascript
function promiseAll() {
    const promiseArr = Array.from(arguments)
    const promiseArrLen = promiseArr.length
    const resultArr = new Array(promiseArrLen)
    let count = 0
    return new Promise((fulfilled, rejected)=>{
        for(let promise of promiseArr) {
            Promise.resolve(promise).then(
                (res) => {
                    resultArr[count++] = res
                    if(count >= promiseArrLen)  fulfilled(resultArr)
                }, 
                (error) => {
                    rejected(error)
                }
            )
        }
    })
}
```