#### 文件上传

------

##### formdata

- formdata是浏览器提供的一个webAPI,它以键值对的方式存储数据
- formdata配合ajax技术,能够向服务器发送multipart/form-data格式的请求体数据
- formdata+ajax技术实现文件上传的功能
- ajax实现文件上传的时候,请求体的编码格式必须是 multipart/form-data

##### formdata的基本用法

- formdata是一个构造函数,new formdata( ) 即可得到formdata对象

  const id = new FormData( )

- 调用FormData对象的append(键,值)方法,可以向空白的formdata中追加键值对数据,其中:

  1. 键表示数据项的名字,必须是字符串
  2. 值表示数据项的值,可以是任意类型的数据

- 实例

  ```JavaScript
              let fd1 = new FormData(form);
              // 展开运算符可以查看所有可遍历对象;
              console.log(...fd1);
  ```

  ```javascript
              let fd2 = new FormData();
              // 利用 append() 向FormData添加数据
              fd2.append('name', '罗渽民');
              fd2.append('age', 18);
  ```

#### XMLHttpRequest

------

##### 基础概念

- 是浏览器内置的一个构造函数

- 基于new出来的XMLHttpRequest实例对象,可以发起ajax的请求

  axios中的基础方法都是基于XMLHttpRequest封装出来的

- 发起ajax请求的核心对象是XMLHttpRequest

##### 数据交换格式

- 数据交换格式就是服务器端与客户端之间数据传输的格式
- 两种数据交换格式:XML(少用)/JSON( 主流 )

##### JSON

- json全程JavaScript object notation 是一种数据交换格式,他本质上是用字符串的方式来表示对象或数组类型的数据
- 