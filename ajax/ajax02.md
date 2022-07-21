#### form表单

------

##### 表单概述

- 在网页中，表单主要负责数据采集功能，它分为三个部分:表单标签,表单域,表单按钮

- 表单标签

  ```javascript
  <form>  </form>
  ```

- 表单域

  常见的表单域有input,textarea,select等

  > 表单域必须包含name属性,否则用户填写的信息无法被收集到

- 表单按钮

  触发提交操作或者是重置等操作

  > button  type = 'submit' 表示提交按钮的意思  type属性的默认值就是submit

- form标签的属性一览表

  | 属性    | 可选值                     | 说明                                                         |
  | ------- | -------------------------- | ------------------------------------------------------------ |
  | action  | url                        | 页面跳转/把表单中获得的数据,提交到哪个接口中/此属性为空会导致页面的刷新/#表示跳转至页面最顶端 |
  | method  | get/post                   | 数据交接的方式,默认值是get                                   |
  | enctype | application/multipart/text | 数据的编码格式,默认值是application                           |

  > 未来form表单用来收集数据，ajax负责发送这些数据

- 以get的当时提交表单数据

  ```javascript
      <form action="http://www.baidu.com" method="get" enctype="application/x-www-form-urlencoded">
          用户名:     <input type="text" name="username"> <br><br>
          密&emsp;码: <input type="text" name="password"> <br><br>
          <input type="submit"><br><br>
      </form>
  ```

  通过action属性指定提交的url地址,通过method属性指定提交的方式为get

  由于method属性的默认值是get,因此method="get"可以被省略

- 在form标签上,通过action属性指定提交的url地址,通过method属性指定提交的方式为post,并通过enctype属性指定数据的编码方式为 application/x-www-form-urlencoded

  ```javascript
      <form action="http://www.baidu.com" method="post" enctype="application/x-www-form-urlencoded">
          用户名:     <input type="text" name="username"> <br><br>
          密&emsp;码: <input type="text" name="password"> <br><br>
          <input type="submit"><br><br>
      </form>
  ```

  由于enctype的默认值就是application/x-www-form-urlencoded,所以enctype可以被省略

- enctype三个可选值之间的区别

  | 属性值                            | 是否常用 | 应用场景                                        |
  | --------------------------------- | -------- | ----------------------------------------------- |
  | application/x-www-form-urlencoded | 是       | 表单中不包含文件上传的场景,适用于普通数据的提交 |
  | multipart/form-data               | 是       | 表单中包含上传文件的场景                        |
  | text/plain                        | 否       | 无                                              |

  > 未来我们不会用form表单发送数据, 而是改为axios发送ajax

  > 未来form表单用来收集数据，ajax负责发送这些数据

- 通过ajax提交表单采集到的数据

  通过ajax提交表单采集到的数据,可以防止表单默认提交行为导致的页面跳转问题,提高用户的体验

  思路

  1. 监听表单的submit提交事件
  2. 阻止默认提交行为
  3. 基于axios发起请求
  4. 请求指定方式,请求地址
  5. 指定请求体数据

  ```javascript
          // 未来会用form表单收集数据，ajax发送请求;
          // 给form表单绑定submit提交事件，并阻止表单默认提交
          const form = document.querySelector('form');
          // 绑定提交事件
          form.addEventListener('submit', function (e) {
              // 阻止事件的默认行为 - 阻止默认提交
              e.preventDefault();
              // 发送ajax
              axios({
                  method: 'post',
                  url: 'http://www.liulongbin.top:3009/api/form',
                  // 查询参数用 params, 请求体参数用 data
                  data: {
                      username: document.querySelector('[name=username]').value,
                      password: document.querySelector('[name=password]').value,
                  }
              }).then(({ data: res }) => {
                  console.log(res);
              })
          })
  ```

- jQuery库简介(了解)

  $( 选择器 )   获取元素；  类似 document.querySelector() / querySelectorAll()

  $( 选择器 ) .on(事件，函数)；  绑定事件；    类似  addEventListener();

  $( 选择器 ) .show() ;  显示；  类似   div.style.display = “block”;

  $( 选择器 ) .hide();   隐藏；    类似   div.style.display = “none”;

