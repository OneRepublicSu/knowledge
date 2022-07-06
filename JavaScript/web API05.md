#### M端事件

------

- 移动端也有自己独特的地方,比如触屏事件,也称touch触摸事件

- 常见的touch事件如下

  | touch事件  | 说明                          |
  | ---------- | ----------------------------- |
  | touchstart | 手指触摸到一个dom元素时触发   |
  | touchmove  | 手指在一个dom元素上滑动时触发 |
  | touchend   | 手指从一个dom元素上移开时触发 |

#### js插件

------

- 网址:https://www.swiper.com.cn/ 

- 使用方法:

  首先建一个lib文件夹引入swiper文件

  $\textcolor{Emerald}{  css和js文件都放在package文件夹中}$

  可以在demo中找到自己需要的案例效果进行修改,也可以去官网找自己demo查看源代码进行复制

  不要忘记加上js初始化代码,需要添加任何效果都可以去官网的API接口中寻找相应的代码修改方法以及指令进行添加

#### 重绘和回流

------

- 页面的渲染过程

  解析(parser)html,生成dom树

  同时解析(parser)css,生成样式规则

  根据dom树和样式规则,生成渲染树(render tree)

  进行布局(回流/重排)layout 根据生成的渲染树,得到节点的几何信息/位置大小

  进行绘制 painting(重绘):根据计算和获取的信息进行整个页面的绘制

  display:展示

- 回流/重排

  当render tree中部分或者全部元素的尺寸,结构,布局等发生改变时,浏览器就会重新渲染部分或全部文档的过程称为回流

- 重绘

  由于节点/元素的样式的改变并不影响到它在文档流中的位置和文档布局,所以我们把这个过程称为重绘

  > $\textcolor{Emerald}{  重绘不一定引起回流,而回流一定会引起重绘}$

- 会导致重绘和回流的操作

  页面的首次刷新

  浏览器的窗口大小发生改变

  元素的大小或者位置发生改变

  改变字体的大小

  内容的变化(如:input框的输入,图片的大小)

  激活css伪类,如::hover

  脚本dom操作(添加或者删除可见的dom元素)

  > 简单理解就是一旦影响到布局,就会发生回流

#### window对象

- bom(浏览器对象模型)

  browser object model是浏览器对象模型

- $\textcolor{Emerald}{  window对象是一个全局对象,也可以说是JavaScript中的顶级对象}$

- 像document,alert(),console.log()这些都是window的属性,基本bom的属性和方法都是window的

- 所有通过var定义在全局作用域中的变量,函数都会变成window对象的属性和方法

- window对象下的属性和方法调用的时候可以省略window

#### 定时器-延时函数

- JavaScript内置的一个用来让代码延迟执行的函数

  ```javascript
  setTimeout(function(){
                  console.log('okk')
              },3000)
  ```

- settimeout仅仅只执行一次,所以可以理解为就是把一段代码延迟执行,平时省略window

- 清除延时函数

  ```javascript
      let id = setTimeout(function(){
                  console.log('okk')
              },3000)
            
       clearTimeout(id)      
  ```

  > 延时器需要等待,所以后面的代码会先执行
  >
  > 每一次调用延时器都会产生一个新的延时器

  





