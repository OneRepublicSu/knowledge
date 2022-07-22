#### 定位

##### 定位的基本介绍

- 元素的层级关系:标准流<浮动<定位<层级
- 一般用于盒子的堆叠层叠状况,也可以让盒子始终固定在屏幕中的某个位置
- 定位之间的层级相同,想要让某个元素置于最顶层用z-index(数字越大,层级越高)

##### 四种定位

- 四种定位(position)

  | 取值                            | 含义 | 备注                                |
  | ------------------------------- | ---- | ----------------------------------- |
  | static                          | 静态 | 不常用                              |
  | $\textcolor{Emerald}{relative}$ | 相对 | $\textcolor{Emerald}{子 绝 父  相}$ |
  | $\textcolor{Emerald}{absolute}$ | 绝对 | $\textcolor{Emerald}{子 绝 父  相}$ |
  | $\textcolor{red}{fixed}$        | 固定 | $\textcolor{red}{导航常用}$         |

  > 设值时水平垂直的只要各就近取一个就够了

- static:标准流

- relative:相对自身之前的位置进行移动,占位置未脱离标准流

  使用于小范围的移动或者子绝父相

- absolute:当祖先元素中没有定位时,默认相对于浏览器进行移动,当祖先元素中有定位的时候,相对于离得最近的祖先元素进行移动

  > 脱离标准流,不占位置

##### 子绝父相

- 含义:$\textcolor{red}{子元素采用绝对定位,父元素采用相对定位}$

- 应用场景:让子元素相对于父元素进行自由移动

- 好处:父元素是相对定位,对网页布局影响最小

- 子绝父相情况下的元素居中

  ```css
    .father{
              width: 400px;
              height: 400px;
              /*父元素相对定位*/
              position: relative;
              /*父元素居中*/
              margin: 0 auto;
          }
          .son{
              width: 100px;
              height: 100px;
              /*子元素绝对定位*/
              position: absolute;
               /*移动父元素的百分之五十*/
              left: 50%;
              top: 50%;
              /*移动自己的百分之五十*/
              transform: translate(-50%, -50%);      
          }
  ```

##### 固定定位

- 代码

  ```css
   position: fixed;
  ```

- 固定定位始终是相对于浏览器窗口进行定位和移动的,可以让盒子固定在屏幕中的某个特定位置

- 脱离标准流

#### 装饰

##### 基线对齐

- 代码

  ```css
   vertical-align: middle;
  ```

- 可以解决的问题

  | 场景                                                   |
  | ------------------------------------------------------ |
  | 解决行内元素和行内块元素的垂直对齐问题                 |
  | div中的文本框无法贴顶的问题                            |
  | div不设宽度由img撑开,img标签下会存在间隙问题           |
  | 配合父元素的$\textcolor{Emerald}{行高}$,让图片垂直居中 |

##### 光标类型

- 代码

  ```css
  cursor: pointer;
  ```

  > default默认值/pointer小手效果/text工字型/move十字光标

- 作用:设置鼠标光标在元素上时显示的样式

##### 边框圆角

- 场景:让四个角变得圆润,增加页面细节,提升用户体验

- 属性名:border-radius

- 常见取值:数字+px,百分比

  > 从左上角开始赋值,顺时针进行,没有赋值的看对角

- 有趣应用:画正圆(盒子必须是正方形,设置边框圆角为盒子宽高的一半)

  胶囊形:盒子必须是长方形,赋值时设置盒子高度的一半

##### 溢出隐藏

- 代码

  ```css
   overflow: hidden;
   /*根据是否溢出自动显示或者隐藏滚动条*/
   overflow: auto; 
  ```

##### 元素本身隐藏

> 通过visbility:hidden和display以及opacity

- 方法一

  ```css
  visibility: hidden;
  ```

  此方法未脱离标准流,占位置

- 方法二

  ```css
     display:none;
     display: block;
  ```

  两行代码配合使用,脱离标准流,不占位置

- 方法三

  ```css
    opacity: 0;
    opacity: 1;
  ```

  opacity可以改变整个组的透明度,未脱离标准流,占位置

##### 边框合并

- 代码

  ```css
  table,
  tr,
  td{
      border-collapse: collapse;
  }
  ```

  > 此效果可以让边框的表格合并

##### 三角形(拓展)

- 用css画三角形的步骤

  > 01设置一个盒子
  >
  > 02设置四周不同颜色的边框
  >
  > 03将盒子的宽高设置为0,仅保留边框
  >
  > 04得到四个三角形,选择其中一个后,其他三角形的颜色设置为透明

  ```css
    div{
              width: 0px;
              height: 0px;
              border-top: 20px solid transparent;
              border-right:20px solid transparent;
              border-left: 20px solid transparent;
              border-bottom: 20px solid pink;
  
          }
  ```

  注意:其他三条边框一定要保留,不然三角形就会塌陷

#### 选择器扩展

##### 链接伪类选择器

- 常用于选中超链接的不同状态

  | 选择器语法 | 功能               |
  | ---------- | ------------------ |
  | a:link     | 选中未访问过的状态 |
  | a:visited  | 选中访问之后的状态 |
  | a:hover    | 选中鼠标悬停的状态 |
  | a:active   | 选中鼠标按下的状态 |

  > 顺序速记$\textcolor{Emerald}{lv好啊}$

##### 焦点伪类选择器

- 场景:用于选中元素获取焦点时的状态,常用于表单控件

- 选择器语法:

  ```css
       input{
              outline: none;
          }
          input:focus{
              border: 1px solid cornflowerblue;
              color: aquamarine;
          }
  ```

  表单控件获取焦点时默认会显示外部轮廓线

##### 属性选择器

- 场景：用于选中具有某种属性的元素

- 语法：

  ```css
   input[type=text]{
              width: 400px;
              height: 400px;
          }
          div[class]{
              color: red;
          }
  ```

  