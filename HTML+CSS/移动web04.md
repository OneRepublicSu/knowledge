#### flex布局

------

##### flex-direction

- 作用:改变flex布局的主轴方向

- 主轴默认是水平方向,侧轴默认是垂直方向

- 属性值及其效果

  | 属性                          | 效果                           |
  | ----------------------------- | ------------------------------ |
  | row                           | 行,水平(默认)                  |
  | $\textcolor{Emerald}{column}$ | $\textcolor{Emerald}{列 垂直}$ |
  | row-reverse                   | 行,从左向右                    |
  | column-reverse                | 列,从下向上                    |

##### 精灵二倍图

- 背景精灵图也存在二倍图

- 语法:

  ```css
  background-size:32px auto;
  ```

- 有时会出现三倍图,在正常的web模式下不存在3倍图,需要切换到ios模式,即可看到三倍图选项

##### flex-wrap

- 作用:控制弹性盒子的换行(默认情况下弹性盒子不换行)

- 语法

  ```css
  flex-wrap:wrap;
  ```

- 调整对齐方式

  ```css
  align-content:center
  ```

  > $\textcolor{Emerald}{此对齐方式适用于多行对齐}$
  >
  > 取值与justify-content基本相同
  >
  > 多行与此属性必须同时使用才能达到对齐效果

