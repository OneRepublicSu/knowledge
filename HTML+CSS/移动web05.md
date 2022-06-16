#### 移动适配方案

------

##### 基础内容

- 适配的本质:屏幕的宽度发生变化时,页面元素的尺寸和高度也随之变化
- 主流的两种适配方法:$\textcolor{red}{rem和vw}​$

##### 长度单位rem

- rem是一个相对单位,它的大小是相对于html标签的字号计算后的结果

  $\textcolor{Emerald}{1rem=1html字号大小}$

  > 所以我们只需要修改html的文字大小就可以完成元素大小的等比例缩放

##### 媒体查询

- 媒体查询可以检测视口的宽度,然后编写差异化的css样式

- 语法

  ```css
     @media (width:375px) {
              body {
                  background-color: red;
              }
          }
  
  ```

##### rem的适配原理

- 运用rem适配的步骤流程是

  > 查看设计稿宽度>确定参考设备宽度>确定基准根字号

  $\textcolor{red}{rem单位的尺寸=px单位数值 / 基准根字号}$

##### flexible js

- $\textcolor{Emerald}{flexible.js}$是一个用来适配移动端的js库

  核心原理就是根据不同视口宽度给网页中html根节点设置不同的font-size

#### less

------

##### less语法

- css不支持计算写法,可以通过less实现,less是一个css预处理器,扩充了css语言,使css具备一定的逻辑性和计算能力
- 浏览器不识别less代码,目前阶段,网页要引入对应的css文件

- 加减乘直接书写计算表达式

- 除法需要添加小括号或.

  ```less
  width: (200 / 37.5rem);
  ```

  > 如果表达式存在多个单位以第一个单位为准
  >
  > $\textcolor{Emerald}{但是我们推荐将单位尽量写到最后一个数字上}$
  >
  > 先乘除后加减

- less可以直接嵌套生成后代选择器和伪类,伪元素

  ```css
  .nav {
    width: 100px;
    height: 100px;
    background-color: pink;
    &::before {
      content: '1';
    }
    &:hover::before {
      color: red;
    }
  }
  ```

  ```less
  .box {
      .son {
          background-color: pink;
  
          p {
              color: red;
  
              span {
                  color: yellow;
              }
          }
      }
  }
  ```



##### less变量设置属性值

- 语法

  ```css
  @color: red;
  @borderColor: 1px solid #ccc;
  ```

  > 此方法易于进行项目维护，后期修改也非常的容易快捷

##### less的导入与导出

- 导入语法

  ```css
  // 写法1  
  @import url(./02-less计算.less);
  // 写法2
  @import './01-less的注释.less';
  ```
  less语法的优点之一就是减少了html页面的link标签数量

- 导入/导出

  | 方法                        | 效果                            |
  | --------------------------- | ------------------------------- |
  | setting.json里配置out属性   | 沿着指定的路径导出对应的css文件 |
  | less文件首行设置编写out属性 | 沿着指定的路径导出对应的css文件 |
  | less文件的首行添加out属性   | 禁止该less文件导出css文件       |

  ```js
      "less.compile": {
      "out":"../css/"
      },
  ```

  > 此处属性名和路径都必须用双引号包起来

  ```css
  // out: ../css/
  ```

  > 最后一个文件夹后面必须要带一个斜线表示进入该文件夹

  ```css
  // out:false 
  ```

  > 使用此语法在建立文件之前需要关闭自动保存