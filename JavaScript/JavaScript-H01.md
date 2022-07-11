#### 作用域

------

##### 局部作用域

- 局部作用域分为块级作用域和函数作用域

- 函数作用域

  ```javascript
        function fn(){
              let num = 123;
          }
          fn()
  ```

  在函数内部声明的变量只能在函数内部被访问,外部无法直接访问

  函数的参数也是函数内部的的局部变量

  不同函数内部声明的变量无法互相访问

  函数执行完毕后,函数内部的变量实际被清空了

- 块级作用域

  ```javascript
         {
              let str='aaa'
          }
  ```

  在JavaScript中使用{}包裹的被称为代码块,内部声明的变量外部将有可能无法访问

  let/const声明的变量会产生块作用域,var不会

  不同代码块之间的变量无法互相访问

##### 全局作用域

- script标签和js的最外层就是所谓的全局作用域,在此声明的变量在函数内部也可以被访问

  ```javascript
       // chapter one 在script里定义的全局变量
          let num = 123 
          function fn(){
              console.log(num)
          }
          fn()
  ```

  ```javascript
          // chapter two 在js文件中定义的变量,跨域文件和跨域script标签也可以访问
          console.log(str)
  ```

  为window对象动态添加的属性默认也是全局的

  函数中未使用任何关键字声明的变量为全局变量

  尽可能少的声明全局变量,防止全局变量被污染

##### 作用域链

- 作用域链本质上是底层的变量查找机制

  在函数被执行时,会优先查找当前函数作用域中的变量

  如果在当前作用域中查找不到则会逐级查找父级作用域直到全局作用域

- 嵌套关系的作用域链串联起来形成了作用域链

  相同作用域链中按着从小到大的规则查找变量

  子作用域能够访问父作用域,父级作用域无法访问子级作用域

- 语法

  ```javascript
          let a = 111
          function fn1(){
              console.log(a)
          }
          fn1()
          // 取到111
  ```

  ```javascript
          let a = 111
          function fn1() {
              function fn2() {
                  let a = 222
                  console.log(a)
                // let a = 222
                // Cannot access 'a' before initialization
                // 如果先使用再定义,在使用a的时候会报错
              }
              fn2()
          }
          fn1()
          // 取到111
  
  ```

##### 闭包

- 一个函数对周围状态的引用捆绑在一起,内层函数中访问到其外层函数的作用域

  简单理解  闭包=内层函数+外层函数的变量

  ```java
        function outer(){
              let num = 123
              function inner(){
                  console.log(num)
                  // 内层的函数用到了外层的变量就构成了闭包
              }
              inner()
              console.log(num)
          }
          outer()
  ```

- 闭包的作用

  封闭数据,实现数据私有,外部也可以访问函数内部的变量

  闭包很有用,因为它允许将函数与其操作的某些数据(环境)关联起来

  同时闭包也有可能引起内存泄漏的问题

##### 变量提升

- 情况

  ```javascript
          console.log(num)
          var num = 123
          // undefined
          // 只有var有声明提升
  ```

  ```javascript
          console.log(str)
          let str = '345'
          //  Cannot access 'str' before initialization
          //  不能先使用后声明
  ```

- let/ const声明的变量不存在变量提升
  实际开发中一定要先声明再访问变量

#### 函数进阶

------

#####   函数提升

- 函数提升与变量提升比较类似,是指函数在声明之前即可被调用

- 情况

  ```javascript
          fn1()
          function fn1(){
              console.log('爷提升了想不到吧')
          }
          // 正常执行
  
  ```

  ```javascript
          console.log(fn2)
          // undefined
          fn2()
          // fn2 is not a function
          var fn2=function(){
              console.log('我可以吗')
          }
          // 将函数赋值给一个变量的时候,仅仅会提升变量但是不会提升整个函数
  ```

  函数提升能够使函数的声明调用更灵活

  函数表达式不存在提升的现象

  函数提升出现在相同作用域当中

##### 函数参数

- 动态参数

  arguments是函数内部内置的伪数组变量,它包含了调用函数时传入的所有实参
  它是一个只存在于函数内部的伪数组
  作用是动态获取函数的实参

- 剩余参数  

  剩余参数允许我们将一个不定数量的参数表示为一个数组

  ```javascript
        function getNum(...args){
              console.log(args)
              let sum =0
              for(let i = 0 ; i < arguments.length ; i++){
                  sum = sum + arguments[i]
              }
              return sum
          }
          getNum(1,2,3,4,5,6)
          console.log(getNum(1,2,3,4,5,6))
          // 接受全部参数
  ```

  ```JavaScript
          function getPart(a,b,c,...args){
              console.log(args)
          }
          getPart('susu','onerepublic','su',1,2,3,4,5,6,7)
          // 只接受一部分
  ```

  ...是一个语法符号,至于最末函数形参之前,用于获取多余的实参

  借助此语法获取的剩余实参是个真数组

- 展开运算符

  展开运算符... ,可以将一个数组进行展开

  ```javascript
         const arr = ['111','222','333','444']
         console.log(...arr)
  ```

  ```javascript
          console.log(Math.max(...[1,2,3,4,5,6]))
          console.log(Math.min(...[1,2,3,4,5,6]))
  ```

  > 剩余参数:函数参数使用,得到真数组
  >
  > 展开运算符:数组中使用,数组展开

##### 箭头函数

