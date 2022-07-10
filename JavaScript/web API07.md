#### 正则表达式

------

##### 介绍

- 正则表达式是用于匹配字符串中字符组合的模式,在JavaScript中,$\textcolor{Emerald}{ 正则表达式也是对象}$
- 常见应用场景:表单验证(匹配)过滤敏感词(替换)字符串中提取我们想要的部分(提取)

##### 语法

- 先定义正则表达式字面量,然后再用方法去匹配

- 语法

  ```javascript
    const str = 'Java'
     // 定义正则对象 
    const reg = /前端/
     // 正则对象里面 有一个 正则对象.test(要校验的字符串) 返回值 true|false 
     console.log(reg.test(str))
  ```

- exec()方法 在一个指定字符串中执行一个搜索匹配

  如果匹配成功,exec( )方法返回一个数组,否则返回null

- 元字符

  普通字符:大多数的字符仅能够描述他们本身,这些字符称作普通字符,例如所有的字母和数字,也就是说普通字符只能够匹配字符串中与他们相同的字符

  元字符是一些具有特殊含义的字符,可以极大的提高灵活性和强大的匹配功能

- 边界符

  | 边界符 | 说明               |
  | ------ | ------------------ |
  | ^      | 表示匹配行首的文本 |
  | $      | 表示匹配行尾的文本 |

  > 如果^和$在一起,表示必须是精确匹配

  ```javascript
      // /^字符串/
      console.log(/^我/.test('我很丑'))  // true
      console.log(/^我/.test('很丑我'))  //false
  
      // $ 表示 必须以 某个字符结尾
      console.log(/我$/.test('我是李云鹤'))  //false
      console.log(/我$/.test('是李云鹤我'))  //true
  
      // ^ $ 一起使用 表示 精确匹配
      console.log(/^哈哈$/.test('哈哈哈'))   //false
      console.log(/^哈哈$/.test('我哈哈哈'))  //false
      console.log(/^哈哈$/.test('哈哈'))  // true
  ```

- 量词(表示重复次数)

  | 量词  | 说明             |
  | ----- | ---------------- |
  | *     | 重复零次或更多次 |
  | +     | 重复一次或更多次 |
  | ?     | 重复零次或一次   |
  | {n}   | 重复n次          |
  | {n,}  | 重复n次或更多次  |
  | {n,m} | 重复n到m次       |

  > 逗号左右两侧千万不要出现空格

  ```javascript
      //  * 表示 0次或者更多次
      console.log(/^鹤*$/.test(''))
      console.log(/^鹤*$/.test('鹤'))
      console.log(/^鹤*$/.test('鹤鹤鹤鹤鹤鹤鹤鹤鹤鹤鹤鹤鹤鹤鹤鹤'))
      //  + 表示  >= 1
       console.log(/^鹤+$/.test(''));  //false
      console.log(/^鹤+$/.test('鹤'));
      console.log(/^鹤+$/.test('鹤鹤鹤鹤'));
      // ? 表示  0次或者1次
      console.log(/^磊?$/.test(''));
      console.log(/^磊?$/.test('磊'));
      console.log(/^磊?$/.test('磊磊'));  //false
  ```

- 字符类

  [ ]匹配的是字符集合

  ```javascript
      //  [字符] 表示 匹配 里面的一个字符即可 
      console.log(/^[abc]/.test('andy'))
      console.log(/^[abc]/.test('nady'))  //false
      console.log(/^[abc]/.test('baby'))
      console.log(/^[abc]/.test('city'))
      console.log(/^[abc]/.test('die'))  //false
      console.log(/^[abc]*$/.test('aa'))
      console.log(/^[abc]$/.test('a'))
  ```

  [] 中使用一个-连字符,表示的是范围

  ```javascript
    const reg = /^[a-zA-Z0-9_]{3,16}$/
    console.log(reg.test('a009'))
  ```

  [a-z]表示小写的a到z

  [A-Z]表示大写的A-Z

  [0-9]表示0-9

  ^表示取反

  ```javascript
      const reg = /[^a-z]/
      console.log(reg.test('a'))
  ```

  []里面加上^取反符号,表示匹配除了中括号里的字符之外的其他字符

  注意取反和开始符号非常相似不要搞混

  > .(点)匹配换行符之外的任何单个字符

- 预定义

  预定义指的是某些常见模式的简写方式

  | 预定类 | 说明                                            |
  | ------ | ----------------------------------------------- |
  | \d     | 匹配0-9之间的任一数字,相当于[0-9]               |
  | \D     | 匹配所有0-9以外的字符,相当于[ ^ 0-9]            |
  | \w     | 匹配任意的字母数字和下划线,相当于[ a-zA-Z0-9]   |
  | \W     | 匹配任意的字母数字和下划线,相当于[ ^ a-zA-Z0-9] |
  | \S     | 匹配非空字符                                    |

- 修饰符

  修饰符约束正则执行的某些细节行为,如是否区分大小写,是否支持多行匹配等

  ```javascript
      // 匹配 因为字母 a 
      // i ignore 不区分大小写
      const str = 'ABCD'
      const reg = /a/i
      console.log(reg.test(str))
  ```

  i表示匹配字母时不区分大小写

  ```javascript
    const reg = /hello/gi
  ```

  g表示全局,不仅找到一个,直到找到所有

  ```javascript
      const reg = /hello/gi
      const res = str.replace(reg, '你好')
  ```

  repalace表示替换

- 补充

  ```javascript
  classList.contains()
  ```

  表示查看有没有包含某个类,有则true,无则false

  ```javascript
   const reg = /哈哈|呵呵/
  ```

  筛查多个字符串

  

  

  

  

  



