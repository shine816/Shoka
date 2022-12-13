# JavaScript

## 目录导航

| 目录                         | 简介                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| 0 容易遗忘内容               | 当前笔记中容易遗漏知识点记录                                 |
| 1 JavaScript简介             | 简要介绍JavaScript的作用及语言特点                           |
| 2 **变量 let var**           | 介绍`let` 与 `var` 关键字声明变量的使用及各自作用范围        |
| 3 数据类型                   | 简述 js 里面存在的 `string`，`number`,`boolean`,`undefined`四种数据类型 |
| **4 运算符**                 | js 里面的运算符使用  注意点:**JavaScript中进行减乘除运算时会自动将变量转成数值类型==== 加法:会用于字符串拼接** |
| 5 各种语句                   | 循环、分支语句的描述                                         |
| **6 html页面中添加JS代码**   | 简述在HTML页面中添加JS代码的三种方式 **内部 内联 外部**      |
| 7 方法                       | 简述 js里面创建方法的三种方式 **其中第三种new Funtion(..)较为特殊** |
| 8 和页面相关的方法           | 简述元素模型dom模型如何**创建标签、获取标签元素、获取标签值**等方法及属性 |
| 9 NaN简介                    | 简述不是个数出现的条件  以及`isNaN(参数)`的方法运用          |
| 10 javaScript对象分类        |                                                              |
| ------10.1 BOM浏览器对象模型 | 简述window里面内置的几个**常用方法** 及 **location 、history**属性信息 |
| ------10.2 DOM文档对象模型   | 描述介绍当前JS操作得6个属性或方法 `获取元素标签对象`,`创建元素标签对象`,`追加元素`,`获取或设置文本值`,`获取或设置控件值`,`获取页面body` |



## 0 容易遗忘内容

1. [^1]:字符串参与<font size=5 >加法</font>运算时，默认为拼接运算，需要自己手动转为number值进行加法运算 <font size=5px>**JavaScript中进行减乘除运算时会自动将变量转成数值类型,如果不是数值则会转成NaN**</font>

2. [^2]: JS中三种定义方法的方式,第三种直接new Function对象方式任意遗忘

3. [^3]:<font size=5>**window常用方法及属性 location history等**</font>

4. [^4]:<font size=5 color=green> **JS目前所学习的六个对元素操作的属性或方法** </font>

3. 

## 1 JavaScript简介

- 作用: 给页面添加动态效果
- 语言特点:  
  - 属于脚本语言,不需要编译,直接由浏览器解析执行
  - 属于弱类型语言        
  - **基于面向对象的语言**
  - 安全性强: JS语言只允许访问浏览器内部的数据,浏览器以外的数据禁止访问.
  - 交互性强: 因为JS语言是嵌入到HTML页面中,运行在客户端的语言, 直接和用户面对面进行交互.



- 编程语言包括: 
  - 变量,数据类型,运算符,各种语句,方法,面向对象


## 2 变量 let var

- JS语言属于弱类型语言, 声明变量的时候不需要指定类型   

- 通过let或var关键字声明变量 

  - `let` 声明的变量作用域和java语言类类似

  - `var`声明的变量 作用域相当于java中的**全局变量,**可以在页面中任何地方调用

  - 举例:

    - ```javascript
      java:
      
      for(int i=0;i<10;i++){
      	int j=i+1;
      }
      int x = i+j;   //i和j都超出了作用域 编译报错 
      
      JavaScript:
      
      for(let i=0;i<10;i++){
      	let j=i+1;	    
      }
      let x = i+j;  //不报错 但是访问不到i和j 因为超出了作用域
      
      for(var i=0;i<10;i++){
      	var j=i+1;	    
      }
      var x = i+j;   //不报错 并且可以访问i和j的值 
      ```

## 3 数据类型

- JS语言中只有对象类型 

- 常见的对象类型:
  - **string**字符串:  可以用单引号或双引号修饰    "abc"   'abc'
  - **number**数值:   相当于Java中所有数值类型的总和
  - **boolean**布尔值:   true和false
  - **undefined**未定义:  当变量**只声明不赋值**的时候,变量为未定义类型
  
- 获取变量类型的方式: **typeof(变量)**;

- ```javascript
  let a = 1;
  let type = typeof(a);//number
  ```

- 

## 4 运算符

