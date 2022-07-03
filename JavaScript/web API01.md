#### web API的基本认知

------

- const声明的值不能更改,而且const声明变量的时候需要进行起始化,但是对于引用数据类型,比如数组,const声明的变量里面存储的并不是值,而是指向值的内存地址

  ![堆栈.png](https://s2.loli.net/2022/06/29/WprnYJs3b7z4cmA.png)

  为了vue和react的学习,我们建议尽量多的使用const,当然需要重新赋值的值,我们依然需要保留let关键字

- dom的全程叫做document object model 文档对象模型,它是用来呈现以及与任意html实现交互的API,简单来说就是提供了操作网页内容的功能

- 将html文档以树状结构直观的表现出来的形式,我们称之为文档树或者dom树

  文档树能够非常清晰明了的体现标签与标签之间的关系

- $\textcolor{Emerald}{  dom对象就是浏览器根据html标签生成的js对象}$

  所有的标签属性都可以在这个标签上找到

  修改这个对象的属性会映射到标签上

  dom的核心思想就是把网页内容当做对象来处理

- document对象是dom里提供的一个对象,他所提供的属性和方法都是用来访问和操作网页内容的,网页所有的内容都在这个document/文档里  

- 节点分类

  1. 【元素节点】其实就是 HTML 标签，如上图中 `head`、`div`、`body` 等都属于元素节点。
  2. 【属性节点】是指 HTML 标签中的属性，如上图中 `a` 标签的 `href` 属性、`div` 标签的 `class` 属性。
  3. 【文本节点】是指 HTML 标签的文字内容，如 `title` 标签中的文字。
  4. 【根节点】特指 `html` 标签。

#### 获取dom对象

------

#####   获取dom元素

- 基本原理:根据css选择器来获取dom元素

- 语法

  ```javascript
  document.querySelector('div') // 单个
  ```

- 特点

  1. 当应用标签或者类选择器时,只获取$\textcolor{Emerald}{  第一个}$满足条件的元素
  2. 直接打印的话,返回的是[object HTMLDivElement] html div标签对象(根据选择器的不同div部分会有所调整,但是$\textcolor{Emerald}{  一直都是一个object}$)
  3. 在整个document里都无法匹配的话会返回null
  4. 后代选择器,结构伪类选择器统统适用于此结构,不存在任何限制

- 语法

  ```javascript
         const lis = document.querySelectorAll('ul li')
          lis[2].innerHTML = '我才是真的第一哈哈哈哈'
  ```

- 特点

  1. 运用此方法获取到的是一个伪数组,是一组可以用下标来获取的数据,$\textcolor{Emerald}{  下标是从0开始的}$
  2. 要想得到里面的每一个对象,则需要遍历for的方式获得
  3. 哪怕只有一个元素,通过querySelectAll()获取过来的也是一个伪数组,只是里面只有一个元素

- 这两个语法的括号里都必须是字符串必须加引号

##### 其它获取dom元素的方法

- 语法

  ```javascript
    const box = document.getElementById('box')
  ```

  按照给的id获取一个元素

- 语法

  ```javascript
   const boxs = document.getElementsByTagName('div')
  ```

  按照给的标签名获取一类标签

- 语法

  ```javascript
    const boxss = document.getElementsByClassName('box')
  ```

  按照给的标签名获取所有叫同一个类名的标签

#### 操作元素的内容

------

##### innerText

- dom对象本质上就是对象,就是操作对象使用的点语法

- 通过innerText我们可以将文内容添加/更新到任意标签位置

- $\textcolor{Emerald}{  只能显示纯文本,不解析标签}$

- 语法

  ```javascript
     const box = document.querySelector('.box')
     box.innerText = '五一仅仅放了一天假'
  ```

##### innerHTML 

- 将文本内容添加/更新到任意标签位置
- $\textcolor{Emerald}{  能够解析标签,建议使用模板字符串}$

#### 操作元素属性

------

##### 操作元素常用属性

- 语法

  ```javascript
     const img = document.querySelector('img')
      img.src = './images/2.webp'
      img.alt = '刘德华'
      img.title = 'pink老师真帅'
  ```

##### 操作元素样式属性

- 语法

  ```javascript
     const box = document.querySelector('.box')
      box.style.border = `10px solid #000`
  ```

  此方式是通过style属性操作css,会直接生成一个行内样式,覆盖本来的样式

  > $\textcolor{Emerald}{  当属性之间有连接符时,统统需要换成小驼峰命名法哦~}​$
  >
  > background-color  变成  backgroundColor
  >
  > 赋值的时候,很多属性值都是需要加单位的,千万不要忘记哦

- 语法

  ```javascript
      const box = document.querySelector('div')
      box.className = 'box1 '
  ```

  由于class是关键字,所以使用classname去代替

  classname是使用新值换旧值

- 语法

  ```javascript
      const box = document.querySelector('.box1')
      //给 box 对象 添加一个类名 box 
      box.classList.add('box')
      //移除指定的类名 
      box.classList.remove('box1')
      //如果有这个类名 就移除 如果没有就添加 切换
      box.classList.toggle('box')
  ```

  classlist一个显著的优点是它只追加和删除不影响以前的类名

##### 操作表单元素属性

- 语法

  ```javascript
     const input = document.querySelector('.hobby')
     input.checked = false
  ```

  单选框的checked属性为false就是没选中,true是选中

- 语法

  ```JavaScript
      const btn = document.querySelector('button')
      btn.disabled = false 
  ```

  btn的disabled属性为true时禁用,为false时启用

##### 自定义属性

- 这是html专门开辟出来的一种以data-开头的自定义属性

- $\textcolor{Emerald}{  在标签上一律以data-开头}$

- 语法

  ```javascript
    <div class="box" data-index="0" data-abcd="22"></div>
    <script>
      const box = document.querySelector('.box')
      console.log(box.dataset.abcd)
    </script>
  ```

#### 定时器-间歇函数

- 开启语法

  ```javascript
    let id = setInterval(function () {
        console.log('今天真热');
      }, 500)
      console.log(id)
  ```

  ```javascript
      function fn() {
        console.log('查镇真好看')
      }
  
      // setInterval(fn, 1000)
  ```

- 一个值为函数,第二个值为间隔时间,单位为毫秒

- 注意函数名不加括号

- 定时器返回的是一个数字(随机生成)

- 关闭语法

  ```javascript
      let id = setInterval(function () {
        console.log(i)
        i++
        if (i > 10) {
          // 清除定时器
          clearInterval(id)
          // i = 1
        }
      }, 200)
  ```

  

  

