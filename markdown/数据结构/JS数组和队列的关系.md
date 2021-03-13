# JS数组和队列的关系

## JS数组

### 数组创建
- new Array
- []
- Array.of、Array.from

### 数组访问方法
- map、forEach
- filter
- some、every、find、findIndex
- indexOf、lastIndexOf、includes
- fill 填充
- reduece、concat、reverse、join 功能型
- sort 排序

### 数组增删改查
- add
    - push 向数组尾部添加
    - unshift 向数组首部添加
    - splice(index, 0, value,....) 下标，删除数量，从下标开始插入的值，...同上一个
- delete
    - pop 从数组尾部弹出
    - shift 从数组首部弹出
    - splice(index, count) 下标，删除的数量
- find、update
    - index下标访问

## 队、栈
- 队
    先进先出
    数组只使用shift和push方法

- 栈
    先进后出
    数组只使用pop和push方法

## 链表

### 为什么需要
当数组中插入和删除一个元素，那么其它元素要进行依次的移位，复杂度为O(n)级别，查改直接访问下标index

### 链表的操作
- 插入：
    - 头插、尾指
    - 中部  

        ```javascript
        newNode.next = currentNode.next
        currentNode.next = newNode
        ```
- 删除

    ```javascript
    currentNode.next = currentNode.next.next
    ```

### 链表缺点
链表虽然删除、更新高效，但是查询和修改都是O(n)级别