- 算术运算符: + - * / %
  - JS 除法运算会自动根据结果转成整数或小数 
    - java:   int x =5 ; int y =2;   int z = x/y;     z=2  
    - JS:     let x = 5;  let y = 2;  let z = x/y;    z=2.5       x=6   z=3
  
  - 字符串参与运算
  
    - 在**做加法运算的时候，会默认按照字符串进行拼接**，如果要做数字运算需要进行先行**parseInt || parseFloat** 转换为number值[^1]
  
      ```javascript
      let a = "12";
      let b = 3;
      //减 乘 除运算会自动减字符串转为数字
      a / b = 4;
      //加法 运算 需要自行转换为数值
      a+b // "123" 为转换前
      parseInt(a)+b //15 转换后
      ```
  
    - 其他运算时 会自动默认将字符串转为数字进行运算
    
      - <font size=5px>**JavaScript中进行减乘除运算时会自动将变量转成数值类型,如果不是数值则会转成NaN**</font>
  
- 关系运算符:  > < >=  <=  !=  ==和===
  - ==:  先统一等号两边变量的类型 再比较值,  "666"==666      true
  - ===: 先比较类型, 类型相同之后再比较值,   "666"===666     false
  
- 逻辑运算符: && || !  只支持短路与和短路或   

- 赋值运算符:  =   +=  -=  *=  /=  %=   

- 三目运算符:    条件?值1:值2

## 5 各种语句

- if  else
- for
- while
- switch case

## 6 html页面中添加JS代码

- 和CSS一样有三种引入方式:
  - **内联**: 
  
    - 在标签的事件属性中添加js代码, 当事件触发时执行 
  
      - 事件: 系统给提供的一系列时间点 
      - 点击事件: 当用户点击某个元素时触发的时间点
  
      ```HTML
      <!--给按钮添加点击事件 当按钮被点击时会执行onclick点击事件里面的js代码
        alert('xxx') 是JavaScript语言中提供的弹出提示框方法.
      -->
      <input type="button" value="按钮" onclick="alert('按钮点击了')">
      ```
  
  - **内部**: 
  
    - 在html页面中的任意位置添加script标签,在标签体内写js代码
  
      ```HTML
      <script>
        //JS单行注释
        /*JS多行注释*/
        // alert("内部JS代码执行成功!");
        //在浏览器的控制台中输出数据 类似Java的sout
        console.log("内部JS代码执行成功!")
      </script>
      ```
  
  - **外部**:
  
    -  在单独的JS文件中写JS代码, 在html页面中通过script标签引入并执行
  
      ```HTML
      <!--引入外部js文件-->
      <script src="my.js"></script>
      ```

## 7 方法

- Java: public 返回值类型 方法名(参数列表){方法体}   

- JS: function 方法名(参数列表){方法体}

- **常见的四种方法**:
  
  - 无参无返回值
  
    ```javascript
     //无参无返回值
      function f1() {
        console.log("f1")
      }
    ```
  
  - 有参无返回值
  
    ```javascript
      //有参无返回值
      function f2(name,age) {
        console.log(name+":"+age);
      }
    ```
  
  - 无参有返回值
  
    ```javascript
      //无参有返回值
      function f3() {
        return "我是返回值";
      }
    ```
  
  - 有参有返回值
  
    ```javascript
      //有参有返回值
      function f4(x,y) {
        return x*y;
      }
    ```
  
    
  
- **<font color=red>JS中三种定义方法的方式</font>**:[^2]
  
  - **function 方法名(参数列表){方法体}**
  
    ```javascript
      function f2(name,age) {
        console.log(name+":"+age);
      }
    ```
  
    
  
  - **let 方法名 = function(参数列表){方法体}**
  
    ```javascript
      let f5 = function (name,age) {
        console.log(name+":"+age);
        parse
      }
    ```
  
    
  
  - **let 方法名 = new Function("参数1","参数2"...,"方法体");**
  
    -  注意:参数字段名要用字符串引起来
  
    ```javascript
      let f6 = new Function("name","age"
          ,"console.log(name+':'+age)");
      f6("关羽",70);
    ```
  
    

## 8 和页面相关的方法

   

| 关键字                                 | 描述                         |
| -------------------------------------- | ---------------------------- |
| document.**querySelector**("选择器")   | 获取标签元素对象             |
| **innerText**                          | 获取文本内容 \| 设置文本内容 |
| **value**（与控件值相关）              | 获取**控件**值 \| 设置控件值 |
| document.**createElement**("元素标签") | 创建一个元素标签             |
| 元素标签.**append**(元素)              | 在元素标签里面追加一个子元素 |



- 通过选择器查找页面中的元素对象   

  **let 元素对象 = document.querySelector("选择器");**
  
  ```javascript
  //获取页面中的文本框和span
    let i = document.querySelector("input");
    let s = document.querySelector("span");
  ```


- 获取或修改元素的文本内容    

  元素对象.**innerText** = "xxx";      修改元素的文本内容 

  元素对象.innerText         获取元素的文本内容  

  ```javascript
   s.innerText = "输入错误";
  ```

  

