### css基础认知

#### 基础了解

------

- css叫做层叠样式表(也叫做级联样式表)

  结构为:***选择器{属性名:属性值};*** /属性名:属性值一起也叫做样式键值对 

- css引入方式

  | 引入方式   | 书写位置                                                    | 作用范围 |
  | ---------- | ----------------------------------------------------------- | -------- |
  | 内部样式表 | css写在style标签中                                          | 当前页面 |
  | 外部样式表 | $\textcolor{Emerald}{css写在单独的css文件里再通过link引入}$ | 多个页面 |
  | 行内样式   | 标签的style属性中                                           | 当前标签 |

  

#### 基础选择器

------

##### 标签选择器

- 代码组成

  ```html
  p{color: red;}
  ```

  > 标签名{css属性名:属性值;}

  注意:$\textcolor{Emerald}{标签选择的是一类标签而不是某一个}$,不管嵌套的多深,选择器都可以找到对应的标签

##### 类选择器

- 代码组成

  ```html
  .pink{color: pink;}
  ```

  >.类名{css属性名:属性值;}

  注意:可以由数字字母下划线中划线组成,$\textcolor{Emerald}{但不能以数字和中划线开头}$,

  一个标签可以同时具有多个类名,中间用空格隔开

  类名可以重复,一个类选择器可以同时选中多个标签

##### id选择器

- 代码组成

  ```html
  #yellow {color: yellow;}
  ```

  > #id属性值 { css属性名：属性值； } 

  注意:id类似于身份证号码,他在整个页面里是唯一的,不可重复的

  一个标签只能有一个id,$\textcolor{red}{一个id选择器只能选中一个标签}$


##### 类选择器与id选择器的区别

- 不同点

  | class                                         | id                                 |
  | --------------------------------------------- | ---------------------------------- |
  | class相当于姓名,一个标签可以同时有多个class名 | 相当于身份证号码不可重复具有唯一性 |
  | $\textcolor{Emerald}{以.开头}$                | **#**$\textcolor{Emerald}{开头}$   |
  | 广泛使用                                      | 一般配合js使用                     |

##### 通配符选择器

- 代码组成

  ```html
  *{color: rgb(206, 168, 175);}
  ```

  > *{ css属性名：属性值； } 

  注意:这是一个需要慎重使用的选择器,它会作用于页面的所有标签

#### 字体和文本样式

------

##### 字体样式

- 字体大小

  属性名:font-size 取值:数字 + px

  谷歌浏览器默认文字大小是16px / 单位需要设置，否则无效

- 字体粗细

  属性名：font-weight 取值:100~900的整百数 $\textcolor{Emerald}{400是正常,700是加粗}$

- 字体样式

  属性名：font-style取值：正常（默认值）：normal 倾斜：italic

- 字体系列

  属性名:font-family 取值具体字体1,具体字体2,具体字体3,具体字体4,...,字体系列

  > 规则为从左往右按顺序查找,如果未安装则显示下一个字体,直到显示默认字体为止

  注意:如果字体名称存在多个单词,推荐使用引号包裹

- 常见的字体系列(了解)

  无衬线字体-粗细均匀且首尾无装饰

  衬线字体-文字字体粗细不均且收尾有笔锋装饰

  等宽字体-每个字母或者文字的宽度相等

- 字体font相关属性的连写

  属性名：font (复合属性) 取值：font : style weight size family

  > 注意:只能省略前两个值,省略了相当于设置了默认值
  >
  > 如果需要同时设置单独和连写形式,单独的样式必须要在连写的下面

##### 文本样式

- 文本缩进

  属性名：text-indent 取值:数字+px,数字+em(em是默认字体的倍数2就是两倍)

- 文本的水平对齐方式

  属性名：text-align 取值:left:z左对齐 right:右对齐 center:居中

  > 如果要让文本水平居中,text-align属性要加在文本所在标签的父元素上

- 文本修饰

  属性名：text-decoration 

  取值:$\textcolor{Emerald}{underline下划线 none无装饰线 }$overline上划线 line-through删除线

##### line-height行高

- 作用:控制一行的上下行间距(值=上边距+下边距+字高)

  属性名:line-height 取值:数字+px  or em

  > 让单行文本垂直居中可以设置line-height:文字的父元素的高度
  >
  > 如果把行高加进font连写,要注意覆盖问题

  ***font : style  weight size/line-height family;***

#### Chrome调试工具

- 打开方式

  检查;styles是当前元素的css样式,elements是当前页面的html结构

- 控制样式

  有的属性值可以直接修改/添加属性可以在上一个属性的分号后面点击一下,直接添加/控制属性是否生效只需要点击前面的小框里的√

- 特殊情况

  | 现象           | 含义     | 原因                                              |
  | -------------- | -------- | ------------------------------------------------- |
  | 出现删除线     | 样式失效 | 样式被注释                                        |
  |                |          | $\textcolor{Emerald}{样式被覆盖}$                 |
  | 样式前有小三角 | 样式报错 | $\textcolor{Emerald}{属性后没有写分号}$           |
  |                |          | $\textcolor{Emerald}{出现中文标点}$               |
  |                |          | $\textcolor{Emerald}{属性名或者属性值的单词拼错}$ |

#### web颜色(了解)

- 四种基本的颜色表示法

  | 方法           | 属性以及取值             | 特点                                                         |
  | -------------- | ------------------------ | ------------------------------------------------------------ |
  | 关键词         | red：红色                |                                                              |
  | rgb表示法      | rgb ( 255 , 0 , 0 )      |                                                              |
  | rgba表示法     | rgba ( 0 , 0 , 0 , 0.5 ) | 可以指定透明度                                               |
  | 十六进制表示法 | #ffaabb                  | 如果三组中，每组数字都相同，此时可以每组可以省略只写一个数字 |

  



