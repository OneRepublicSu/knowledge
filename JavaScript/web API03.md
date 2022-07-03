#### 事件流

------

##### 事件流

- 事件流指的是事件完整执行过程中的流动路径
- 假设页面里有一个div,$\textcolor{Emerald}{  当触发事件时,会经历两个阶段,分别是捕获阶段,冒泡阶段}$
- 简单来说:捕获阶段是$\textcolor{red}{从父到子}$,冒泡阶段是$\textcolor{red}{从子到父}​$
- 实际工作中都是使用事件冒泡为主

##### 事件捕获

- 事件捕获就是从dom的根元素开始去执行对应的事件,从外到里

- 事件捕获需要写对应的代码才能看到效果

- 语法

  ```javascript
  //捕获根节点 
  document.addEventListener('click', function () {
              console.log(1)
          }, true)
   //捕获父元素
  document.querySelector('.father').addEventListener('click', function () {
              console.log(2)
          }, true)
   //捕获子元素   
  document.querySelector('.son').addEventListener('click', function () {
              console.log(3)
          }, true)
  ```

  addEventListener的第三个参数为true就代表触发阶段

- L0事件的监听只有冒泡阶段,没有捕获

##### 事件冒泡

- 概念:$\textcolor{Emerald}{  当一个元素的事件被触发的时候,同样的事件将会在该元素的所有祖先元素中被依次触发,这一过程被称为事件冒泡}$

- 简单理解:当一个元素被触发之后,会依次向上调用所有父级元素的同名事件

- 事件冒泡行为是默认存在的

- L2监听事件的第三个参数是false,或者默认是冒泡

- 语法

  ```javascript
   //根元素
  document.addEventListener('click', function () {
              console.log(1)
          }, false)
        //父元素被触发
  document.querySelector('.father').addEventListener('click', function (e) {
              console.log(2)
      //阻止冒泡
              e.stopPropagation()
          }, false)
  //子元素
  document.querySelector('.son').addEventListener('click', function () {
              console.log(3)
          }, false)
  ```


##### 阻止冒泡

- 原因:因为冒泡是默认存在的,所以容易导致事件影响到父级元素,如果想把事件就限制在当前元素内,就需要阻止事件冒泡

- 语法

  ```javascript
  document.querySelector('.father').addEventListener('click', function (e) {
              console.log(2)
      //阻止冒泡
              e.stopPropagation()
          }, false)
  ```

  > 此方法可以阻断事件流动传播,不光在冒泡阶段有效,捕获阶段也有效


- 阻止默认行为

  有些情况下我们需要阻止默认行为的发生,比如阻止链接的跳转,表单域的跳转

- 语法

  ```javascript
  document.querySelector('form').addEventListener('click',function(e){
              alert('听又听不懂,学又学不废')
              //阻止默认事件
              e.preventDefault()
          })
  ```

##### 解绑事件

- L0版本的点击事件可以直接使用null来覆盖

  ```javascript
    btn.click = function (){
              alert('点击了')
          }
          btn.onclick = null
  ```

- 事件监听版本的解绑语法如下

  ```javascript
          function fn(){
              console.log('表妹我出来了噢')
          }       document.querySelector('#btn').addEventListener('click',fn)
      document.querySelector('#btn02').addEventListener('click',function(){
      //移除btn的绑定事件  
          document.querySelector('#btn').removeEventListener('click',fn)
          })
  
  ```
  >匿名事件无法被解绑,只有具名函数才可以被解绑

- 鼠标经过事件的区别

  $\textcolor{Emerald}{  mouseover和mouseout会有冒泡效果}$

  $\textcolor{Emerald}{  mouseenter和mouseleave没有冒泡效果}​$



#### 事件委托

------

##### 事件委托

- 事件委托是利用事件流的特征解决一些开发需求的知识技巧

- 优点:减少注册次数,可以提高程序性能

- 原理:$\textcolor{red}{事件委托其实是利用了事件冒泡的特点,给父元素注册事件,当我们触发子元素的时候,会冒泡到父元素的身上,从而触发父元素的事件}$

- 实现:$\textcolor{red}{事件对象.target. tagName }$可以获得真正触发事件的元素(就是事件源)

##### 其他事件

- 页面加载事件one

  加载外部资源加载完毕时触发的事件

  ```javascript
      window.addEventListener('load',function(){       
          })
  ```

- 页面加载事件two

  当初始的html文档被完全加载和解析完成之后,DOMContentLoaded 事件就会被触发,无需等到其他资源被完全加载

  ```javascript
  document.addEventListener('DOMContentLoaded',function(){         //执行的操作
          }) 
  ```

##### 元素滚动事件

- 滚动条在滚动的时候持续触发的事件

- 事件名:scroll

  ```javascript
      window.addEventListener('scroll',function(){           
          })
  ```

  > 此事件不仅可以监听某一个页面,还可以监听某个特定的元素

- $\textcolor{red}{scrollLeft和scrollTop}$用来获取被卷去的大小,获取元素内容在往左往上看不见的部分与距离

- 这个值是可以修改和读取的

  


