#### 空间转换

------

##### 使用transform实现元素空间位移效果

- transform:translate3d(x,y,z)

  > 取值:$\textcolor{Emerald}{右边为正,下边为正,朝向自己为正}​$
  >
  > 可以用像素单位,也可以用百分比

- perspective属性实现透视效果

  > 此元素$\textcolor{Emerald}{添加给父级}$,语法为

  ```css
  perspective:800px;
  ```

  取值建议在$\textcolor{Emerald}{800~1200}$之间,比较便于观察,可以通过这个属性实现近大远小,近实远虚的视觉效果

  透视距离也被称为视距

##### 使用rotate实现元素空间旋转效果

- $\textcolor{Emerald}{左手法则}$:大拇指朝向正方向,其余四个手指指的方向就是旋转的方向
- 右方向为x轴的正方向,下方向为y轴的正方向,朝向自己为z轴的正方向
- 取值为deg和turn

##### 使用transform-style:preserve-3d呈现立体图形

- 此属性需要$\textcolor{Emerald}{添加给父元素}$,会让子元素处于真正的3d空间
- 如果不添加此属性,子元素默认是存在于二维平面里的

#### 动画

------

##### 使用animation添加动画效果

- 过渡可以实现2个状态之间的变化过程

- 过程可控

- 动画的本质是连续的画面,构成动画的最小单元是帧或动画帧

- 定义语法

  ```css
    @keyframes move{
              form{
                  transform: rotate(0deg);
              }
              to{
                  transform: rotate(720deg);
              }
          }
  ```

  > 定义动画的方法01

  ```css
          @keyframes move{
              0%{
                  transform: translate(0,0);
              }
              100%{
                  transform: translate(0,0);
              }
          }
  ```

  > 定义动画的方法02

- 调用语法

  ```css
  animation: move 5s ;
  ```

  > 第一个值是动画名,第二个是持续时间,这是必填项,
  >
  > 取值不分先后顺序
  >
  > 如果有两个时间值:第一个时间表示动画时长,第二个时间表示延长时间

  | 值                        | 描述                                          |
  | ------------------------- | --------------------------------------------- |
  | $\textcolor{red}{linear}$ | $\textcolor{red}{动画从头至尾的速度是相同的}$ |
  | ease                      | 默认,低速开始,然后加快,在结束之前变慢         |
  | ease-in                   | 动画以低速开始                                |
  | ease-out                  | 动画以低速结束                                |

- 一些相关属性

  | 属性                      | 作用     | 取值                         |
  | ------------------------- | -------- | ---------------------------- |
  | animation-iteration-count | 无限循环 | $\textcolor{red}{infinite}$  |
  | animation-direction       | 反向     | $\textcolor{red}{alternate}$ |
  | animation-play-state      | 暂停动画 | $\textcolor{red}{paused}$    |

- 用steps实现逐帧动画

  ```css
   animation: person 0.2s steps(12) infinite;
  ```

  > 此效果会让动画逐帧呈现,没有自动补间





















