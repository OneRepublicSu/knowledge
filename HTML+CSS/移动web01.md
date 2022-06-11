##### 字体图标

- 字体图标展示的是图标,但是本质是字体

- 优点:灵活/轻量级/兼容性强/使用方便/$\textcolor{Emerald}{适用于单色图标}$

- 常用图标库:

  ```
  iconfont:https://www.iconfont.cn/
  ```

- iconfont引入方法:

  从路径上分可以分为:绝对路径和相对路径

  先引入css样式表,绝对路径在资料文档中复制(需要自己添加http://),本地的css样式在下载下来的本地文件中找,命名为:iconfont.css

  > $\textcolor{Emerald}{很多情况下我们并不推荐使用本地字体图标,在线更稳定并且易于更新和维护}$

- ###### 引入方法

  > 类名调用法

  ```html
   <span class="iconfont icon-right"></span>
  ```

  使用类名调用时标签必须有两个类名:iconfont,icon-xxx

  > Unicode调用法

  ```html
   <span class="iconfont">&#xe8ab;</span>
  ```

  用标签将图标字符包起来,依然需要引用通用类iconfont

  > 伪元素使用法

  ```css
    .box::before{
              content: '\e665';
          }
  ```

  取值在css里寻找

##### 平面转换

- 平面转换语法:transform

- 用transform实现元素位移效果:

  ```css
   transform: translate(x,y);
  ```

  > $\textcolor{red}{注意x轴的正方向为右,y轴的正方向朝下}$
  >
  > $\textcolor{Emerald}{如果只出现一个值,默认为x轴的方向}​$

- ###### 小拓展:使用translate进行元素居中效果

  ```css
         .father{
              position: relative;
              width: 500px;
              height: 500px;
          }
          .son{
              position: absolute;
              left: 50%;
              top: 50%;
              width: 200px;
              height: 200px;
              transform: translate(-50%,-50%);
          }
  
  ```

  > 原理:先用position移动父元素的百分之五十,然后再用transform移动自己的百分之五十就可以达到比较完美的垂直水平居中

- 用transform实现元素旋转效果:

  ```css
  transform: rotate(360deg);
  ```

  > 360deg=1turn

- 用transform-origin属性改变旋转原点:

  ```css
  transform-origin: center center;
  ```

  > 第一个值为水平值,第二个值为垂直值
  >
  > 方位名词用left/top/right/bottom/center,取值也可以用像素值和百分比

- 想要同时实现多种效果,$\textcolor{Emerald}{需要使用transform的复合值,避免被层叠性覆盖}$

- 使用transform实现元素缩放效果:

  ```scss
  transform: scale(3);
  ```

- 多行文字超过显示省略号:

  ```css
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
  overflow: hidden;
  ```

##### 渐变

- 使用backg-image属性实现渐变背景效果

  > 渐变一般用于设置盒子的背景
  >
  > 第一个属性是方向,第二个属性是颜色从哪里向哪里变化

  ```css
  background-image: linear-gradient(to bottom,red,green,);
  ```

  

