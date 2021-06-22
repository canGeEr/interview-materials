# Cookie 和 Seeion
## Cookie：
- 存储于客户端电脑上的文本文件中，只要客户端cookie开放且有数据，每一次请求都会自动识别当前请求的路径，将电脑存储对于域下的cookie 添加到http报文中，后台可以实时接收观察获取这些Cookie
- 属性有：name=value，domain、path、maxAge、expires、secure、httpOnly
    - 有效范围：domain、path
    - 有效时间：maxAge（相对时间）、expires（过期时间） ，maxAge的优先级更高，如果两者都没有的话，Chrome里过期时间会显示为Session或N/A
    - 安全：httpOnly、SameSite，属性“HttpOnly”会告诉浏览器，此 Cookie 只能通过浏览器 HTTP 协议传输，禁止其他方式访问；“SameSite”可以防范“跨站请求伪造”（XSRF），设置成Strict可以严格限定 Cookie 不能随着跳转链接跨站发送，而“SameSite=Lax”则略宽松一点，允许 GET/HEAD 等安全方法，但禁止 POST 跨站发送；还有一个属性叫“Secure”，表示这个 Cookie 仅能用 HTTPS 协议加密传输，明文的 HTTP 协议会禁止发送。但 Cookie 本身不是加密的，浏览器里还是以明文的形式存在
- HTTP 是无状态的协议
- Cookie 是不可跨域的

## Session：
- 基于 cookie 实现的，session 存储在服务器端，sessionId 会被存储到客户端的cookie 中（当然也不是必须存储在cookie中）
- 客户端第一次访问，服务端记录，并生成唯一的标识sessionId，写回给浏览器；浏览器收到信息后，存储在对应的域下；当浏览器再次发送的时候自动判断是否在该域下携带cookie，并以cookie的sessionId识别身份信息

## 区别：
- Session 是存储在服务器端的，Cookie 是存储在客户端的
  - Session 比 Cookie 安全，不是谁都能获取到服务器的Session
  -  Cookie 只支持存字符串数据，想要设置其他类型的数据，需要将其转换成字符串，Session 可以存任意数据类型

- Cookie 可设置为长时间保持，比如我们经常使用的默认登录功能，Session 一般失效时间较短，客户端关闭（默认情况下）或者 Session 超时都会失效

- 单个 Cookie 保存的数据不能超过 4K，Session 可存储数据远高于 Cookie，但是当访问量过多，会占用过多的服务器资源