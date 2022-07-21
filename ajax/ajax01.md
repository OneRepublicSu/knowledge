#### 服务相关的基础概念

------

##### 服务器

- 服务器是提供服务的设备

- 服务器专门负责存放资源和对提供服务

- 常见的五大客户端浏览器:chrome/Firefox/edge/Safari/Opera

- 网络上的资源保存在服务器上,我们在访问服务器上的资源时,需要知道资源的确切存放地址

- $\textcolor{Emerald}{url}$就是用来表示服务器上每个资源的确切访问路径的

  ![1658025779311](C:\Users\野生苏苏\AppData\Roaming\Typora\typora-user-images\1658025779311.png)

  $\textcolor{Emerald}{协议}$:网络协议的简称,用来保证通信的双方能够读懂彼此发过来的消息内容

  $\textcolor{Emerald}{主机名}$:用来标识互联网中服务器的唯一性

  $\textcolor{Emerald}{端口号}$:0-65535之间的整数,主要作用是表示一台计算器中特定进程所提供的的服务/ 80端口可以省略不写(有且仅有80可以)

##### 客户端和服务器通信的过程

- 客户端和服务器之间的通信过程,分为请求-响应两个步骤
- $\textcolor{red}{请求}$:客户端通过网络去找服务器要资源的过程叫做请求
- $\textcolor{red}{响应}$:服务器把资源通过网络发送给客户端的过程,叫做响应
- 服务器对外提供的资源一般包括:文字/图片/音乐/视频/$\textcolor{red}{数据}$

#### ajax的基础用法

------

#####  基础知识

- ajax是浏览器中的技术:用来实现客户端网页请求服务器的数据

  全程 Asynchronous Javascript And XML (xml可扩展标记语言)

- 地址栏/form/a/location.href都是同步发送请求,在执行的时候会进行刷新操作

- ajax作为异步,并不会刷新整个页面,可以比较方便的操作页面中的某个部分

- 使用ajax请求数据的5种方式

  |      | 方式   | 描述                |
  | ---- | ------ | ------------------- |
  | 1    | GET    | 从服务器获取        |
  | 2    | POST   | 向服务器新增        |
  | 3    | DELETE | 删除                |
  | 4    | PUT    | 更新-侧重于完整更新 |
  | 5    | PATCH  | 更新-侧重于部分更新 |

##### axios

- 是一个专注于数据请求的库

- http://www.axios-js.com/

- 用axious获取数据的案例

  ```javascript
      <!-- 这是一个库,所以在使用之前必须先引入 -->
      <script src="./lib/axios.min.js"></script>
      <script>
          // 点击按钮发送
          document.querySelector('button').addEventListener('click',function(){
              // 发送ajax - 要配置的参数比较多,所以我们的参数是对象类型
              axios({
                  method:'get',
              url:'http://www.liulongbin.top:3009/api/getbooks'
              }).then(res =>{
                 //res里面有六个属性,未来我们基本上只会用到data属性  
                  //在axios里面我们基本只使用箭头函数
                  console.log(res.data)
              })
          })
  ```

##### get请求(获取信息)

- 实例

  ```javascript
      <script src="./lib/axios.min.js"></script>
      <script>
          axios({
              method:'get',
             url:'http://www.liulongbin.top:3009/api/getbooks' 
          }).then( function(res){
              console.log(res.data)
          })
      </script>
  ```

- 如果想指定查询条件,可以通过$\textcolor{Emerald}{  params }$选项来制定查询的参数

  ```javascript
      <script>
          axios({
              method:'get',
             url:'http://www.liulongbin.top:3009/api/getbooks' ,
             params:{
              id : 2,
              bookname :'红楼梦'
             }
          }).then( function(res){
              console.log(res.data)
          })
      </script>
  ```

- 查询参数的本质

  在使用ajax中的get请求时，data中的参数会以？键=值 的形式拼接到url地址的末尾

  ```javascript
      <script src="./lib/axios.min.js"></script>
      <script>
          axios({
              method:'get',
             url:'http://www.liulongbin.top:3009/api/getbooks?author=曹雪芹' ,
       
          }).then( function(res){
              console.log(res.data)
          })
      </script>
  ```

- 在url中不允许出现中文，空格等特殊字符，因此浏览器会自动对url地址内的中文进行转换处理，浏览器内置了方法，用来实现url的编码和解码处理

- axios的结构

  ```javascript
      <script src="./lib/axios.min.js"></script>
      <script>
          axios({
              method: 'get',
              url: 'http://www.liulongbin.top:3009/api/getbooks?author=曹雪芹',
  
          }).then(function ({data:res}) {
              console.log(res.code)
              console.log(res.msg)
              console.log(res.data)
  
          })
      </script>
  ```

  > 服务器端响应给axious的原始数据,被axious在外面套了一层壳,解构时一定要小心这一点

- 接口里的一些信息

  | 组成部分 | 说明                                      |
  | -------- | ----------------------------------------- |
  | 名称     | 接口的名称                                |
  | 接口url  | 客户端发起ajax调用此接口时,请求的url地址  |
  | 请求方式 | 如:get,post,put,delete等                  |
  | 请求参数 | 请求时,需要发送到服务器的查询参数或请求体 |

##### post数据(添加)

- 实例

  ```javascript
      <script src="./lib/axios.min.js"></script>
      <script>
          axios({
              method:'get',
             url:'http://www.liulongbin.top:3009/api/getbooks' 
          }).then( function(res){
              console.log(res.data)
          })
      </script>
  ```

- get和post的区别

  get请求只能在url中携带少量的数据

  post请求适合用来提交大量的数据

#### 请求报文以及响应报文

------

##### 基础知识

- 请求报文规定了客户端以什么格式把数据发送给服务器

- 响应报文规定了服务器以什么格式把数据响应给客户端

- 请求报文由请求行,请求头部,空行和请求体4个部分组成 

- 在浏览器中,get和delete比较特殊,他们几乎不设置请求体参数

- 响应报文由状态行,响应头部,空行和响应体4个部分组成

- 响应状态码由三位数字组成,用来表示响应成功与否的状态,客户端可以根据响应状态码判断出这次http请求是成功还是失败了

  | 状态码 | 描述                  | 说明                                          |
  | ------ | --------------------- | --------------------------------------------- |
  | 200    | ok                    | 请求成功                                      |
  | 201    | created               | 资源在服务器已经成功创建                      |
  | 304    | not modified          | 响应体中不包含任何资源内容                    |
  | 400    | bad request           | 客户端的请求或者参数有误导致失败              |
  | 401    | unauthorized          | 客户端用户身份未通过导致失败                  |
  | 404    | not found             | 客户请求的资源地址错误,导致服务器无法找到资源 |
  | 500    | internal server error | 服务器内部错误导致本次请求失败                |

- 业务状态码多数写在响应体里面,是写给编写程序人员的开发人员看的

  响应状态码被放在状态行里,是给浏览器辨别使用的

- 响应状态码只能表示这次请求的成功与否（成功地失败了）
  业务状态码用来表示这次业务处理的成功与否

- 响应状态码是由 http 协议规定的，具有通用性。每个不同的状态码都有其标准的含义，不能乱用。
  业务状态码是后端程序员自定义的,不具有通用性

#### 接口相关的基础概念

------
- 使用ajax请求数据的时候,被请求的url地址,就叫做数据接口(也叫API)
- 同时每个接口必须有对应的请求方式

