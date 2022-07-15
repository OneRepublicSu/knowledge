#### 编程思想

------

##### 面向过程

- 面向过程就是分析出解决问题所需要的$\textcolor{red}{步骤}$,然后用函数那这些步骤一步一步实现,使用的时候再一个一个的依次调用就可以了.

- 性能比面向对面高,适合跟硬件联系很紧密的东西,比如单片机

- 不易维护,不易复用,不易扩展

  > 大型项目更加适合面向对象的方式,简单小体量的工程适合面向过程

##### 面向对象

- 面向对象就是把事务分成一个一个$\textcolor{red}{对象}$,然后对象之间分工与合作

- 面向对象是以对象功能来划分问题而不是步骤

- 特征:$\textcolor{Emerald}{ 灵活,代码可复用,容易维护和开发(封装性/继承性)低耦合,但是性能比面向过程低}$

  > 在前端中,面向过程编程更加常见

##### 构造函数

------

##### 基础概念

- 我们的主要任务是使用对象而不是封装对象
- 封装过程将同样的变量和函数组合到了一起并且能通过this实现数据的共享,$\textcolor{Emerald}{但是借助构造函数创建出的实例对象是彼此互不影响的}$
- 构造函数的方法缺点:存在浪费内存的影响
- $\textcolor{Emerald}{ 对于复杂数据类型而言,全等比较的是内存地址}$
- 构造函数内部的属性是静态成员,很显然,实例对象(构造函数生成的对象)中的成员,和静态成员是互不影响的,实例对象无法访问静态成员

##### 原型

- 构造函数通过原型分配的函数时所有对象所共享的

- JavaScript规定,每一个构造函数都有一个 prototype 属性，指向另一个对象，所以我们也称为原型对象

- 我们可以把那些不变的方法，直接定义在 $\textcolor{red}{prototype}​$对象上，这样所有对象的实例就可以共享这些方法

- Q:为什么所有的实例对象都可以访问 prototype 属性中的值?

  A:因为所有实例对象上的_ proto _  都指向它的构造函数原型(prototype属性),所以实例上没有的属性和方法,都可以在 _ proto _中寻找 

- 构造函数里面的对象都指向实例对象,构造函数的原型对象中的this也指向实例对象,依然符合:$\textcolor{red}{谁调用this就指向谁}$

- 演示

  ```javascript
          function Star(name , age){
              this.name  = name
              this.age = age
          }
          Star.prototype.sing = function(){
              console.log(this)
          }
          const s1 = new Star('罗渽民','dream')
          s1.sing()
          // 结果打印了star age: "dream" name: "罗渽民" 
          // 很明显,实例调用了原型对象,原型对象的this就会指向调用它的实例
  ```

##### constructor属性

- 实例对象都可以通过$\textcolor{Emerald}{ constructor属性}$获取它的构造函数,因为构造函数原型中包含这个属性
- 如果有多个对象的方法,我们可以给原型对象采取对象形式赋值,,但是这样就会覆盖构造函数原型对象原来的内容,这样修改后的原型对象constructor就不再指向当前构造函数了,此时我们可以在修改后的原型对象中添加一个constructor指向原来的构造函数

##### 对象原型

- 对象都会有一个属性__ proto __ 指向构造函数的prototype原型对象,之所以我们对象可以使用构造函数prototype原型对象的属性和方法,就是因为对象有__ proto __$\textcolor{Emerald}{原型}$的存在
- __  proto  __是JS非标准属性
- [[prototype]]和__ proto __ 意义相同,用来表明当前实例对象指向哪个原型对象prototype
- __ proto __对象原型里面也有一个 constructor属性，指向创建该实例对象的构造函数

##### 原型链

- 图示

  ![原型链.png](https://s2.loli.net/2022/07/13/tQXbSgeVWiyGlHF.png)

  基于原型对象的继承使得不同构造函数的原型对象关联在一起,并且这种关联的关系是一种链状的结构,我们将原型对象的链状结构关系为原型链

- $\textcolor{Emerald}{原型链实际上就是定义了一种查找规则}​$

   当访问一个对象的属性(包括方法)时,首先查找这个对象自身有没有该属性

  如果没有就查找它的原型(也就是__ proto __ 指向构造函数的prototype原型对象)

  如果还没有就查找原型对象的原型(object的原型对象)

  依次类推一直找到object为止(null)

  __ proto __对象原型的意义就在于为对象成员查找机制提供一个方向，或者说一条路线

  可以使用  instanceof 运算符用于检测构造函数的 prototype 属性是否出现在某个实例对象的原型链上

##### 原型继承

- 适用于超大型项目(框架级)

- 继承是面向对象编程的另一个特征,通过继承进一步提升代码封装的程度,JavaScript中大多是借助原型对象实现继承的特征

- 示例

  ```javascript
          function Cat (name ,age){
              this.name = name 
              this.age = age 
          }
          Cat.prototype.eat = function(){
              console.log('可爱猫猫吃')
          }
          
          function  Miumiu(name , age ,color){
              this.name = name
              this.age = age
              this.color = color
          }
  
          Miumiu.prototype = new Cat()
          const s1 = new Miumiu('miao',3,'白')
          s1.eat()
  ```

  要想完成正确的继承我们要先宏观来看再微观来看,先看共有的属性和方法有哪些,进行封装,一般公共属性写到构造函数内部,公共方法写在构造函数的原型里,之后继承方通过prototype继承了公共属性后还可以创建自己独有的属性和方法

  

