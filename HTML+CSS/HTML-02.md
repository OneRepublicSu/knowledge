#### 列表标签

------

##### 无序列表(最常用)

- 场景:无顺序之分的列表,eg:新闻列表

- 标签组成

  ```html
     <ul>
          <li>01</li>
          <li>02</li>
          <li>03</li>
      </ul>
  ```

  >特点  01 自带小圆点  02 无顺序   $\textcolor{red}{03 ul里只能包含li标签}$  04 li标签里可以包含任何内容

  效果:

 [![1653201909496.md.png](https://s1.imagehub.cc/images/2022/05/26/1653201909496.md.png)](https://www.imagehub.cc/image/GPaxrK)
##### 有序列表

- 场景:有顺序之分的列表,eg:排行榜

- 标签组成

  ```html
      <ol>
          <li>01</li>
          <li>02</li>
          <li>03</li>
      </ol>
  ```

  >特点 : 01 自带代表顺序的数字 02 有顺序 $\textcolor{red}{03ol里只能包含li标签}$ 04 li标签里可以包含任何内容

  效果:
  
  [![1653202331701.md.png](https://s1.imagehub.cc/images/2022/05/26/1653202331701.md.png)](https://www.imagehub.cc/image/GParRc)
##### 自定义列表(列表底部导航)

- 标签组成

  ```html
    <dl>
         <dt>01</dt>
         <dd>011</dd>
         <dd>012</dd>
         <dd>013</dd>
     </dl>
  ```

  >特点  01 dd前默认缩进  02 dd和dt标签里可以包含任何内容  $\textcolor{red}{03dl里只能包含dt和dd标签}$  $\textcolor{red}{04dt是主题,dd是对dt的描述}$

  效果:
 [![1653202580706.md.png](https://s1.imagehub.cc/images/2022/05/26/1653202580706.md.png)](https://www.imagehub.cc/image/GPaqtY)

#### 表格标签

------

- 标签组成

  ```html
     <table>
          <tr>
              <td></td>
              <td></td>
          </tr>
          <tr>
              <td></td>
              <td></td>
          </tr>
      </table>
  ```

  > table-表格的整体  tr-行  td-单元格 
  >
  > ==注意:table里不能放除了tr之外的标签==

- 相关属性

  > border-边框宽度 width-表格宽度 height-表格高度

  $\textcolor{Emerald}{实际开发时推荐使用css进行装饰}$

- 表格大标题组成

  ```html
  <caption>
     <h3>班级成绩表</h3>
  </caption>
  ```

  > 表格的大标题-自动居中

- 表头单元格组成

  ```html
  <th>班级</th>
  ```

  > 表头单元格-文字加粗且居中

- 表格的基本结构(了解):

  thead-表格头部 tbody-表格主体 tfoot-表格底部

  不是必须写的部分,可以省略

- 合并单元格

  01:先明确合并哪几个单元格

  02:通过左上原则,确定保留谁删除谁$\textcolor{Emerald}{上下合并时留上方,左右合并时留左边}​$

- 给保留的单元格设置格式

  | 属性名  | 属性值           | 备注     |
  | ------- | ---------------- | -------- |
  | rowspan | 合并单元格的个数 | 跨行合并 |
  | colspan | 合并单元格的个数 | 跨列合并 |

  >只有一个结构标签中的单元格才能合并,不能跨结构合并标签

#### 表单标签

------

##### input系列标签

- type属性$\textcolor{red}{(不要拼错或者加多了属性,否则相当于默认值text)}​$

  | 标签名 | type属性值                      | 说明                    |
  | ------ | ------------------------------- | ----------------------- |
  | input  | $\textcolor{Emerald}{text}$     | 文本框用于输入单行文本  |
  |        | $\textcolor{Emerald}{password}$ | 密码框用于输入密码      |
  |        | $\textcolor{Emerald}{radio}$    | 单选框用于多选一        |
  |        | $\textcolor{Emerald}{checkbox}$ | 多选框用于多选多        |
  |        | file                            | 文件选择,用于上传文件   |
  |        | submit                          | 提交按钮,用于提交       |
  |        | reset                           | 重置按钮,用于重置       |
  |        | button                          | 普通按钮,需结合js来应用 |

- 文本框

  > 常用属性:placeholeder:占位符-提示用户输入内容的文本

- 密码框

  > 常用属性:placeholeder:占位符
  >
  > 特点:自动隐藏输入的文字

- 单选框

  > 常用属性:$\textcolor{red}{name:分组功能(同类的name相同,不同的类需要进行区分)}$ checked:默认选中
  >
  > 特点:一组当中同时只有一个能被选中

- 复选框

  > 常用属性: $\textcolor{red}{checked:默认选中}$
  >
  > 特点:一组当中同时可以有多个被选中

- 文件选择

  >常用属性:multiple:多文件选择

- 按钮

  >常用属性: submit:提交按钮 reset:重置按钮 button:普通按钮

  ==以上所有的标签都必须被包裹在form中才能生效==

##### button按钮标签

- type属性值

  | 标签名 | type属性值                    | 说明                                            |
  | ------ | ----------------------------- | ----------------------------------------------- |
  | button | submit                        | 提交按钮                                        |
  |        | reset                         | 重置按钮                                        |
  |        | $\textcolor{Emerald}{button}$ | $\textcolor{Emerald}{普通按钮(谷歌默认是提交)}$ |

  > button与input的button值的区别在于它是双标签,便于包裹其他内容

  

##### select下拉菜单标签

- 代码组成

  ```html
   <select>
              <option>请选择城市:</option>
              <option>武汉</option>
              <option>长沙</option>
              <option selected>重庆</option>
              <option>杭州</option>
          </select>
  ```

  > select-下拉菜单的整体 option-下拉菜单的每一项 
  >
  > $\textcolor{Emerald}{selected:下拉菜单的默认选中}$

- 也需要被包裹在form之中才能生效

##### textarea文本标签

- 代码组成

  ```html
  <form>
  <textarea cols="30" rows="10" placeholder="请输入评论内容....."></textarea>
  <form>
  ```

  >cols-宽 rows-高 实际开发仍然推荐用css来完成

##### label标签

- 第一种方法

  ```html
    <input type="radio" name="sex" id="man">
    <label for="man"> 男</label>
  ```

  > 在label标签的for属性中设置对应的id属性值

- 第二种方法

  ```html
   <label ><input type="radio" name="sex" > 女</label>
  ```

  > 直接使用label标签把内容（如：文本）和表单标签一起包裹起来 
  >
  > $\textcolor{red}{图片标签放在label标签里}$

#### 语义化标签

##### 没有语义的布局标签

- 标签组成

  | 标签 | 特点             |
  | ---- | ---------------- |
  | div  | 一行只显示一个   |
  | span | 一行可以显示多个 |

##### 有语义的布局标签

- 标签组成(了解)

  | 标签名  | 语义       |
  | ------- | ---------- |
  | header  | 网页头部   |
  | nav     | 网页导航   |
  | footer  | 网页底部   |
  | aside   | 网页侧边栏 |
  | section | 网页区块   |
  | article | 网页文章   |

  > 显示和div一致,但是更加语义化,多用于移动端

#### 字符实体

------

- 常见实体

  | 显示结果 | 描述 | 实体名称       |
  | -------- | ---- | -------------- |
  |          | 空格 | ==& n b s p;== |
  | <        | 小于 | ==& l t ;==    |
  | >        | 大于 | ==& g t;==     |

