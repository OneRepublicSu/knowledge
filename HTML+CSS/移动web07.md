#### 响应式

------

##### 媒体查询

- 媒体查询的作用：能够根据设备的宽度变化，设置差异化样式

- 语法

  ```css
    @media(min-width：540px){
              body{
                  background-color: #fff;
              }
          }
      @media screen and (max-width:1189px) {
          body{
              background-color: aquamarine;
          }    
        }
  ```

- 两个基本值的含义

  ![坐标系.png](https://s2.loli.net/2022/06/19/C4TuV9YMSJ5F72w.png)

- 外链式css引入媒体查询

  ```css
   <link rel="stylesheet" href="./css/m.css" media="(max-width:768px)">
  ```

##### bootstrap

- UI框架:将常见效果进行统一封装后形成的一套代码

  作用:基于框架开发,效率高,稳定性高

- bootstrap使用步骤

  首先第一步需要下载/引入在线链接(链接较慢不推荐)

  then在文件结构中引入bootstrap的css,运用JavaScript插件时还需要引入$\textcolor{Emerald}{jQuery文件和js文件}$

##### 栅格系统

- 底层原理:通过一系列的行与列的组合创建页面布局

- bootstrap3默认将网页分成12等份

- bootstrap的默认响应点

  |        | 超小屏 | 小屏   | 中等屏 | 大屏    |
  | ------ | ------ | ------ | ------ | ------- |
  | 响应点 | 768px- | 768px+ | 992px+ | 1200px+ |
  | 前缀   | xs     | sm     | md     | lg      |

- bootstrap系统为我们提供了专门的版心类

  > container
  >
  > 默认指定了宽度并且居中
  >
  > container-fluid通栏盒子,宽度为100%

  注意:$\textcolor{Emerald}{container类自带padding15px,row自带padding-15px}$

- 列偏移

  ```html
   <div class="container">
      <div class="row first">
        <div class="col-lg-4">左侧</div>
        <div class="col-lg-4 col-lg-offset-4">右侧</div>
      </div>
      <div class="row second">
        <div class="col-lg-3 col-lg-offset-3">1侧</div>
        <div class="col-lg-3 col-lg-offset-3">2侧</div>
      </div>
      <div class="row third">
        <div class="col-lg-6 col-lg-offset-3"></div>
      </div>
    </div>
  
  ```

  > col-lg-offset-xx xx是偏移值，偏移了几等份

- 列嵌套

  > 一个盒子里可以再嵌套其他的盒子,站在这个盒子的角度来看,他又分为了12份

  

  

  

  

  

  

  

  





