#### 事件监听

------

- 事件是在编程时系统内发生的动作或者发生的事,比如在网页上单击一个按钮或者按下键盘上的一个键

- 事件监听就是让程序检测是否有事发生,一旦有事件触发,就立即调用响应的函数进行响应,也称为绑定事件或者注册事件

- 语法

  ```javascript
   prev.addEventListener('click', function () {
        i--
      })
  ```

- $\textcolor{Emerald}{  事件监听的三要素}$

  事件源:哪个dom元素被事件触发了,要获取哪一个dom元素

  事件类型:用什么方式触发,比如是单击鼠标click还是鼠标经过等

  事件调用的函数:要做什么事

- 事件类型(click / keydown)需要加引号

- 函数是点击之后再去执行的,每次点击都会执行一次

#### 事件类型

------

##### 鼠标事件

- click 鼠标点击

  ```javascript
    box.addEventListener('click',function(){
              console.log('我点击啦')
          })
  ```

- dblclick鼠标双击

  ```javascript
    box.addEventListener('dblclick',function(){
              console.log('我双击啦')
          })
  ```

- mouseenter 鼠标经过

  ```javascript
    box.addEventListener('mouseenter',function(){
              console.log('我经过啦')
          })
  ```

- mouseleave 鼠标离开

  ```javascript
    box.addEventListener('mouseleave',function(){
              console.log('我离开啦')
          })
  ```

##### 焦点事件

- focus 获得焦点

  ```javascript
    box.addEventListener('focus',function(){
              console.log('我拿到焦点啦')
          })
  ```

- blur 失去焦点

  ```javascript
    box.addEventListener('blur',function(){
              console.log('我释放焦点啦')
          })
  ```

##### 键盘事件

- 键盘按下触发keydown

  ```javascript
  box.addEventListener('keydown',function(){
              console.log('按下了键盘')
          })
  ```

- 键盘抬起触发keyup

  ```javascript
  box.addEventListener('keyup',function(){
              console.log('抬起了键盘')
          })
  ```

##### 文本事件

- 表单输入触发 input

  ```javascript
  box.addEventListener('input',function(){
              console.log('你正在输入')
          })
  ```

  

#### 事件对象

------

- 事件对象是一个object,在这个对象里有事件触发时的相关信息

- $\textcolor{Emerald}{  在事件绑定的回调函数里的第一个参数就是事件对象(一般命名为e)}$

- 事件对象的常用属性

  | 属性      | 功能                                     |
  | --------- | ---------------------------------------- |
  | type      | 获取当前的事件类型                       |
  | clientX/Y | 获取光标相对于浏览器可见窗口左上角的位置 |
  | offsetX/Y | 获取光标相对于当前dom元素左上角的位置    |
  | key       | 用户按下的键盘键的值                     |

#### 环境对象

------

- $\textcolor{Emerald}{  环境对象指的是函数内部的特殊的 变量this,它代表着当前函数运行时所处的环境}$
- 作用:弄清楚this的指向,可以让我们的代码更简洁
- 粗暴理解:谁在调用这个函数,谁就是这个函数里的this
- 直接调用函数的时候,其实相当于是window函数,所以this指代window

#### 回调函数

------

- $\textcolor{Emerald}{  如果将函数A作为参数传递给函数B,我们就称函数A为回调函数}$

- 当一个函数当做参数来传递给另外一个函数的时候,这个函数就是回调函数

- 语法

  ```javascript
      function fn(){
              console.log('我是回调函数')
          }
          setInterval(fn,1000)
  ```

  ```javascript
     box.addEventListener('click',function(){
              console.log('我也是回调函数')
          })
  ```

- 回调函数的本质还是函数,只不过把它当成参数来使用

- 使用匿名函数作为回调函数比较常见