- 获取或修改控件的值   (控件:文本框,密码框,单选,多选,下拉选等)

  控件对象.**value**="xxxx";   修改控件的值

  控件对象.value      获取控件的值 
  
  ```javascript
  let name = i.value;
  ```

## 9 NaN 简介

- Not a Number: 不是一个数 ,  NaN和任何数值进行任何运算得到的结果都是NaN
- <font size=5px>**JavaScript中进行减乘除运算时会自动将变量转成数值类型,如果不是数值则会转成NaN**</font>
- isNaN(变量)  判断变量是否是NaN   返回值为布尔值  
  - true代表是NaN
  - false不是NaN




## 10 JavaScript中对象分类

​		

| 对象分类                      | 描述                                   |
| ----------------------------- | -------------------------------------- |
| 内置对象                      | number,string,boolean等                |
| BOM: **Browser Object Model** | 浏览器对象模型, 包含和浏览器相关的内容 |
| DOM: Document Object Model    | 文档对象模型, 包含和页面相关的内容     |

### 10.1 BOM浏览器对象模型[^3]

- window对象: 该对象中的属性和方法称为全局属性和全局方法, 访问的时候可以省略掉window.  

- window对象中常见方法:

- | window常见方法                         | 描述                                              |
  | :------------------------------------- | ------------------------------------------------- |
  | **isNaN()**                            | 判断变量是否是NaN                                 |
  | **parseInt()**                         | 将字符串或小数转成整数 "28.5"->28   28.5->28      |
  | parseFloat()                           | 将字符串转成整数或小数   "25"->25    "25.8"->25.8 |
  | alert("xxx")                           | 弹出提示框                                        |
  | confirm("xxx")                         | 弹出提示框                                        |
  | confirm("xxx")                         | 弹出确认框                                        |
  | **prompt("xxx")**                      | 弹出文本框                                        |
  | let timer = setInterval(方法,时间间隔) | 开启定时器                                        |
  | clearInterval(timer)                   | 停止定时器                                        |
  | setTimeout(方法,时间间隔)              | 开启只执行一次的定时器                            |

- window对象中常用的属性 
  - <font size = 5 color=red>**location**</font> 位置
    - **location.href** 获取或修改浏览器的请求地址   
    - **location.reload();**   浏览器重新加载(刷新) 
  - <font size = 5 color=red>**history**</font> 历史
    - **history.length**  得到历史页面数量
    - **history.back();**  返回上一页面
    - **history.forward();** 前往下一页面

### 10.2 DOM文档对象模型[^4]

- 包含页面相关的内容

- | DOM文档方法                           | 描述                                                         |
  | ------------------------------------- | ------------------------------------------------------------ |
  | **document.querySelector**("选择器"); | 通过选择器查找页面中的元素对象                               |
  | .innerText                            | 获取或修改元素的文本内容                                     |
  | .**value**                            | **获取或修改控件的值   (控件:文本框,密码框,单选,多选,下拉选等)** |
  | **document.createElement**("标签名"); | 创建元素对象的方法                                           |
  | 元素对象.**append**(新元素)           | 添加到某一个元素里面                                         |
  | **document.body**                     | 获取页面中body的方式                                         |

  

1. 通过选择器查找页面中的元素对象   

   let 元素对象 = **document.querySelector**("选择器");

   

2. 获取或修改元素的文本内容    

   元素对象**.innerText** = "xxx";      修改元素的文本内容 

   元素对象.innerText         获取元素的文本内容  

   

3. 获取或修改控件的值   (控件:文本框,密码框,单选,多选,下拉选等)

   控件对象.**value**="xxxx";   修改控件的值

   控件对象.value      获取控件的值 

   

4. 创建元素对象的方法

   let 变量 = **document.createElement**("标签名");

   

5. 添加到某一个元素里面

   元素对象.**append**(新元素)

   

6. 获取页面中body的方式

   **document.body**
   
   应用实例:
   
   ```javascript
    //给按钮添加点击事件,方法里面创建tr和3个td把文本框的内容设置给td
     //把td装进tr,把tr装进table标签
     //得到页面中的元素对象
     let i1 = document.querySelector("#i1");
     let i2 = document.querySelector("#i2");
     let i3 = document.querySelector("#i3");
     let table = document.querySelector("table");
     function f() {
       //创建tr和td
       let tr = document.createElement("tr");
       let nameTd = document.createElement("td");
       let salaryTd = document.createElement("td");
       let jobTd = document.createElement("td");
       //把文本框的内容赋值给td
       nameTd.innerText = i1.value;
       salaryTd.innerText = i2.value;
       jobTd.innerText = i3.value;
       //把td装进tr
       tr.append(nameTd,salaryTd,jobTd);
       //把tr装进table
       table.append(tr);
     }
   ```
   
   
