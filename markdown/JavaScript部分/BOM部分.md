## 5.前端路由
#### 前端路由的本质：
监听 URL 的变化，然后匹配路由规则，显示相应的页面，并且无须刷新页面。目前 前端使用的路由就只有两种实现方式：
- Hash 模式
- History 模式
	
#### Hash 模式：
就是 Hash URL，当 # 后面的哈希值发生变化时，可以通过 hashchange 事件来 监听到 URL 的变化，从而进行DOM卸载更新，并且无论哈希值如何变化，页面都其实没有刷新，浏览器没有历史记录
	
#### History 模式：
History 模式是 HTML5 新推出的功能，主要使用 history.pushState 和 history.replaceState 改变 URL，通过 History 模式改变 URL 同样不会引起页面的刷新，只会更新浏览器的历史记录；当用户做出浏览器动作时，比如点击后退按钮时会触发 popState 事件

#### 两种模式的区别：
- Hash 模式只可以更改 # 后面的内容，History 模式可以通过 API 设置任意的同源 URL
- History 模式可以通过 API 添加任意类型的数据到历史记录中，Hash 模式只能更改哈希值，也就 是字符串
- Hash 模式无需后端配置，并且兼容性好。History 模式在用户手动输入地址或者刷新页面的时候 会发起 URL 请求，后端需要配置 index.html 页面用于匹配不到静态资源的时候
