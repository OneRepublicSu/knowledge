#### JS执行机制

- JavaScript语言的一大特点就是$\textcolor{Emerald}{ 单线程}$,也就是说同一个事件只能做一件事

- 为了避免某一环节执行的时间过长,造成页面的渲染不连贯,导致页面渲染加载阻塞的感觉,利用多核cpu的计算能力,允许JavaScript脚本创建多个线程,于是js中出现了同步和异步

- 同步任务都在主线程上执行,形成一个执行栈

- js的异步是通过回调函数实现的

- 一般而言,异步任务有以下三种类型

  普通事件:如click,resize等

  资源加载:如load,error等

  定时器,包括setInterval,setTimeout等

  异步任务相关添加到任务队列中(任务队列也称为消息队列)

- js的执行机制是:

  $\textcolor{Emerald}{  先执行执行栈中的同步任务}$

  异步任务放入任务队列中,一旦执行栈中的所有同步任务执行完毕,系统就会按次序读取任务队列中的异步任务,于是被读取的异步任务结束等待状态,进入执行栈,开始执行

  $\textcolor{Emerald}{  这个过程就叫做事件循环eventloop}$

#### location对象

- location的数据类型是对象,它拆分并保存了URL地址的各个组成部分

- href属性获取完整的url地址,对其赋值时用于地址的跳转

  search属性获取地址中携带的参数,是符号?后面的部分

  hash属性获取地址中的哈希值,符号#后面的部分

  reload方法用来刷新当前页面,传入参数true时表示强制刷新

- 语法

  ```javascript
   //跳转到目标页面
  document.querySelector('#btn').addEventListener('click',function(){
              location.href ='https://www.baidu.com/'
          })
  //打印windows的location地址
     console.log(location.href)
  ```

- 常用的属性和方法

  ```JavaScript
     console.log(location.search)
  ```

  search属性获取地址中携带的参数,符号?后面部分

  ```javascript
     console.log(location.hash)
  ```

  hash属性获取符号#之后的部分

  ```javascript
   location.reload(true)
  ```

  reload方法用来刷新当前页面,传入参数时表示强制刷新

#### navigator对象

- navigator的数据类型是对象，该对象下记录了浏览器自身的相关信息

- 语法

  ```javascript
  // 检测 userAgent（浏览器信息）
  !(function () {
  const userAgent = navigator.userAgent
  // 验证是否为Android或iPhone
  const android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)
  const iphone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)
  // 如果是Android或iPhone，则跳转至移动站点
  if (android || iphone) {
  location.href = 'http://m.itcast.cn'
  }
  })()
  ```

##### history对象

- history的数据类型是对象,主要管理历史记录,该对象与浏览器地址栏的操作相对应,如前进,后退,历史记录等

- 常用的属性和方法

  | history对象方法 | 作用                                                      |
  | --------------- | --------------------------------------------------------- |
  | back()          | 可以后退功能                                              |
  | forward( )      | 前进功能                                                  |
  | go(参数)        | 前进后退功能,参数如果是1前进一个页面,如果是-1后退一个页面 |

#### 本地存储介绍

- 本地存储的数据存储在用户浏览器中

- 设置,读取方便,甚至页面刷新不丢失数据

- 容量较大,$\textcolor{Emerald}{  sessionStorage和localStorage }$约5M左右

- 分类-localStorage

  作用:可以将数据永久存储在本地(用户的电脑),除非手动删除,否则关闭页面也会存在

  可以多窗口(页面)共享(同一浏览器可以共享)

  以键值对的形式存储使用

- 语法

  ```javascript
  localStorage.setItem('age',3)
  //存
  localStorage.getItem('obj')
  //读
  localStorage.removeItem(key)
  //删除
  ```

  > 在console控制台的application处查看结果

- 分类-sessionstorage

  声明周期为关闭浏览器窗口

  在同一个窗口(页面)下数据可以共享

  以键值对的形式存储使用

  用法跟localstorage基本相同

#### 存储复杂数据类型

- 本地储存只能存储字符串,无法存储复杂数据类型

- 想要解决这个问题需要将复杂数据类型转换成json格式的字符串,存储到本地

  ```javascript
              {id:1, name:'zkx'},
              {id:2, name:'hy'}]
  
              const arrNew = JSON.stringify(arr)
              console.log(arrNew)
  ```

- 此方法读取出来的数据是字符串无法直接使用,需要将它再次转换为对象

  ```javascript
  JSON.parse(str)
  ```

- map方法遍历数组

  ```javascript
    const newArr = data.map(function (item,index) {
          return `hello`
        })
  ```

  > map可以处理数据并且返回新的数组

- join方法可以将数组拼接成字符串

  ```javascript
     const arr = ['<li>1</li>', '<li>2</li>', '<li>2</li>']
      const res = arr.join('')
      console.log(res)
  ```

  > 数组元素是通过参数里面指定的分隔符进行分隔的







  

