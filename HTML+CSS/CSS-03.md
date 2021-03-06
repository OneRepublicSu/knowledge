#### CSS三大特性

##### 优先级(继承性and层叠性)

- 特性:不同的选择器具有不同的优先级,优先级高的样式会覆盖优先级低的.

- 优先级公式:继承<通配符选择器<标签选择器<类选择器<id选择器<行内样式<!important

  > !important写在属性值的后面,分号的前面
  >
  > !improtant不能提升继承的优先级,只要是继承优先级就是最低的
  >
  > $\textcolor{Emerald}{实际开发中不建议使用!improtant}$

- 权重的叠加计算

  如果是复合选择器,此时需要通过权重叠加计算的方法,判断最终哪个选择器优先级最高会生效
  $$
  (0,0,0,0)
  $$

  > 依次是:行内样式的个数/id选择器的个数/类选择器的个数/标签选择器的个数
  >
  > $\textcolor{red}{两个选择器的优先级相同则比较层叠性,谁写在下面,谁离目标元素更近,谁就是最后显现的效果}$

- 综上所述,我们需要尽量避免多个选择器同时选中一个标签的情况

##### Chrome调试工具和pxcook的基本使用

- 情况如下

  | 情况                                        | 原因                       |
  | ------------------------------------------- | -------------------------- |
  | $\textcolor{Emerald}{没有看到自己的选择器}$ | 选择器的单词拼错           |
  | (没生效)                                    | 选择器的结构错了           |
  | $\textcolor{Emerald}{出现了报错}$           | 属性值后面没有分号         |
  | (出现了小三角)                              | 出现了中文标点             |
  |                                             | 属性名或者属性值的单词拼错 |

##### 盒子模型

###### 基础

- 浏览器在渲染页面的时候会将网页中的元素看成一个个矩形的区域,我们就称之为盒子
- css中规定,盒子由:content内容区,内边距padding,边框区域border,外边距区域margin构成,这就是盒子模型

###### 内容区的宽度和高度

- 利用width和height可以设置盒子内容区域的大小

###### 边框

- border给边框设置粗细样式和颜色效果等值

- 属性包括

  | 作用                        | 属性名       | 属性值                          |
  | --------------------------- | ------------ | ------------------------------- |
  | 粗细                        | border-width | 数字+px                         |
  | $\textcolor{Emerald}{样式}$ | border-style | 实线solid,虚线dashed,点线dotted |
  | 颜色                        | border-color | 颜色取值                        |

- 连写:$\textcolor{Emerald}{border:粗细 实线 颜色;(值需要选全),样式是必填选项}$

- 单方向设置的话就是border-方位词

###### 内边距

- 边框与内容区域之间的距离

- 属性名:padding

  | 取值 | 示例                          | 含义                                        |
  | ---- | ----------------------------- | ------------------------------------------- |
  | 1    | padding:10px;                 | 上下左右都是10                              |
  | 2    | padding:10px 20px ;           | 上下是10,左右是20                           |
  | 3    | padding:10px 20px  30px;      | 上是10,左右是20,下是30                      |
  | 4    | padding:10px 20px  30px 40px; | 上设置为10,右设置为20,下设置为30,左设置为40 |

- 单方向设置内边距

  padding-方位名词  属性值-数字+px

- $\textcolor{Emerald}{盒子的宽度=左边框+左内边距+内容宽度+右内边距+右边框}$

  $\textcolor{Emerald}{盒子的高度=上边框+上内边距+内容高度+下内边距+下边框}$

- 不会撑大盒子的特殊情况:

  如果盒子没有设置宽度,此时宽度默认是父盒子的宽度

  此时给子盒子设置左右的padding或者左右的border,不会撑大盒子

- 如果不想自己内减还可以求助一个属性:

  border-sizing:border-box;加上这个属性后,浏览器会自行计算多余的大小,自动在内容中减去

###### 外边距

- 设置边框以外,盒子与盒子之间的距离

- 属性名:margin

  | 取值 | 示例                         | 含义                                        |
  | ---- | ---------------------------- | ------------------------------------------- |
  | 1    | margin:10px;                 | 上下左右都是10                              |
  | 2    | margin:10px 20px ;           | 上下是10,左右是20                           |
  | 3    | margin:10px 20px  30px;      | 上是10,左右是20,下是30                      |
  | 4    | margin:10px 20px  30px 40px; | 上设置为10,右设置为20,下设置为30,左设置为40 |

- 单方向设置外边距,margin-方位名词  属性值-数字+px

- margin的左右和上都是作用于自己的,下是作用于下面的盒子的

###### 一些特殊情况

- 很多标签都有自己的默认设置,所以在代码的开头可以加一段

  ```css
    * {
              margin: 0;
              padding: 0;
          }
  ```

- 水平布局的盒子,左右的margin正常互不影响,两者之间的距离为左右margin的和

- 垂直布局的块元素,上下的magin会合并,两个盒子之间的距离为最大的那个margin,所以只给其中一个盒子设置margin即可

###### 塌陷现象

- 互相嵌套的块级元素,子元素的magin-top会作用在父元素上
- 解决办法:
  1. 给父元素设置overflow:hidden
  2. 给父元素设置边框或者padding
  3. 转换为行内块元素
  4. 设置浮动
  5. 设置定位,固定绝对定位的盒子也不会有塌陷问题

###### margin和padding的无效状况

- 水平方向的margin和padding在布局中有效
- 垂直方向的margin和padding在布局中无效
