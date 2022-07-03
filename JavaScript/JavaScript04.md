#### 函数

------

##### 函数的基本概念

- 函数就是将一段代码封装起来反复复用(alert ,promp都是一些已经封装好我们可以直接调用的函数),也就是一段执行特定任务的代码块
- 关键字:function
- 一个完整的函数包括:关键字+函数名+形式参数+函数体+返回值五个部分

##### 函数的使用

- 声明

  ```js
     function sayHi (name){
              console.log(`hi,${name}`)
          }
  
  ```

- 函数的命名规则

  01 和变量命名的方法基本一致

  02 尽量使用小驼峰命名法

  03 前缀尽可能使用动词(can has is get add set load)

- 函数的调用语法

  ```js
   sayHi('强宝')
  ```

  > 我们之前使用的alert(),parseInt()这种名字后面跟小括号的本质上都是函数的调用

- 函数体是函数的构成部分,即大括号括起来的部分,直到函数调用时函数体内的代码才会被执行

##### 函数传参

- 传参可以极大的提高函数的灵活性

- 传参

  ```js
       function add (num1,num2){
              let sum = num1 +num2
              document.write(sum)
          }
  ```

  ```js
   function sayHi (name){
              console.log(`hi,${name}`)
          }
  ```

  > 参数可以是一个也可以是多个,用逗号隔开即可

- 声明函数时写在函数名右边小括号里的叫形参(形式上的参数)

  调用参数时写在函数名右边小括号里的叫实参(实际上的参数)

- 开发中尽量保持形参和实参的个数一致

##### 函数返回值

- 当调用某个函数时,这个函数会返回一个结果出来,这就是有返回值的函数

- 当然也有很多函数并不存在返回值,这是需要根据条件来判断的

- 当需要将返回数据出去时,用return关键字

- return后面的代码不会再执行,会立即结束当前函数,所以return后面的数据不要换行写

- return函数可以没有return,这种情况函数默认返回值为undefined

- 函数之间也存在覆盖,两个相同的函数,后面覆盖前面

- 函数的形参和实参并不严格要求相等,形参过多补填undefined,实参过多多余的都会被自动忽略

- 返回多个值

  ```js
    function getMin(arr){
              for( let i=0 ; i<arr.length; i++){
                  for(j=i ; j< arr.length ; j++){
                      if(arr[i]>arr[j]){
                          let temp = arr[i]
                          arr[i]=arr[j]
                          arr[j]=temp
                      }
                  }
              }
              return [arr[0],arr[arr.length-1]]
          }
  
          let a = getMin([12,45,789,34,2,-1])
          document.write(`最小值是${a[0]}最大值是${a[1]}`)
  ```

  > 返回多个值的最简单方法就是传出一个数组,实参可以是任意的数据类型

  ```js
    function getMin(arr){
              for( let i=0 ; i<arr.length; i++){
                  for(j=i ; j< arr.length ; j++){
                      if(arr[i]>arr[j]){
                          let temp = arr[i]
                          arr[i]=arr[j]
                          arr[j]=temp
                      }
                  }
              }
              return `最小值是${arr[0]}最大值是${arr[arr.length-1]}`
          }
          document.write( getMin([12,45,789,34,2,-1]))
  ```

  > 也可以返回一个拼接字符串

- 在函数中遇到break只结束当前循环,遇到return后整个函数结束执行

##### 作用域

- 通常来说一段程序中所用到的名字并不总是有效可用的,这个名字的可用性代码范围就是这个名字的作用域

- 作用域提高了代码的程序逻辑的局部性,增强了代码的可靠性,减少了名字冲突

- 两种常见情况

  | 名称       | 特点                                       | 特点                                 |
  | ---------- | ------------------------------------------ | ------------------------------------ |
  | 全局作用域 | 作用域是整个script标签或者一个独立的js文件 | 全局变量在任何区域都可以访问和修改   |
  | 局部作用域 | 也称为函数作用域,局部生效                  | 局部变量只能在当前函数内部访问和修改 |

- 有时候出现了变量冲突可能是因为函数中的某个变量未声明,变成了全局变量

- 函数内部的形参是局部变量

- 函数的访问原则

  01 只要是代码,就至少有一个作用域

  02 写在函数内部的局部作用域

  03 如果函数中还有函数,那么在这个作用域中就又可以诞生一个作用域

  04 在能够访问到的情况下先布局,局部没有再找全局(就近原则)

##### 匿名函数

- 没有名字的函数无法直接使用,但是我们可以用函数表达式和立即执行函数构造出匿名函数

- 函数表达式语法

  ```js
  let fn = function(){
              console.log('hello, 帅哥')
          }
  ```

  将匿名函数值赋给一个变量,并且通过变量名称进行调用,我们将这个称为函数表达式

- webAPI写法

  ```js
    btn.onclick= function(){
              console.log('hello, 帅哥')
          }
  ```

  需要结合webAPI来理解和应用

- 立即执行函数

  ```js
    (function(){
              console.log(11)
          })();
  ```

  ```js
      (function(){
              console.log(11)
          }());
  ```

  立即执行函数不需要调用,本质已经出现即执行了

  多个立即执行函数之间用分号隔开

- 函数表达式调用必须写在后面,具名函数调用在前面和后面都可以

  
