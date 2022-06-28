#### 对象

------

##### what

- 对象是JavaScript里的一种数据类型
- 可以理解为一种无序的数据集合,注意数组是有序的数组集合
- 用来描述某个事物比如一个人

##### use

- 语法

  ```JavaScript
   // 创建对象  
  let dog = {
        // 属性名 可以加'' 或者 ""，可以省略， 
        uname: '淘淘',
        'color': 'yellow',
        // 方法名: 匿名函数
        play: function () {
          console.log('玩球')
        }
      }
  ```

- 对象由属性和方法组成 ,属性是特征,方法叫行为,他们之间没有顺序

- 对象是一种字面量,它是对象字面量

- 属性都是成对出现的,包括属性名和值,他们之间使用英文的冒号分隔

- 多个属性之间用逗号隔开

- 属性就是依附在对象上的变量,外面是变量,对象内是属性

- 属性名可以加上引号,一般情况下我们是省略这个符号的,除非遇到特殊符号比如空格,中横线等

##### 增删改查

- 查

  声明对象并添加了若干属性后,可以获取对象中属性对应的值,我们称之为属性访问,当然我们也支持查询整个对象

  ```JavaScript
      console.log(dog.uname)
      console.log(dog['age'])
      console.log(dog)
  ```

- 改

  本质上就是查询+赋予新值

  ```javascript
      dog.uname = '毛球'
      dog['age'] = 20
  ```

- 增加

  对象名.新属性=新值即可

  ```javascript
      dog.weight = 30
      dog['height'] = 35
  ```

- 删除

  delete 对象名.属性

  ```javascript
    delete dog.age
    delete dog['uname']
  ```

- 特别注意,点后面的属性名一定不要加引号,中括号里的属性名一定要加引号

- 属性和方法之间也存在覆盖，后面的会覆盖前面的

##### 对象中的方法

- 方法是由方法名和函数两部分构成的,他们之间使用英文的冒号分隔,多个属性之间用逗号分隔

- 方法名也可以使用引号单引号,但是我们一般不这么做,除非遇到特殊符号

- 方法是依附在对象中的函数,

- 对象中的方法是可以调用的,也可以进项传参等操作

- 语法

  ```javascript
    let obj = {
        uname: '吴彦祖',
        // 对象里边的方法 方法名: 匿名函数
        play: function (a) {
          console.log(a)
        },
        'eat-rose': function () {
          console.log('吃肉丝');
        }
      }
      // 调用对象的方法 对象名.方法名() 对象名['方法名']()
      obj.play('玩建筑')
      obj['eat-rose']()
  
      // 对象增加新的方法
      obj.drink = function () {
        console.log('喝威士忌')
      }
      console.log(obj);
  ```

##### 遍历对象

- 在遍历之前我们首先要搞明白一点,那就是对象里都是无序的键值对,没有规律,是没有下标的

- for-in循环

  for-in循环是一种非常适合用来遍历对象的循环,for in循环中的k是一个变量,在循环过程中依次代表对象的属性名,由于k是变量,所以必须使用[]语法解析

  一定记住,k是获得对象的属性名,对象名[k]是获得属性值

- 语法

  ```javascript
     for (let k in dog) {
        // k 就是对象里边的属性名
        console.log(k)
        // 对象名[k] 对象里边属性值
        console.log(dog[k])
      }
  ```

##### 内置对象

- 内置对象是JavaScript为我们准备好的内置对象,我们熟悉的console,docment都是内置对象

- 部分比较重要的math内置对象

  ```javascript
   // Math.PI  属性
      console.log(Math.PI);
      // Math.random() 方法 生成[0, 1) 生成大于等于0，小于1的随机数
      console.log(Math.random())
      // 天花板函数 向上取整
      console.log(Math.ceil(4.2)) // 5
      console.log(Math.ceil(-4.2)) // -4
      // 地板函数 向下取整
      console.log(Math.floor(4.2)) // 4
      console.log(Math.floor(-4.2)) // -5
      // 取整 parseInt() 保留整数，小数舍去
      console.log(parseInt(4.2)) // 4
      console.log(parseInt(-4.2)) // -4
      // 取最大值
      console.log(Math.max(12, 23, 4)) // 23
      // 取最小值
      console.log(Math.min(4, 23, 1)); // 1
      // 幂运算
      console.log(Math.pow(2, 3)); // 8
      // 绝对值
      console.log(Math.abs(-3)); // 3
      console.log(Math.abs(6)); // 6
  ```

- 生成n-m之间随机数的公式

  ```javascript
  Math.floor(Math.random() * (m - n + 1)) + n
  ```

#### 术语拓展

| 术语   | 解释                                  | 举例           |
| ------ | ------------------------------------- | -------------- |
| 关键字 | 在JavaScript中有特殊意义的词汇        | let,var        |
| 保留字 | 现在没有意义,但是往后可能有意义的词汇 | int,long,char  |
| 标识符 | 变量名函数名的另一种叫法              |                |
| 表达式 | 能产生值的代码,一般配合运算出现       | let age = 10+3 |
| 语句   | 一段可执行的代码                      | if()           |

#### 数据类型拓展

简单类型又叫做基本数据类型或者值类型,复杂类型又叫做引用类型,值类型在存储变量时存储的仅仅是地址,因此叫做值类型,引用复杂数据类型时,在存储时变量中存储的仅仅是地址,因此叫做引用数据类型