# CSS那些属性可以为负值

[chokcoco - 你所不知道的 CSS 负值技巧与细节](https://juejin.cn/post/6844903908440014861#heading-6)


## 常见的几个
- 使用负 marign 实现元素的水平垂直居中，使用负 marign 隐藏列表 li 首尾多余的边框
- 使用负 text-indent 实现文字的隐藏 
- 使用负的 z-index 参与层叠上下文排序
- 使用负值 outline-offset 实现加号
- box-shadow 单侧投影
- scale(-1) 实现翻转
- letter-spacing 倒叙排列文字
- animation-dealy 为负值的动画会立刻执行，开始的位置是其动画阶段中的一个阶段
- 正padding和负值margin实现多列等高布局