# 	VUE

## 目录导航

具体内容参照:  

 [Vue官网](https://cn.vuejs.org/)

API指令内容参照:

  [Vue内置指令](https://cn.vuejs.org/api/built-in-directives.html#v-text)

| 目录                     | 简介                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 0 容易遗忘内容           | 当前笔记中容易 遗忘点                                        |
| 1 设计模式               | 简述前端的俩种设计模式 `MVC`,`MVVM`                          |
| 2 VUE简述                | 简单介绍VUE的作用                                            |
| 3 如何引入vue.js框架文件 | 简单介绍vue.js文件引入的途径，及相关引入**地址链接**         |
| 4 安装Vue插件            | IDEA中插件商城安装Vue插件                                    |
| 5 HelloVue               | **简单的Vue框架代码示例**                                    |
| **6 Vue相关指令**        | Vue的相关指令介绍及应用示例 `文本相关`,`属性绑定`，`双向绑定`，`事件绑定`，`循环绑定`，`显隐判断`等 |



## 0 容易遗忘内容

1. [^1]: 前端常见的俩种设计模式 特别是MVVM模式

2. [^2]:如何引入Vue文件

3. [^3]:Vue目前的相关指令，文本相关，属性绑定，控件双向绑定，事件绑定，显隐判断，循环绑定等

4. [^4]:<font size=5>属性绑定时要看对应的属性后面跟的是不是变量，如果是则加属性绑定 :</font>

4. 

## 1 设计模式[^1]

### 1.1 前端M,V,C设计模式

- **MVC**设计模式是将实现一个前端业务功能的所有代码划分为三部分
  - **Model**: 模型, 指数据模型, 对应的代码是和数据相关的代码
  - **View**: 视图, 指页面相关代码, 对应的是页面中标签相关的代码
  - **Controller**:控制器, 把Model显示到View中的**过程代码**称为控制器


- 前端MVC设计模式中, 在Controller部分将数据显示到页面中,**需要频繁的进行DOM相关操作(查找元素/创建元素等), 浪费资源**, 前端的MVVM设计模式可以解决此问题 

<img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221208112011900.png" alt="image-20221208112011900" style="zoom:60%;" />

### 1.2 前端M,V,VM设计模式

- **MVVM**设计模式是将实现一个前端业务功能的所有代码划分为三部分
  - **Model**: 模型, 指数据模型, 对应的代码是和数据相关的代码
  - **View**: 视图, 指页面相关代码, 对应的是页面中标签相关的代码
  - **VM**:**ViewModel**视图模型, 负责将页面中**可能发生改变的元素和某一个变量在内存中进行绑定,并且会不断地监听变量值的改变, 当变量的值发生改变时,可以直接从内存中的对应关系里面找到对应的页面元素,** 这样就不用每次遍历查找元素了  

- <img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221208113141866.png" alt="image-20221208113141866" style="zoom:60%;" />

## 2 VUE简述

- VUE是目前最流行的前端框架, 基于**MVVM**设计模式
- VUE框架两种用法:

  - 多页面应用
    - 在html页面中引入vue.js框架文件
  - 单页面应用
    - 通过脚手架的方式使用VUE框架

## 3 如何引入vue.js框架文件[^2]

- 两种方式:

  - **从CDN服务器引入框架文件**

    ```HTML
    <script src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
  
  
  
  - | 框架文件                         | 地址                                                        |
    | -------------------------------- | ----------------------------------------------------------- |
    | 推荐: **Staticfile CDN**（国内） | https://cdn.staticfile.org/vue/2.2.2/vue.min.js             |
    | unpkg                            | https://unpkg.com/vue@2.6.14/dist/vue.min.js                |
    | cdnjs                            | https://cdnjs.cloudflare.com/ajax/libs/vue/2.1.8/vue.min.js |
  
    
  
    ![image-20221202142220963](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221202142220963.png)
  
  - **把框架文件下载到本地后再引入**
  
    ```HTML
    <script src="js/vue.min.js"></script>
  
    

## 4 安装Vue插件

- **File->Settings->Plugins**

  <img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221202152754290.png" alt="image-20221202152754290" style="zoom:50%;" />

## 5 HelloVue （第一个Vue工程）

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div>
  <h1>{{info}}</h1>
</div>
<script src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
<script>
  /*Vue对象相当于是MVVM设计模式中的VM视图模型
  * 该对象负责将页面中的元素和某个变量进行绑定,并且Vue会在内存中不断监听着
  * 变量值的改变,当变量值发生改变时Vue框架会自动找到页面中的元素
  * 让其跟着发生改变*/
let v = new Vue({
  el:"body>div",  //element元素, 写一个选择器用来设置Vue框架的管理范围
  data:{ //data里面定义和页面相关的变量,定义完之后Vue会对变量进行监听
    info:"Hello Vue!"
  },methods:{//绑定方法
      
  }
})
</script>
</body>
</html>
```



## 6 Vue相关指令[^3]

| 相关指令                                                     | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| {{变量}}                                                     | 插值, 让当前位置的文本内容和变量进行绑定                     |
| v-text="变量"                                                | 让元素的**文本内容**和变量进行绑定                           |
| v-html="变量"                                                | 让元素的**标签内容**和变量进行绑定                           |
| <font color=red>v-bind:属性名="变量"</font>\|\|  **:属性名="变量"** | 让元素的**某个属性**的值和变量进行绑定                       |
| **v-model="变量"**                                           | **让控件的值和变量进行双向绑定<br />**<br />双向绑定: 控件的值和变量进行绑定, 变量发生改变时控件的值跟着变, 同时控件的值发生改变时变量也会跟这变 |
| v-on:事件名 \|\| **@事件名="方法"**                          | 让元素的某个事件和Vue中的方法进行绑定                        |
| **v-for** = 变量名 in arr ， **v-for** = (value,key,index) in obj | v-for 可以绑定**数组遍历**，遍历数组元素，也可以将对象做为一个数组，**遍历对象**中的属性元素 |
| **v-if** = boolean && **v-else-if** = boolean && **v-else**  | 基于表达式值的真假性，来条件性地**渲染**元素或者模板片段 （**控制元素显隐**） |
| **v-show = boolean**                                         | 让元素是否显示和变量进行绑定, true显示, false不显示(隐藏元素) |

### 6.1 文本相关指令

- **{{变量}}**:  
  - 插值, 让当前位置的文本内容和变量进行绑定

- **v-text="变量"**; 
  - 让元素的文本内容和变量进行绑定

- **v-html="变量"**; 

  - 让元素的标签内容和变量进行绑定

  ```HTML
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div>
      <!--{{变量}}插值,让当前位置的文本内容和变量进行绑定-->
      {{info}}
      <p>{{info}}</p>
      <!--v-text="变量" 让元素的文本内容和变量进行绑定-->
      <p v-text="info"></p>
      <!--v-html="变量" 让元素的标签内容和变量进行绑定-->
      <p v-html="info"></p>
  </div>
  <!--从本地引入vue.js框架文件-->
  <script src="js/vue.min.js"></script>
  <script>
      let v = new Vue({
          el: "body>div",
          data: {
              info: "文本相关指令测试<b>加粗标签</b>"
          }
      })
  </script>
  
  </body>
  </html>
  ```

### 6.2 属性绑定

- **v-bind:属性名="变量"**  

- **:属性名="变量"** 

  -  让元素的某个属性的值和变量进行绑定

  ```HTML
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div>
      {{msg}}
      <!--:属性名="变量" 让某个属性的值和变量进行绑定-->
      <input type="text" :value="msg">
      <!--属性绑定的复杂写法,如果没有安装vue插件会报错,
      在错误上面alt+回车进行修复-->
      <input type="text" v-bind:value="msg">
      <a :href="url">超链接</a>
      <img :src="imgUrl" alt="">
  </div>
  <script src="js/vue.min.js"></script>
  <script>
      let v = new Vue({
          el: "body>div",
          data: {
              msg: "属性绑定测试",
              url:"http://www.baidu.com",
              imgUrl:"a.jpg"
          }
      })
  </script>
  </body>
  </html>
  ```

- 当属性的值是个变量时，必须添加属性绑定，如果属性后面跟的是常量，不需要绑定[^4]

  - 属性后面跟常量

    ```HTML
    <el-option label="北京" value="bj"></el-option>
    <el-option label="上海" value="sh"></el-option>
    ```

  - 属性后面跟变量

    ```html
     <el-option v-for="p in arr"
                       :label="p.title" :value="p.price"></el-option>
    ```

### 6.3 双向绑定

- **v-model="变量"**
  - 让控件的值和变量进行双向绑定, 
- 双向绑定: 控件的值和变量进行绑定, 变量发生改变时控件的值跟着变, 同时控件的值发生改变时变量也会跟这变

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div>
  {{info}}
  <!--v-model="变量" 让控件的值和变量进行双向绑定
  变量值改变会影响页面,页面的改变也会影响变量-->
  <input type="text" v-model="info">
  <hr>
  用户名:<input type="text" v-model="user.username">
  密码:<input type="text" v-model="user.password">
</div>
<script src="js/vue.min.js"></script>
<script>
  let v = new Vue({
    el:"body>div",
    data:{
      info:"双向绑定测试",
      user:{username:"",password:""}
    }
  })
</script>

</body>
</html>
```

### 6.4 事件绑定

- **v-on:**事件名="方法"; 

- **@**事件名="方法";   

  - 让元素的某个事件和Vue中的方法进行绑定

  ```HTML
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div>
      {{info}}
      <!--@事件名="方法" 让元素的某个事件和方法进行绑定-->
      <input type="button" value="按钮1" @click="f()">
      <input type="button" value="按钮2" v-on:click="f()">
  </div>
  <script src="js/vue.min.js"></script>
  <script>
      let v = new Vue({
          el: "body>div",
          data: {
              info: "事件绑定测试"
          },
          methods: {
              f(){
                  alert("按钮点击了!");
              }
          }
      })
  </script>
  </body>
  </html>
  ```

### 6.5 循环绑定

- v-for作用

  - 循环遍历指令, 遍历的同时生成当前元素, 用法类似于Java的新循环

- 对象/数组准备

  ```javascript
  let v = new Vue({
          el:"body>div",
          data:{
              arr:[{name:"夏弥","age":18},{name:"绘梨衣","age":21}],
              obj:{name:"夏弥","age":18}
          },
          methods:{
  
          }
      });
  ```

- 遍历数组

  - **v-for = 变量名 in arr**

    - 遍历数组里面的值

  - **v-for = (变量名，index) in arr**

    - 遍历数组里面的值，并且显示下标

    ```javascript
    <table border="1px">
            <tr>
                <td>姓名</td>
                <td>年龄</td>
            </tr>
            <tr v-for="p in arr">
                <td>{{p.name}}</td>
                <td>{{p.age}}</td>
            </tr>
            <tr v-for="(p,index) in arr">
                <td>{{index}}:{{p.name}}</td>
            </tr>
        </table>
    ```

- 遍历对象

  - > > **value[属性值]** == **key[属性字段名]** ===**index[属性下标]**
    > >
    > > 可以通过不同写法，获取不同需要显示的值

  - **v-for = value in arr**

    - 遍历对象里面的值

  - **v-for = (value,key) in arr**

    - 遍历对象值 与 属性字段名

  - **v-for = (value,key,index) in arr**

    - 遍历显示值 属性字段名 下标

    ```javascript
     <table border="1px">
            <tr v-for="(value,key,index) in obj">
                <!-- 可以获取这三个值 -->
                <td>{{index}}:{{key}}:{{value}}</td>
            </tr>
        </table>
    ```

### 6.6  显隐绑定

-  **渲染绑定**

  - 如果条件判断为false，标签内容不进行加载进html，如果已经存在则会对标签进行删除

  - **v-if | v-else-if | v-else**的使用

    - 可以实现多条件判断当前标签的显隐情况

      ```javascript
      <div v-if="type === 'A'">
        A
      </div>
      <div v-else-if="type === 'B'">
        B
      </div>
      <div v-else-if="type === 'C'">
        C
      </div>
      <div v-else>
        Not A/B/C
      </div>
      
      ```

- **显隐display**

  - 如果条件判断为false，则设置标签的display为none

  - **v-show**		

    - 实现if-else的俩路分支显隐判断

      ```javascript
      <h1 v-show="ok">Hello!</h1>
      ```

- **v-if 与 v-show 区别**

  - `v-if` 是“真实的”按条件渲染，因为它确保了在切换时，条件区块内的事件监听器和子组件都会被销毁与重建。

  - `v-if` 也是**惰性**的：如果在初次渲染时条件值为 false，则不会做任何事。条件区块只有当条件首次变为 true 时才被渲染。

  - 相比之下，`v-show` 简单许多，元素无论初始条件如何，始终会被渲染，只有 CSS `display` 属性会被切换。

  - 总的来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要频繁切换，则使用 `v-show` 较好；如果在运行时绑定条件很少改变，则 `v-if` 会更合适。





