- jQuery中的serialize()函数能一次性获取到表单中采集的数据

  ```javascript
          // window.onload 在jquery中 $();
          $(function () {
              // console.log(document.querySelectorAll('button'));
              // console.log($('button'));
              // 绑定事件
              $("#btn1").on('click', function () {
                  // 隐式迭代，链式编程;
                  $("li").show().html('天行健君子以自强不息，地势坤君子以厚德载物！');
              })
              $('#btn2').on('click', function () {
                  $("li").hide();
              })
          })
  ```

#### anxios请求方法的别名

------

##### 请求方法的别名

- get,post,put,patch,delete

- 为了简化,axious为所有支持的请求方法提供了别名:

  ```javascript
          let url = 'http://www.liulongbin.top:3009/api/getbooks';
          // 语法: axios.post(url, 配置)
          axios.get(url, {
              //  请求方式和资源路径不能修改，但是可以添加请求参数
              // 查询参数，只是众多属性之一
              params: {
                  id: 1
              }
          }).then(({data: res}) => {
              console.log(res);
          });
  ```

  ```javascript
          let url = 'http://www.liulongbin.top:3009/api/addbook';
          //   语法: axios.post(url, 参数, 配置)
          axios.post(url, {
              bookname: '三体黑暗森林',
              author: '刘慈欣',
              publisher: '武汉人民出版社'
          }, {
              // 第三个参数是配置ajax请求参数的，但是请求方式资源路径配置参数都不能改;
          }).then(({data: res}) => {
              console.log(res);
          });
  ```

- 全局配置请求根路径

  在url地址中,协议://域名:端口 对应的部分叫做"请求根路径"

  全局配置请求根路径的好处：提高项目的可维护性

  ```javascript
          axios.defaults.baseURL = 'http://www.liulongbin.top:3009';
  
          // 1.简写get
          axios.get('/api/getbooks').then(({data: res}) => {
              console.log(res);
          })
  
          // 2.简写post
          axios.post('/api/addbook').then(({data: res}) => {
              console.log(res);
          })
          
          // 3.完整写法
          axios({
              method: 'get',
              url: '/api/getbooks'
          }).then(({data: res}) => {
              console.log(res);
          })
  ```

#### axious拦截器

------

- 拦截器用来全局拦截axious的每一次请求与响应

- 好处:可以把每个请求中,某些重复性的业务代码封装到拦截器中,提高代码的复用性

- 实例

  ```javascript
  	<script>
  		// 请求拦截器 - 显示loadding效果
  		axios.interceptors.request.use(function (config) {
  			// config: 所有的ajax参数都在这参数中(method,url,params,data...)
  			console.log(config);
  			// 显示loadding效果
  			document.querySelector('.loading-box').style.display = 'block'
  			// 必须返回
  			return config;
  		}, function (error) {
  			// 固定语法 - 请求未能正常发送出去怎么处理
  			return Promise.reject(error);
  		});
  
  		// 响应拦截器 - 隐藏loadding效果
  		axios.interceptors.response.use(function (response) {
  			// 响应对象，里面有六个属性，最常用的是 data
  			console.log(response);
  			// 隐藏loadding效果
  			document.querySelector('.loading-box').style.display = 'none'
  			// 一定要返回 response
  			return response;
  		}, function (error) {
  			// 固定语法 - 请求未能正常发送出去怎么处理
  			return Promise.reject(error);
  		});
  		
  	</script>
  	<script>
  		// 配置请求根路径
  		axios.defaults.baseURL = 'http://www.liulongbin.top:3009'
  
  		// 点击按钮，发起 GET 请求
  		document.querySelector('#btnGET').addEventListener('click', function () {
  			axios.get('/api/get').then(function (res) {
  				console.log(res.data)
  			})
  		})
  
  		// 点击按钮，发起 POST 请求
  		document.querySelector('#btnPOST').addEventListener('click', function () {
  			axios.post('/api/post', { name: 'zs' }).then(function (res) {
  				console.log(res.data)
  			})
  		})
  
  		document.querySelector('#btnBooks').addEventListener('click', function () {
  			axios.get('/api/getbooks').then(function (res) {
  				console.log(res.data)
  			})
  		})
  	</script>
  ```

  