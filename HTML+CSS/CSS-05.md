#### 项目搭建注意点

##### 结构搭建

- 项目名使用英文(计算机无法解析中文)

- $\textcolor{Emerald}{样式与结构分离}$

  > images 图片文件夹  css样式文件夹  index首页

- 引入css文件

  ```css
  <link rel="stylesheet" href="./css/index.css" />
  ```

##### css样式初始化

```css
* {
    margin: 0;
    padding: 0;
    /* 自减盒子模型 */
    box-sizing: border-box;
}

ul {
    /* 清除默认圆点 */
    list-style: none;
}

a {
    /* 取消下划线 */
    text-decoration: none;
}

input,
button {
    /*去掉input的轮廓线*/
    outline: none;
    border: 0;
}

/* 左浮动 */
.fl {
    float: left;
}

/* 右浮动 */
.fr {
    float: right;
}

/* 清除浮动 */
.clearfix::after {
    content: '';
    /* 因为伪元素插入的标签属于行内元素,需要转换为块级 */
    display: block;
    clear: both;
    /* 兼容性的作用 */
    height: 0;
    visibility: hidden;
}

/* 兼容ie6 ie7 */
/*ie浏览器 */
.clearfix {
    *zoom: 1;
}

/*body页面背景色*/
body {
    background-color: #f3f5f7;
}
```

##### 分析页面布局

- 确定版心(可视区)
- 分析模块时的原则是$\textcolor{Emerald}{先行后列(需要确定列的大小),先上后下,从外到内}$
- 先有结构后有样式

##### 版心常见样式为

```css
.container{
    width: 1200px;
    margin: 0 auto;
}
```

> 版心固定命名为container
>
> 给出可视区的宽度,完成后续所有居中的工作

#### 顶部布局

##### header布局

一般给高度以及上下的magin即可

```css
.header {
    height: 42px;
    margin: 30px auto;
}
```

##### logo布局

> logo里面首先放一个h1标签,目的是提取,告诉搜索引擎这个部分非常重要
>
> h1里面再放一个a链接,用于返回首页,logo的背景图片加给a链接
>
> 为了方便搜索引擎收录,我们的链接里要放上网站的名称(可以中文),隐藏文字
>
> 方法一:font-size:0  京东
>
> 方法二:text-indent: -9999px;overflow:hidden   淘宝

```html
     <div class="logo fl">
            <h1>
                <a href="#">您的工程名字</a>
            </h1>
        </div>
```

```css
/*大小写在总的logo盒子上*/
.logo {
    width: 195px;
    height: 42px;
}

.logo h1 {
    width: 100%;
    height: 100%;
}
/*装饰都加在a标签上*/
.logo h1 a {
    display: block;
    width: 195px;
    height: 42px;
    background: url(../images/logo.png);
    font-size: 0;
}
```

- 顶部导航布局

  > li是块级元素,为了让他们一行显示,需要给li加浮动
  >
  > 不需要给nav加宽度,方便后续添加文字
  >
  > 每个li的宽度也不一定固定,所以给链接a左右padding撑开盒子
  >
  > margin给外层,padding给内层

  ```html
  <!-- 导航的常见格式-->
  <div class="nav">
              <ul>
                  <li><a href="#">01</a></li>
                  <li><a href="#">02</a></li>
                  <li><a href="#">03</a></li>
          </ul>
  </div>
  ```

- search常见的布局

  ```html
  <!-- 搜索框的常见格式--> 
  <div class="search ">
              <input type="text" placeholder="输入关键词">
              <button></button>
  </div>
  ```

  > input与button需要进行浮动,因为都是行内块元素,中间会有空隙
  >
  > search盒子里面需要单独的包含input表单和button按钮

- 用户user布局

  ```html
  <!-- 图片和id对齐经典应用场景-->
  <div class="user ">
              <img src="./images/user.png" alt="">
              <span>您的名字</span>
  </div>
  ```

  ```css
  /* 图片与文字垂直居中对齐 */
  .user img {
      vertical-align: middle;
  }
  ```

#### banner(轮播)常见布局

> 首先要有一个通栏的大盒子,给高度以及背景颜色

```css
.banner {
    height: 420px;
    background-color: #1c036c;
}

.banner .wrapper {
    height: 420px;
    background-color: pink;
    background: url(../images/banner2.png);
}
```

> 通栏里面套上版心,版心里面分出列

```html
<div class="aside">
               <ul>
                   <li><a href="#">01</a></li>
                   <li><a href="#">02</a></li>
                   <li><a href="#">03</a></li>
                   <li><a href="#">04</a></li>
                   <li><a href="#">05</a></li>
                   <li><a href="#">06</a></li>
                   <li><a href="#">07</a></li>
                   <li><a href="#">08</a></li>
                   <li><a href="#">09</a></li>
               </ul>
</div>
```

> 使用标签的时候尽可能的使用语义化的表达