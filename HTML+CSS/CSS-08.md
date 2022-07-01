#### 项目结构搭建

##### 文件和目录准备

- 模块化开发,结构样式相分离

- 实际开发中,项目文件夹不建议使用中文,推荐命名为$\textcolor{Emerald}{xtx(项目名缩写)-pc-client}$

- 复制$\textcolor{Emerald}{favicon.ico}$到根目录里

- 创建图片文件夹

  | 文件夹                    | 功能                                |
  | ------------------------- | ----------------------------------- |
  | $\textcolor{red}{images}$ | 存放固定使用的图片,比如logo和精灵图 |
  | $\textcolor{red}{upload}$ | 存放非固定使用的图片素材            |

- 新建index.html文件夹

- $\textcolor{red}{base.css}$基础公共样式

  $\textcolor{red}{common.css}$网站中多个网页相同模块的重复样式

  $\textcolor{red}{index.css}$首页样式

  

##### SEO三大标签

- 语法

  ```css
     <!--网页标题-->
    <title>您的标题</title>
      <!--网页描述-->
    <meta name="description" content="您的描述">
       <!--网页关键词-->
    <meta name="keywords" content="您的关键词">
       <!--网页ico图标-->
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
       <!--网页初始化样式-->
    <link rel="stylesheet" href="./css/base.css">
       <!--网页头部 尾部公共样式-->
    <link rel="stylesheet" href="./css/common.css">
       <!--网页首页样式-->
    <link rel="stylesheet" href="./css/index.css">
  ```

##### 精灵图

- $\textcolor{red}{精灵图使用步骤:}$

  1. 创建一个盒子

  2. 设置盒子大小为小图片大小

  3. 设置精灵图为盒子的背景图片

  4. 将小图片左上角坐标 取负值，设置给盒子的background-position：x y

     > 精灵图的坐标基本都是负值

##### logo盒子结构

- $\textcolor{red}{logo盒子结构}​$
  1. logo 里面首先放一个 h1 标签，目的是为了提权，告诉搜索引擎，这个地方很重要。
  2. h1 里面再放一个链接，可以返回首页的，把 logo 的背景图片给链接即可。
  3. 为了搜索引擎收录我们，我们链接里面要放文字（网站名称），但是文字不要显示出来。

##### 底部导航结构

- 语法

  ```html
     <section class="xtx-service">
        <div class="container">
          <a href="#">01</a>
          <a href="#">02</a>
          <a href="#">03</a>
        </div>
      </section>
  ```

  > 底部通常是盒子包a



##### 轮播图

- 轮播大块

  ```html
   <div class="xtx-entry">
      <div class="container">
          <!-- 焦点图 -->
           <ul class="banner">
            <li><a href="#"><img src="./uploads/banner_1.png" alt=""></a></li>
          </ul>
       </div>
  </div>
  ```

  > ul包li的方式方便加轮播图

- 轮播图指示器

  ```html
  <ol class="indicator">
          <li></li>
          <li></li>
          <li class="active"></li>
          <li></li>
          <li></li>
        </ol>
  ```

  > 后期结合js来使用此模块的内容

