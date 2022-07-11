#### 对象

------

##### 创建对象的三种方式

- 利用$\textcolor{Emerald}{字面量创建对象}$

  ```javascript
          const a1 ={
              name:'haha',
              age : 18,
              gender :'男'
          }
  ```

- 利用new object来创建对象

  ```javascript
          const a2 = new Object()
          a2.name = 'hehe'
          a2.age = 20
          a2.gender = '女'
  ```

- 利用构造函数创建对象

  ```javascript
          function Getinfo(name,age){
              //属性
              this.name = name
              this.age = age
              //函数
              this.sleep = function(){
                  console.log(this.name+ '睡觉')
              }
              this.eat = function(food){
                  console.log(this.name+'吃'+ food)
              }
          }
  
          const s1 = new Getinfo('张三',18)
          console.log(s1)
          s1.sleep()
          s1.eat('热干面')
  ```

##### 构造函数

- 是一种特殊的函数,主要用来初始化对象

- 使用场景:创建多个$\textcolor{Emerald}{ 类似}$的对象

- 两个约定:

  > 它的命名以$\textcolor{Emerald}{ 大写字母}$开头
  >
  > 他们只能由'new'操作符来执行

- 语法

  ```javascript
   const s1 = new Getinfo('张三',18)
  ```

  使用new关键字调用函数的行为被称为实例化

  ```javascript
   const s1 = new Getinfo
  ```

  实例化构造函数的时候如果没有参数可以省略()

  构造函数内部无需写return,返回值为新创建的对象

  ```javascript
          new object()
          new Date()
  ```

  以上也是构造函数

- 案例

  ①：写一个Goods构造函数 

  ②：里面包含属性 name 商品名称 price 价格 count 库存数量 

  ③：实例化多个商品对象，并打印到控制台，例如 

  ```JavaScript
          function Goods(name,price,count){
              this.name = name
              this.price = price
              this.count = count
          }
  
          const brand1 = new Goods('小米',1999,20)
          console.log(brand1)
          const brand2 = new Goods('华为',3999,59)
          console.log(brand2)
          const brand3 = new Goods('vivo',1888,100)
          console.log(brand3)
  ```

- 实例化执行过程

  创建新对象

  构造函数this指向新对象

  执行构造函数代码,修改this,添加新的属性

  返回新对象

##### 实例成员&静态成员

- 实例成员:$\textcolor{red}{通过构造函数创建的被称为实例对象,实例对象中的属性和方法被称为实例成员}$

- 实例对象的属性即为实例成员

  为构造函数传入参数,动态创建结构相同单值不同的对象

  构造函数创建的实例对象彼此独立互不影响

- 静态成员:$\textcolor{red}{构造函数的属性和方法被称为静态成员}$

- 构造函数的属性和方法被称为静态成员

  一般公共特征的属性或方法静态成员设置为静态成员

  静态成员方法中的this指向构造函数本身

#### 内置构造函数

------

#####   object

- 在JavaScript中最主要的数据类型有6种

  基本数据类型:字符串/数值/布尔/undefined/null

  引用数据类型:对象

  js中几乎所有的数据都可以基于构成函数创建

- object是内置的构造函数,用于创建普通对象

  ```javascript
  const user = new Object({uname:'李四' , uage:16})
  ```

  > 我们更推荐用字面量的方式来声明对象

- object的三个常用静态方法

  ```javascript
          console.log(Object.keys(a1))
  ```

  .keys用来获取对象中的所有属性(返回的是一个数组)

  ```javascript
          console.log(Object.values(a1))
  ```

  .values用来获取对象中的所有属性值(返回的是一个数组)

  ```javascript
          Object.assign(a2, a1)
          console.log(a2)
  ```

  .assign 对象的$\textcolor{Emerald}{浅拷贝}$  把后面的赋值给前面的

##### array

- array有创建数组的构造函数

  ```javascript
         const arr = new Array(3,5)
         console.log(arr)
  ```

  > 依然建议使用字面量创建数组

