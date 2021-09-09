# 二战腾讯一、二面

## 腾讯CSIG一面
- 聊了下个人经历，问项目
    - JWT，怎么防止Token被**伪造**
    - 项目的难点（性能上做了优化）
- 继续下去问：网页还有其它需要注意的点嘛
    - 兼容（html、css、js（loadsh（JS插件包、JS能力检测）、其实可以从webpack去答有各种兼容插件包）
    - Web安全（SQL注入）
    - 性能监控、异常监控
    - SEO
- 原型链、继承（组合、组合寄生、class）说的比较详细就没叫我手写（基本是背代码那种）
- 功能函数模块：判断两个对象是否相互引用
```javascript
let objOne = {
    next: null,
    name: 'objOne'
}
let objTwo = {
    next: null,
    name: 'objTwo'
}
objOne.next = objTwo
objTwo.next = objOne
// objOne objTwo 两个对象相互应用 这只是一个例子，不要参考这个对象的属性名

function yingYon(obj1, obj2) {

}
```


## 腾讯CSIG二面
- 上来聊项目、经历
    - 怎么做的项目，项目做了些啥
    - 怎么搭建的前端（主要）
    - 登入怎么做的（我当时答的cookie、session、token（没答如果懂的话尽量答）、加密）

- 计算机网络
    - Http头部字段有那些
    - 我说不太会，然后他问我会什么，我说一些比较基础的Http、UDP和TCP和TLS

- 操作系统 
    - 进程和线程
    - 进程线程怎么通信的
    - 死锁（什么是死锁），怎么解决
    - ...不会了，他就不问了

- 来了一道题：
```javascript
/*
// 树的根节点是0
  实现函数buildTree
  const flatTreeDatas = [
    {
      id: "1",
      parentId: "0"
    },
    {
      id: "1-1",
      parentId: "1"
    },
    {
      id: "1-1-1",
      parentId: "1-1"
    },
    {
      id: "1-2",
      parentId: "1"
    },
    {
      id: "1-3",
      parentId: "1"
    },
    {
      id: "2",
      parentId: "0"
    },
    {
      id: "2-1",
      parentId: "2"
    },
    {
      id: "2-2",
      parentId: "2"
    },
    {
      id: "2-3",
      parentId: "2"
    }
  ];

  
  输出：
  
  [{id:"1",children:[{id:"1-1",children:[{id:"1-1-1"}]},{id:"1-2"}]},....] 
  */
```

反思：
- 计科基础差（操作系统、和计算机网络）
- 不够自信
- 编程题每次审题不清，需要仔细的想
