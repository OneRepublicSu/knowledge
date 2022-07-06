#### 日期对象

------

##### 实例化

- 在代码中发现了new这个关键字时，我们一般将这个操作称为实例化

- 语法

  ```javascript
  const day = new Date()
  ```

##### 日期对象方法

- 语法

  | 方法                                     | 作用     | 说明                        |
  | ---------------------------------------- | -------- | --------------------------- |
  | date.getFullYear()                       | 获得年份 | 四位年份                    |
  | $\textcolor{Emerald}{date.getMonth()+1}$ | 获得月份 | $\textcolor{Emerald}{0-11}$ |
  | date.getDate())                          | 获得日期 | 根据月份不同                |
  | date.getDay())                           | 豁得星期 | 0~6                         |
  | date.getHours())                         | 获取小时 | 0~23                        |
  | date.getMinutes())                       | 获取分钟 | 0~59                        |
  | date.getSeconds())                       | 获取秒钟 | 0~59                        |

##### 时间戳

- 使用场景：如果计算倒计时效果，前面方法无法直接计算，需要借助时间戳来完成

- 算法

  将来的时间戳 - 现在的时间戳 = 剩余的时间毫秒数

  剩余时间毫秒数转换为剩余时间的年月日时分秒就是倒计时时间

  1s = 1000ms

- 语法

  ```javascript
         const date = new Date()
          console.log(date.getTime())
          console.log(+new Date())
          console.log(Date.now())
  ```

  > 最后一种方法不能传参

  

#### 页面尺寸与位置事件

- 语法

  ```javascript
     window.addEventListener('resize',function(){
           // 获取元素
          const box = document.querySelector('.box')
          // 求高度
          console.log(box.clientWidth , box.clientHeight)    
          })
  ```

- resize是在窗口尺寸改变时触发的事件

- clientWidth和clientHeight

  $\textcolor{Emerald}{  获取元素的可见部分宽高,不包含边框,margin,滚动条}$

- 语法

  ```javascript
    // 获取元素
          const father = document.querySelector('.father')
          const son = document.querySelector('.son')
  
          // box-sizing: border-box会影响盒子的真实宽度  可视宽度
          console.log(father.offsetWidth, father.offsetHeight)
          console.log(son.offsetWidth, son.offsetHeight)
  ```

- offsetLeft和offsetTop 是只读属性,位置以带有定位的父元素为准,如果都没有就以文档左上角为准

   获取的是可视宽高, 如果盒子是隐藏的,获取的结果是0 

  $\textcolor{Emerald}{  offsetWidth得到的是内容 + padding + border加在一起的宽高}$

-  element.getBoundingClientRect() 

  方法返回元素的大小及其相对于视口的位置 

  




