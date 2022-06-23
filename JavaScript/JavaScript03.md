#### for循环

------
- for循环的特点是把声明起始值,循环条件和变化值写在了一起

- 语法

  ```js
   for(i=1 ;i<4; i++){
              //执行了i=1.2.3,3遍
              document.write('我要暴富')
          }
  ```

  > for循环中continue和break依然适用,作用依然是跳出本次循环或者是结束大循环

- 与while循环的异同

  $\textcolor{Emerald}{  如果明确了循环的次数,推荐使用for循环,当不明确循环的次数的时候推荐使用while循环}$

- for循环的嵌套

  ```js
     for(j=1 ; j<4 ; j++){
              document.write(`这是第${j}天<br>`)
              for(i=1; i<6;i++){
                  document.write(`今天背了${i+5*(j-1)}个单词<br>`)
              }
          }
  ```
  >$\textcolor{Emerald}{  实际上JavaScript中的任何一种循环都支持嵌套}$
- 任何循环都离不开三个值:起始值、变化量、终止条件


##### 数组

------

- 数组是一种可以按顺序保存数据类型的数据类型

- 数组和变量一样,在使用之前必须声明

- 数组的索引/下标是$\textcolor{Emerald}{  从0开始}$的,依次往后排,并且是通过下标取值的

- 遍历数组

  ```
   let arr = [12,34,56,78,90]
          for(i=0;i<arr.length;i++ ){
              document.write(arr[i])
          }
  ```

  > 就是循环了数组的长度次
  >
  > 一定要记得数组的下标是从0开始的

- 操作数组

  > 增

  ```js
          // 放在后面
          //增一个
          arr.push('wyb')
          console.log(arr)
          //增多个
          arr.push('12', '23')
          console.log(arr)
          //增一个数组
          let Aarr = ['zcyy', 'wsh']
          arr.push(Aarr)
          console.log(arr)
          
          // 放在前面
          //增一个
          arr.unshift('强宝')
          console.log(arr)
          //增多个
          arr.unshift('gxxl', 'lzm')
          console.log(arr)
          //增一个数组
          let Barr = ['leslie', 'mq']
          arr.unshift(Barr)
          console.log(arr)
  ```

  > 删

  ```js
          //删掉最后一个
          let arr = ['xz' ,'wyb','gxxl','lzm']
          arr.pop()
          console.log(arr)
  
          //删掉第一个
          let newArr = ['xz' ,'wyb','gxxl','lzm']
          newArr.shift()
          console.log(newArr)
  
          //从下标为2的元素开始删除一个数据
          let Arr01 = ['xz' ,'wyb','gxxl','lzm']
          Arr01.splice(2,1)
          console.log(Arr01)
  ```

  > 改

  ```js
         let arr = [1005, 805, 56, 34, 6500]
          arr[0] = 'xz'
          console.log(arr[0])
          //直接给对应的数组元素赋新值即可
  ```

  > 查

  ```js
          let arr = [1005, 805, 56, 34, 6500]
          //查(下标从0开始)
          console.log(arr[0])
  ```

##### if多分支语句和switch的区别

- 相同点:都能实现多分支循环,多选一,大部分情况下可以互换

- 不同点:

  1. switch通常处理case为比较确定的值的情况,而if... else .... 更加的灵活
  2. switch判断后直接到执行的语句,在某些情况下效率更高
  3. switch在判断case时一定要注意数据类型,不要落下break否则会穿透
  4. 当分支较少时if的效率高,当分支比较多的时候switch的结构更清晰

  











