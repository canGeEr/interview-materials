## 1.DOM创建、删除元素
#### 创建：
- createElement、createTextNode
- innerHTML
#### 复制：
- cloneNode

#### 插入：
- append，可以一次插入多个节点，插入的可以是DOMString（字符串，作为文本节点）
- 被插入元素.appendChild(插入元素)
- 被插入元素.insertBefore(插入元素，被插队的子元素)

#### 删除；
- 被删除元素.removeChild(删除元素)


## 2.DOM元素器和区别
#### 两个系列：
- Get开头：ById、ByTagName、ByClassName、ByName
- Query开头：querySelector、querySelectorAll （CSS元素选择一致）
	
#### 区别：
- Query选择出来的元素是静态的，Get系列是动态的
- Query返回的类数组可以使用forEach迭代

## 3.DOM关系选择器
#### 关系节点：
- parentNode、childNodes
- firstChild、lastChild
- nextSibling、previousSibling

#### 关系元素：
- parentElement、children
- firstElementChild、lastElementChild
- nextElementSibling、previousElementSibling

#### 验证关系函数：
Contains 函数，确认是否包含子元素

## 4.事件冒泡、捕获和它们的使用场景
当一个事件发生在具有父元素的元素上，现代浏览器运行两个不同的阶段 - 捕获阶段和冒泡阶段
#### 捕获阶段：
- 浏览器检查元素的最外层祖先html，是否在捕获阶段中注册了一个onclick事件处理程序，如果是，则运行它
- 然后，它移动到html中单击元素的下一个祖先元素，并执行相同的操作，然后是单击元素再下一个祖先元素，依此类推，直到到达实际点击的元素

#### 冒泡阶段：
- 浏览器检查实际点击的元素是否在冒泡阶段中注册了一个onclick事件处理程序，如果是，则运行它
- 然后它移动到下一个直接的祖先元素，并做同样的事情，然后是下一个，等等，直到它到达html元素


## 5.给元素绑定事件的几种方式
三种：
- 在HTML元素中绑定事件 onclick=show()
- onclick
- addEventListener(click,show,1/0)

#### addEventListener 和 其它两种的区别：
- 支持冒泡和捕获
- 支持多个处理函数绑定，并一起触发，并且可以随时移除


## 6.阻止事件冒泡、取消默认事件和阻止事件的默认行为
#### 阻止冒泡：
- 3C标准：E.stopPropagation()
- 在ie里：E.cancelBubble = true

#### 阻止浏览器默认行为：
- W3C标准：E.preventDefault()
- 在ie里：E.returnValue = false

#### 阻止浏览器默认行为：
- return false（注意JQ里面的处理函数return false，还包括阻止冒泡的功能）
> 有意思的是，return false只有在内联绑定事件onclick="return false"才有效，对于addEventListener绑定的事件return false无效