- 语法

  ```javascript
         const fn1 = () => {
              console.log('我是箭头函数')
          }
          fn1()
  ```

- 只有一个参数的时候可以省略小括号

  ```javascript
          const fn2 = a =>{
              console.log(a**2)
          }
          fn2(3)
  ```

- 如果只有一行代码需要返回值可以省略大括号

  ```javascript
          const fn3 = (x,y) => console.log(x+y)
          fn3(3,56)
  ```

- 加括号的函数体返回对象字面量表达式

  ```javascript
          const fn4 = (uname) =>({
              uname:uname,
              age:16,
              genser:'tu'
          })
          console.log(fn4('张三'))
  ```

##### 箭头函数参数

- 普通函数有arguments,但是箭头函数没有,不过箭头函数有剩余参数

  ```javascript
          const fn = (args) =>{
              // Found non-callable @@iterator
              console.log(...args)
          }
          fn(1,2,3,4)
  ```

##### 箭头函数的this属性

- 箭头函数不会创建自己的this,他只会从自己的作用域链的上一层沿用this

  ```javascript
          // 箭头函数指向外部的this
          let obj2 = {
              name:'李四',
              age :28,
              sayHi:() =>{
                  console.log(this)
              }
          }
          obj2.sayHi()
          //Window
  
          document.addEventListener('click',() =>{
              console.log(this)
          }
          )
          //Window
  ```

#### 解构赋值

------

##### 数组结构

- 数组解构是将数组的单元值快速批量赋值给一系列变量的简洁语法

- 赋值运算符 = 左侧的[]用于批量声明变量,右侧数组的单元值将被复制给左侧的变量

  变量的顺序对应数组单元值的位置依次进行赋值操作

- 语法

  ```javascript
          const arr = ['迪迦奥特曼','泰罗奥特曼','赛罗奥特曼']
          // 数组解构
          const[a,b,c] = arr
          console.log(a,b,c)
  ```

  数组解构是将数组的单元值快速批量赋值给一系列变量的简介语法

- 用数组解构的方法交换两个变量

  ```javascript
          // 数组解构 - 交换变量
          let num1 = 111;
          let num2 = 222;
          console.log(num1,num2);
          [num2,num1] = [num1,num2];
          console.log(num1,num2)
  ```

- js中必须加分号的情况

  ```javascript
          // 数组前面
          let num1 = 111
          let num2 = 222
          console.log(123);
          [num1 ,num2] = [num2 , num1]
  ```

  ```javascript
          // 自执行函数
          ;(function(){
              console.log('我是自执行函数')
          })();
          ;(function(){
              console.log('我是自执行函数')
          }());
  ```

- 当变量和单元值数量不一致的几种情况

  ```javascript
          // 数组中元素少,解构的变量多,变量默认undefined
          const[a,b,c,d]=[111,222,333]
          console.log(a,b,c,d)
  ```

  ```javascript
          // 数组中元素多,解构的变量少,未赋值无效
          const [e,f] = [111,222,333]
          console.log(e,f);
  ```

  ```javascript
          // 可以利用剩余参数,接收多余的数组元素
          const [g,h,...args] = [111,222,333,444]
          console.log(g,h,args)
  ```

  ```javascript
          // 可以给解构的变量,设置默认值,没赋值就是默认状态,如果被赋值,会被覆盖掉
          const [i,j = 0 , k= 0] = [111,222];
          console.log(i,j,k)
  ```

  ```javascript
          // 接收指定项
          const [l,,,m] = [111,222,333,444]
          console.log(l,m)
  ```

  ```javascript
          // 多维数组的解构
          const [n,[o,p]] = [111,[222,333]]
          console.log(n,o,p)
  ```

##### 对象解构

- 赋值运算符 = 左侧的{}用于批量声明变量,右侧对象的属性值将被赋值给左侧的变量

  对象的属性的值将被赋值给与属性名相同的变量

  ```javascript
          // 类似于数组,只不过数组有序,对象无序
          const{uname,password,age} = {uname:'张三',password:'123456',age:'17'}
          console.log(uname,password,age)
  
  ```

  ```javascript
          const pig = {name:'佩奇',age:6}
          const{name:uname , age}=pig
          console.log(uname,age)
  ```

  JavaScript支持在提取变量的时候修改新的变量名

- 对象的多级解构

  ```JavaScript
          const pig = {
              name: '佩奇',
              age: 6,
              family: {
                  mother: '猪妈妈',
                  father: '猪爸爸',
                  brother: '乔治'
              }
          }
          const{name,age,family:{mother,father,brother}}= pig
          console.log(name,age,mother,father,brother)
  ```

  ```javascript
          const arr = [
              {
                  uname: '佩奇',
                  uage: 6,
                  ufamily: {
                      umother: '猪妈妈',
                      ufather: '猪爸爸',
                      ubrother: '乔治'
                  }
              }
          ]
          const[{uname,uage,ufamily:{umother,ufather,ubrother}}]= arr
          console.log(uname,uage,umother,ufather,ubrother)
  ```

  ```javascript
          let obj = {
              code: 200,
              msg: '获取新闻列表成功',
              data: [
                  { id: 1, title: '特大喜讯1...', count: 33 },
                  { id: 2, title: '特大喜讯2...', count: 44 },
                  { id: 3, title: '特大喜讯3...', count: 55 },
              ]
          } 
  
          const { data: res } = obj;
          console.log(res);
  ```

  