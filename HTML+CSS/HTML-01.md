#### 基础认知

------

##### 基础概念铺垫

- 前端的代码是通过浏览器(渲染引擎)转化(解析和渲染)成用户看到的网页的

  补充知识:搜索引擎的简称是SEO

- 五大浏览器以及渲染内核:

  | 浏览器名称                         | 内核                          | 备注                                       |
  | ---------------------------------- | ----------------------------- | ------------------------------------------ |
  | 火狐-firefox                       | GECKO                         |                                            |
  | $\textcolor{Emerald}{谷歌-Chrome}$ | $\textcolor{Emerald}{BLINK}$  | $\textcolor{Emerald}{BLINK为webkit的分支}$ |
  | IE                                 | TRIDENT                       | 已经开始升级为edge                         |
  | $\textcolor{Emerald}{Safari}$      | $\textcolor{Emerald}{WEBKIT}$ | $\textcolor{Emerald}{多见于MAC}$           |
  | opera                              | BLINK                         |                                            |


  > 渲染引擎不同性能速度效果都会受影响

- web标准的目的:让展示的效果统一

  三个构成部分:
  
  ![1653041655546.png](https://s1.imagehub.cc/images/2022/05/26/1653041655546.png)

 


##### HTML先导

- html:超文本标记语言

- html通过==标签==来对页面内容进行描述

- $\textcolor{red}{html的骨架结构}​$

  ```html
  <!DOCTYPE html>
  <!--这里是根标签-->
  <html lang="en">
  <!--这里是网页的头部-->
  <head>
      <meta charset="UTF-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <!--这里是网页的标题-->
      <title>Document</title>
  </head>
  <!--这里是网页的主体-->
  <body>
      
  </body>
  </html>
  ```

  $\textcolor{Emerald}{快捷创建骨架代码的两种方式: !+tab或者html:5}$

- vscode部分基础快捷键

  | 功能         | 按键                                   |
  | ------------ | -------------------------------------- |
  | 创建框架     | $\textcolor{Emerald}{!+tab或者html:5}$ |
  | 保存         | ctrl+s                                 |
  | 注释         | ctrl  +/                               |
  | 查看网页效果 | alt+b                                  |

  

##### 语法规范

- 注释标签:`<!-- 这里是内容 -->`

- 标签

 [![1653043555080.md.png](https://s1.imagehub.cc/images/2022/05/26/1653043555080.md.png)](https://www.imagehub.cc/image/GPZ49O)
 
- 属性记录在开始标签里,同时可以存在多个属性,属性名和标签名之间以空格分隔,不分前后顺序

  ```html
  <body class="one" id="two">
  ```

- 标签与标签之间的关系有$\textcolor{Emerald}{嵌套(父子)以及并列(兄弟)}$

  

#### HTML标签

------

##### 排版标签

- 标题标签-双:==<h1~6>== 由大到小

  特点:加粗;数字越小字体越大;独占一行

  数字为几就是几级标题

- 段落标签-双:==< p >== 适用于分段显示

  特点:段落之间存在间隙/独占一行/页面宽度不够时会自动换行

- 换行标签-$\textcolor{red}{单}$:==< br >==用来换行

- 水平线标签-单: < hr >

##### 文本格式化标签

- 场景:需要简单修饰文本时

  注意点:记语义化标签,增强自己代码的可读性

  | 效果          | 代码                                  |
  | ------------- | ------------------------------------- |
  | ~~删除线~~    | $\textcolor{Emerald}{del}$  or  s     |
  | *倾斜*        | $\textcolor{Emerald}{em}$   or  i     |
  | **加粗**      | $\textcolor{Emerald}{strong}$   or  b |
  | <u>下划线</u> | $\textcolor{Emerald}{ins}$   or  u    |

##### 媒体标签

- 图片标签-单标签

  ```html
  <img src="" alt="" title="">
  ```

  > src:目标图片的路径
  >
  > alt:图片的替换文本(当图片加载失败时才会显示的文本)
  >
  > title:相当于注释(悬停时出现的那个小方框)
  >
  > width&height:宽和高(一般写在css里)

  $\textcolor{Emerald}{width和height的值一般给一个就可以了,两个都给容易拉伸图片}$

- $\textcolor{red}{路径}​$

  绝对路径: eg:https://www.baidu.com/ (协议开头)

  ​                      C:\Users\野生苏苏\Desktop\预科班(盘符开头)

  相对路径:eg:   src="../../../image1/image2/image3/a.jpg" 

  $\textcolor{Emerald}{./或者直接写名字}$表示同级路径   $\textcolor{Emerald}{imges(文件夹名)/}$表示下级   $\textcolor{Emerald}{ ../}$表示上级

- 音频标签

  ```html
     <audio src="./03.mp3" controls loop muted autoplay></audio>
  ```

  > src:音频的路径
  >
  > controls:显示播放的控件
  >
  > autoplay:自动播放(受浏览器影响,时常bug)
  >
  > loop:循环播放
  >
  > 最好采用MP3的格式(这个格式有最好的支持率)

- 视频标签

  ```html
  <video src="./video.mp4" loop muted controls></video>
  ```

  > src:视频的路径
  >
  > controls:显示播放的控件
  >
  > autoplay:自动播放(受浏览器影响,时常bug)
  >
  > loop:循环播放
  >
  > muted:静音播放
  >
  > 最好采用MP4的格式(这个格式有最好的支持率)

- $\textcolor{erd}{链接标签}$

  场景:点击之后,从一个页面跳转到另一个页面,网页以及html页面均可

  称呼: a标签,超链接,锚链接

  特点:a标签显示为蓝色和紫色(点击和点击之后)/a标签有下划线

  ```html
  <a href="" target=""></a>
  ```

  > href属性告诉a链接目标网页的路径,网络连接内部链接均可
  >
  > target属性告诉浏览器以何种方式打开新网页:
  >
  > _ self(默认):覆盖原页面==_ blank:新建窗口(保留原页面)==

  $\textcolor{red}{空链接:在href属性里加上}$**#**$\textcolor{red}{,否则点这个链接就会刷新一次界面}$

  $\textcolor{red}{图片标签:在a标签里嵌套一个img}$

  ```html
   <a href="https://www.baidu.com/"><img src="./01.jpg" ></a>
  ```

  



