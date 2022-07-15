#### 深浅拷贝

------

##### forin&forof

- forin的作用是遍历元素的索引值,可以遍历原型中的属性,可以遍历对象
- forof的作用是遍历元素,不可以遍历属性,不可以遍历对象
- 简单来说就是$\textcolor{red}{forin多用于遍历对象}$,$\textcolor{red}{forof多用于遍历数组}$

##### 基础知识

- 简单数据类型传递的是值,复杂数据类型需要传递的是地址

- 简单类型的赋值,原值改变,被赋值的变量并不受到影响

  复杂数据类型赋值,原值也会改变,被赋值的变量也受到了影响

- $\textcolor{red}{深浅拷贝都是针对引用数据而言的}​$

##### 浅拷贝

- 浅拷贝拷贝的是$\textcolor{red}{地址}$

- 浅拷贝的常用思路是利用assign方法和...展开运算符,这样可以做到不影响之前的数据

  (数组和对象都是一样的思路,数组不使用assign,使用concat)

- 对于复杂数据类型的拷贝,拷贝的也是地址,依然存在影响的问题

- 应用

  ```javascript
          // 数组浅拷贝
          const arr = ['111', '222', '333']
          const arr1 = [...arr]
          arr1[2] = '444'
          const arr2 = arr.concat()
          arr2[0] = '000'
          console.log(arr)
          // 0: "111"
          // 1: "222"
          // 2: "333"
          console.log(arr1)
          // 0: "111"
          // 1: "222"
          // 2: "444"
          console.log(arr2)
          // 0: "000"
          // 1: "222"
          // 2: "333"
  
  
          // 对象浅拷贝
          const obj = { name: 'zkx', age: 23, gender: '女' }
          const obj1 = { ...obj }
          obj1.name = 'gxxl'
          const obj2 = {}
          Object.assign(obj2, obj)
          obj2.age = 27
          console.log(obj)
          // {name: 'zkx', age: 23, gender: '女'}
          console.log(obj1)
          // {name: 'gxxl', age: 23, gender: '女'}
          console.log(obj2)
          // {name: 'zkx', age: 27, gender: '女'}
  ```

##### 深拷贝

- 深拷贝拷贝的是$\textcolor{red}{对象的值}$,无论是简单类型还是复杂类型

  深拷贝之后,两个对象之间是完全不会互相影响的

- 深拷贝的思路一 :  JSON.parse(JSON.stringify(a1))

  用json指令先将对象转换为字符串再转回来,但是要注意,这个方法并$\textcolor{red}{不识别函数}$

  应用

  ```javascript
          const a1 = {name:'zkx',age:23,book:['红宝书','犀牛书'],fn : ()=>124}
          let a2 = JSON.parse(JSON.stringify(a1))
          a1.name = 'gxxl'
          a1.book.push(['css','算法'])
          console.log(a1)
          // {name: 'gxxl', age: 23, book: Array(3), fn: ƒ}
          console.log(a2)
          // {name: 'zkx', age: 23, book: Array(2)}
  ```

- 深拷贝思路二  :   js库 lodash

  示范:

  ```javascript
          const a1 = {name:'zkx',age:23,book:['红宝书','犀牛书'],fn : ()=>124}
          let a2 = _.cloneDeep(a1)
          console.log(a1)
          console.log(a2)   
  ```

  这是一个比较强大的js库,除了深拷贝,还可以完成其他的功能,详情参见官网技术文档

- 深拷贝的思路三  :   递归思想(lodash的底层思想)

  简单来说,递归就是一个自己调用自己的过程

  应用示范:

  ```javascript
          // 满足条件跳出
          let num = 0                   // 1
          function fn() {               // 2    
              num++
              console.log(num)          // 3         
              if (num >= 5) {           // 4    
                  return                // 5    
              }
              fn()
          }
          fn()
  
          // 满足条件开始递归
          let sum =0
  
          function fn1() {
              sum++
              console.log('我是递归')
              if (sum <= 5) {
                  fn1()
              }
              // 不调用不执行
          }
          fn1()
  ```

  用递归实现深拷贝需要用到遍历和判断,遍历每一个需要复制的元素,判断是否为基础数据类型,如果不是则进行迭代

#### 异常处理

------

##### throw抛出异常

- 异常处理是指预估代码中可能出现的错误,然后最大程度的避免错误导致这个程序无法继续运行

- 实例

  ```javascript
          const e1 = new Error('this is our definition of the first error')
          console.log(e1.name, e1.message)
          console.log(e1)
  
          throw e1;
          console.log('抛出错误之后,后面的代码将不再执行')
  ```

  throw抛出异常信息之后,程序也会终止执行,

  throw后面跟的是错误提示信息

  error对象配合throw使用,能够设置更详细的错误信息

  > throw会终止程序

##### try/catch捕获异常

- 我们可以通过try/catch捕获浏览器提供的错误信息

- 实例

  ```javascript
          try {
              document.querySelector('asdf').style.color = 'red'
          }catch(err){
              console.error('注意,您使用的选择器在页面中找不到对应的标签!!!')
          }
  
          console.log('模拟1w行代码')
  ```

  try/catch用来捕获错误信息,将预估可能发生的错误代码写在try代码段中

  如果try代码段中的错误出现后,会执行catch代码段,并截获到错误信息

  > finally是不管是否有错误最后都会执行的代码