- array的核心方法

  | 方法    | 作用     | 说明                   |
  | ------- | -------- | ---------------------- |
  | forEach | 遍历数组 | 不返回不改变值         |
  | filter  | 过滤数组 | 筛选并生成新的数组     |
  | map     | 迭代数组 | 返回一个处理过的新数组 |
  | reduce  | 累计器   | 返回函数累计处理的结果 |

  $\textcolor{Emerald}{reduce经常用于累加操作}$
  ```javascript
          const arr = [{
              name: '张三',
              salary: 10000
          }, {
              name: '李四',
              salary: 10000
          }, {
              name: '王五',
              salary: 10000
          },
          ]
  
          //prev是上一次迭代的返回值
          //item是每一项
          const a1 = arr.reduce((prev,item)=>{
              return prev += item.salary*0.3
              //0为prev的起始值
          },0)
  
          console.log(a1)
  ```

  forEach用来遍历数组

  ```javascript
          const arr = [10,20,30,40,50]
  
          arr.forEach(item =>{
              item += 10
              console.log(item)
          })
  ```

  $\textcolor{Emerald}{filter的功能是返回所有满足条件的元素}$

  ```javascript
        const arr = [10, 20, 30, 40, 50]
  
          //   返回符合条件01
          const arr1 = arr.filter((item) => {
              if (item < 30) {
                  return true
              }
          })
          console.log(arr1)
  
          //   返回符合条件02(简化)
          const arr3 = arr.filter((item) => {
              return item < 40
          })
          console.log(arr3)
  
          //   返回符合条件03(极简)
          const arr4 = arr.filter(item => item>=40)
          console.log(arr4)
  ```

  map常见于处理数组

  ```JavaScript
   document.querySelector('.list').innerHTML = goodsList.map(({ name, picture, price }) => {
        return `
        <div class="item">
        <img src="${picture}" alt="">
        <p class="name">${name}</p>
        <p class="price">${price}</p>
      </div>   
        `
      }).join('')
      // 拼接
  
  ```

- 数组的其他常用方法

  ```javascript
          //匹配第一个满足条件的元素
          console.log( [111,222,333,444].find(item =>  item %2 === 0))
          //匹配第一个满足条件的元素返回下标
          console.log( [111,222,333,444].findIndex(item =>  item %2 === 0))
          //判断是否所有的元素都满足条件
          console.log( [111,222,333,444].every(item =>  item %2 === 0))
          console.log( [1110,222,3330,444].every(item =>  item %2 === 0))
          //判断是否至少存在一个元素满足条件
          console.log( [111,222,333,444].some(item =>  item %2 === 0))
          console.log( [111,2221,333,4441].some(item =>  item %2 === 0))       
  ```

- 将伪数组转换为真数组的两种方法

  ```javascript
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <script>
          const divs = document.querySelectorAll('div')
          console.log(divs)
          //array.form
          const arr1 = Array.from(divs)
          console.log(arr1)
          //展开符转换
          const arr2 = [...divs]
          console.log(arr2)
      </script>
  ```

##### string

- 方法

  ```JavaScript
          //从下标1开始,裁剪两个
          console.log('abcdefgh'.substr(1,2))
          //从下标一裁剪到下标2,包左不包右
          console.log('abcdefgh'.substring(1,2))
          //匹配是否以'abc'开始
          console.log('abcdefgh'.startsWith('abc'))
          console.log('abcdefgh'.startsWith('bc'))
          //匹配是否以'fgh'结束
          console.log('abcdefgh'.endsWith('fgh'));
          console.log('abcdefgh'.endsWith('fg'))
          //替换
          console.log('abcdefgh'.replace('abc','哈哈哈'))
          console.log('abcdefgh'.match(/abc/))
          //从下标1开始,裁剪到3
          console.log('abcdefgh'.slice(1,3))
          //分隔字符串,标记为'/'
          console.log('ab/cde/f/gh'.split('/'))
          //检测是否包含'cd'
          console.log('abcdefgh'.includes('cd'))
          //转换为大写
          console.log('abcdefgh'.toUpperCase())
          //转换为小写
          console.log('AsdeFHHJki'.toLowerCase())
          //返回cd的下标
          console.log('abcdefgh'.indexOf('cd'))
  ```

##### number

- tofixed()设置保留小数的长度

  ```javascript
          console.log((0.1+0.2).toFixed(2))
          console.log((100).toFixed(2))
          console.log(0.1+0.2.toFixed(2))
          console.log(0.3300000004.toFixed(2))
  ```