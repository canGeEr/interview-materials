# Sleep

## 实现sleep函数
```javascript
function sleep(delay) {
    return new Promise((fulfilled, rejected)=>setTimeout(fulfilled, delay*1000))
}
```

## 每隔n秒打印n
```javascript
async function loop(n) {
    for(let i=1; i<=n; i++) {
        await sleep(i)
        console.log(i)
    }
}

//setTimeout 方法
function loop(n) {
    let sum = 0
    for(let i=1; i<=n; i++) {
        sum += n
        setTimeout(()=>{
            console.log(i)
        }, sum)
    }
}
```