##### debugger

- 我们可以通过try / catch 捕获错误信息（浏览器提供的错误信息）

#### this的处理

------
##### this的指向问题

- this指向的最好检验方法是log

- 实例

  ```javascript
          // 普通函数指向window
          function fn(){
              console.log(this)
              // Window {window: Window, self: Window, document: document, name: '', location: Location, …}
          }
          fn()
  
          // 普通对象方法中的this指向这个对象
          let obj = {
              name:'zs',
              age:18,
              sayHi:function(){
              console.log(this)
              // {name: 'zs', age: 18, sayHi: ƒ}
          }
          }
  
          obj.sayHi()
  
          // 构造函数中的this指向实例对象
          function Star(name,age){
              this.name = name
              this.age = age
              console.log(this)
              // Star {name: '李四', age: 22}
          }
          let s1 = new Star('李四',22)
  
          // 原型方法中的this
          Star.prototype.sing = function(){
              console.log(this)
          }
          s1.sing()
  
          // 事件绑定中的this指向事件源
          document.addEventListener('click',function(){
              console.log(this)
              // document
          })
  
          // 定时器里面的this指向window
          setTimeout(function(){
              console.log(this)
              // Window {window: Window, self: Window, document: document, name: '', location: Location, …}
          },1000)
  
          // 箭头函数的this指向外层
          let obj2 = {
              name:'王五',
              age:18,
              sayHi:() =>{
                  console.log(this)
                  // Window {window: Window, self: Window, document: document, name: '', location: Location, …}
              }
          }
          obj2.sayHi()
  ```

  > 普通函数被谁调用,this就指向谁
  >
  > 严格模式下普通函数的this指向undefined

- 特别注意箭头函数中的this与普通函数完全不同,也不受调用方式的影响,事实上箭头函数甚至并不存在this

  箭头函数会默认绑定外层函数的this值,所以在箭头函数中this的值和外层的this是一样的

  箭头函数中的this引用的就是最近作用域中的this

  向外层作用域中,一层一层的查找this,直到有this的定义

  使用箭头函数前需要考虑函数中this的值,事件回调函数使用箭头函数时,this为全局的window,因此dom事件回调函数如果里面需要dom对象的this,则不推荐使用箭头函数


##### this的改变

- 一共有三个方法可以改变this的指向

  ```javascript
          function fn(a,b){
              console.log(a+b)
              console.log(this)
          }
          fn(1,2)
  
          let obj = {name:'zs',age:24}
          fn.call(obj,222,333)
  
          console.log(Object.prototype.toString.call('abc'))
          // [object String]
          console.log(Object.prototype.toString.call(12345))
          // [object Number]
          console.log(Object.prototype.toString.call(true))
          // [object Boolean]
          console.log(Object.prototype.toString.call([1,2,3]))
          // [object Array]
          console.log(Object.prototype.toString.call(new Date()))
          // [object Date]
  ```

  第一个方法是call(),call里面的第一个参数是用来指定this的,其余是实参,传递是参数

  ```javascript
          function fn(a,b){
              console.log(a+b);
              console.log(this);
          }
          fn(1,2)
          fn.apply(document,[2,3])
  
          let arr = [1,2,13,4,5]
          console.log(Math.max.apply(Math,arr))
  ```

  第二个方法是apply(),这个方法的第一个参数也是用来设置this的,第二个参数是数组(也必须是数组),进行传参

  ```javascript
      <button>1</button>
      <button>2</button>
      <button>3</button>
     <script>
      function fn(a,b){
          console.log(a+b)
          console.log(this)
      }
      fn(1,2)
      const f1 = fn.bind(document,2,3)
      console.log(f1)
      f1()
  
      let btns = document.querySelectorAll('button')
      for(let i = 0 ; i <btns.length ; i++){
          btns[i].addEventListener('click',function(){
              setTimeout(function(){
                  this.disabled = true
              }.bind(this),3000)
          })
      }
     </script> 
  ```

  bind()方法不会调用函数,但是能改变函数内部this指向

  返回由指定的this值和初始化参数改造的原函数拷贝(新函数)

  因此当我们只是想改变this指向,并不想调用这个函数的时候,可以使用blind,比如改变定时器内部的this指向

#### 性能优化

------

##### 节流

- 所谓节流,就是指连续触发事件但是在n秒中只执行一次函数

- lodash库中有已经完成的成熟的节流API

- 实例

  ```javascript
      let box = document.querySelector('.box')
      function fn(){
        box.innerHTML = ++num
      }
      box.addEventListener('mousemove',_.throttle(fn,1000))
  ```

##### 防抖

- 就是指触发事件后在n秒钟内函数只能执行一次,如果在n秒钟又触发了事件,则会重新计算函数执行时间

- lodash中也有成熟的防抖API

- 实例

  ```javascript
      let num = 1
      let box = document.querySelector('.box')
      function fn(){
        box.innerHTML = ++num
      }
  
      box.addEventListener('mousemove',_.debounce(fn,1000))
  ```

  