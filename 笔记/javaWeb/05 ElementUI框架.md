# ElementUI框架

## 目录导航

| 目录                         | 描述                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| 0 容易遗忘内容               | 记录容易忘记、容易犯错问题点                                 |
| 1 ElementUI文档地址          | 官网与API文档地址 查看 [ElementUI官网      ElementUI文档](https://element.eleme.cn/#/zh-CN/component/layout) |
| 2 ElementUI开发插件安装      | IDEA中安装element插件 便于快捷开发ElementUI                  |
| **3 HelloEUI 模板搭建**      | 第一个ElementUI 模板代码                                     |
| 4 **ElementUI 相关功能组件** | 常用的ElementUI 组件 、及用途 用于实现页面效果 **及相应组件所在的官网地址** |
| 5 实现代码                   | 简单演示一下相关组件功能的应用，具体使用参照官网             |
| 6 **酷鲨商城页面**           | 使用ElementUI制作酷鲨商城页面                                |



## 0 容易遗忘内容

[^1]: 组件表格中记录了各组件实现的功能 及 官网手册所对应的地址，可以便捷查询相应组件内容
[^2]: table表格在定义循环数组以外的属性列时，如何进行自定义
[^3]: 酷鲨商城主页面设计时，所遇到的问题







## 1 ElementUI文档地址

- [ElementUI官网](https://element.eleme.cn/#/zh-CN)
- [ElementUI文档](https://element.eleme.cn/#/zh-CN/component/layout)



## 2 ElementUI开发插件安装

- IDEA File -》setting -》plugins 搜索element进行插件安装
- 该插件的作用
  - 可以默认给你搭建element框架，在写标签的时候，里面内嵌element标签，便捷开发

![image-20221208164858502](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221208164858502.png)

## 3 HelloEUI 模板搭建

- 根据官网上面的手册 可以从unpkg.com里面引入 但可能存在网络延迟

  ```HTML
  <!-- 引入样式 -->
  <link rel="stylesheet" href="https://unpkg.com/element-ui/lib/theme-chalk/index.css">
  <!-- 引入组件库 -->
  <script src="https://unpkg.com/element-ui/lib/index.js"></script>
  ```

  

-  **所以采用在cdn服务器引入方式**

  ```HTML
  <!-- 引入样式 -->
  <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
  <!-- 引入组件库 -->
  <script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
  <!-- 引入VUE -->
  <script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
  ```



- ​	<font color=red size=5>**HelloEUI模板**</font> (后续element组件的开发，可以直接在当前基础模板上开发)

  ```HTML
  <!DOCTYPE html>
  <html>
  <head>
      <meta charset="UTF-8">
      <!-- import CSS -->
      <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
  </head>
  <body>
  <div id="app">
  
  </div>
  </body>
  <!-- import Vue before Element -->
  <script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
  <!-- import JavaScript -->
  <script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
  <script>
      let v = new Vue({
          el: '#app',
          data: function () {
              return {}
          },
          methods:{
  
          }
      })
  </script>
  </html>
  ```

  

## 4 ElementUI 相关功能组件 [^1]

- 前述
  - 可以把里面的组件理解为拼图，你的页面需要搭建什么功能，就去官网查询对应组件，进行拼装，具体组件内容详见官网 [ElemetUI文档](https://element.eleme.cn/#/zh-CN/component/layout)

​	

| 组件功能                | 描述                                                         | 官网手册地址                                                 |
| ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 01 Button 按钮          | 支持各种类型按钮的自定义样式                                 | [Button 按钮](https://element.eleme.cn/#/zh-CN/component/button) |
| 02 Divider 分割线       | 垂直分割线 \| 水平分割线 -------- \| 分割线上自定义内容      | [Divider 分割线](https://element.eleme.cn/#/zh-CN/component/divider) |
| 03 Message 消息提示     | **主动点击某一标签**元素时，需要在页面上弹出多种样式提示信息， | [Message 消息提示](https://element.eleme.cn/#/zh-CN/component/message) |
| 04 Dropdown下拉菜单     | 将动作或菜单折叠到**下拉菜单**中,通过不同提供事件来触发下拉菜单 | [Dropdown下拉菜单](https://element.eleme.cn/#/zh-CN/component/dropdown) |
| 05 **Select 选择器**    | **中规中距**的下拉菜单选择器 支持设置选择器的状态            | [Select 选择器](https://element.eleme.cn/#/zh-CN/component/select) |
| 06 **Table 表格**       | 用于展示多条结构类似的数据，支持多种样式表格                 | [Table 表格](https://element.eleme.cn/#/zh-CN/component/table#biao-wei-he-ji-xing) |
| 07 Carousel **走马灯**  | 在有限空间内 **循环播放**同一类型的图片、文字等内容          | [ Carousel 走马灯](https://element.eleme.cn/#/zh-CN/component/carousel#carousel-attributes) |
| 08 **NavMenu 导航菜单** | 为网站提供**导航功能的菜单**  ，例如页面上方的导航窗口，支持导航栏点击事件自定义等 | [NavMenu 导航菜单](https://element.eleme.cn/#/zh-CN/component/menu) |
| 09 Layout 布局          | **当前父元素基础24分栏 ，对当行进行创建布局 类似于之前的DIV布局** | [ Layout 布局](https://element.eleme.cn/#/zh-CN/component/layout) |
| 10 Container 布局容器   | 用于整体页面布局 分为`header`顶栏容器,`aside`侧边栏容器,`main`主要区域容器,`footer`底栏容器 | [Container 布局容器](https://element.eleme.cn/#/zh-CN/component/container) |
| 11 Card 卡片            | 将原本的信息展示 用类似于**卡片效果包裹显示**出来            | [Card](https://element.eleme.cn/#/zh-CN/component/card)      |
| 12 Icon 图标            | 提供一套常用图标集合 图片大小受字体影响，为字体图标          | [Icon 图标](https://element.eleme.cn/#/zh-CN/component/icon) |
| 13 **Form 表单**        | 由输入框、选择器、单选框、多选框等控件组成，用以收集、校验、提交数据 | [Form 表单](https://element.eleme.cn/#/zh-CN/component/form#form-item-methods) |
| 14 input 输入框         | 输入框类型组件 提供**多种输入框样式**                        | [input 输入框](https://element.eleme.cn/#/zh-CN/component/input#autocomplete-methods) |

## 5 实现代码

### 01 Button 按钮

<el-button>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">

    <el-row>
        <el-button>默认按钮</el-button>
        <el-button type="primary">主要按钮</el-button>
        <el-button type="success">成功按钮</el-button>
        <el-button type="info">信息按钮</el-button>
        <el-button type="warning">警告按钮</el-button>
        <el-button type="danger">危险按钮</el-button>
    </el-row>

    <el-row>
        <el-button plain>朴素按钮</el-button>
        <el-button type="primary" plain>主要按钮</el-button>
        <el-button type="success" plain>成功按钮</el-button>
        <el-button type="info" plain>信息按钮</el-button>
        <el-button type="warning" plain>警告按钮</el-button>
        <el-button type="danger" plain>危险按钮</el-button>
    </el-row>

    <el-row>
        <el-button round>圆角按钮</el-button>
        <el-button type="primary" round>主要按钮</el-button>
        <el-button type="success" round>成功按钮</el-button>
        <el-button type="info" round>信息按钮</el-button>
        <el-button type="warning" round>警告按钮</el-button>
        <el-button type="danger" round>危险按钮</el-button>
    </el-row>

    <el-row>
        <el-button icon="el-icon-search" circle></el-button>
        <el-button type="primary" icon="el-icon-edit" circle></el-button>
        <el-button type="success" icon="el-icon-check" circle></el-button>
        <el-button type="info" icon="el-icon-message" circle></el-button>
        <el-button type="warning" icon="el-icon-star-off" circle></el-button>
        <el-button type="danger" icon="el-icon-delete" circle></el-button>
    </el-row>

    <el-button type="primary">查看详情</el-button>
    <el-button type="success" plain>查看详情</el-button>
    <el-button type="danger" round>查看详情</el-button>
    <el-button type="info" icon="el-icon-info" circle></el-button>
    <hr>
    <!--i标签是斜体的意思但是用来做图标主要是因为icon单词的首字母是i-->
    <i class="el-icon-edit"></i>
    <b class="el-icon-edit"></b>
    <a class="el-icon-edit"></a>
    <span class="el-icon-edit"></span>
    <!--因为图标的大小颜色 受字体影响,所以又称为字体图标-->
    <i style="color: red;font-size: 30px" class="el-icon-share"></i>
    <i class="el-icon-delete"></i>
    <el-button type="primary" icon="el-icon-search">搜索</el-button>
    <i class="el-icon-chat-line-round">消息</i>

</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {}
        },
        methods:{

        }
    })
</script>
</html>
```

### 02 Divider 分割线

<el-divider>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">

    <div>
        <span>青春是一个短暂的美梦, 当你醒来时, 它早已消失无踪</span>
        <el-divider></el-divider>
        <span>少量的邪恶足以抵消全部高贵的品质, 害得人声名狼藉</span>
    </div>
    <div>
        <span>青春是一个短暂的美梦, 当你醒来时, 它早已消失无踪</span>
        <hr>
        <span>少量的邪恶足以抵消全部高贵的品质, 害得人声名狼藉</span>
    </div>
    <template>
        <div>
            <span>头上一片晴天，心中一个想念</span>
            <el-divider content-position="left">少年包青天</el-divider>
            <span>饿了别叫妈, 叫饿了么</span>
            <el-divider><i class="el-icon-mobile-phone"></i></el-divider>
            <span>为了无法计算的价值</span>
            <el-divider content-position="right">阿里云</el-divider>
        </div>
    </template>

    <template>
        <div>
            <span>雨纷纷</span>
            <el-divider direction="vertical"></el-divider>
            <span>旧故里</span>
            <el-divider direction="vertical"></el-divider>
            <span>草木深</span>
        </div>
    </template>

</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {}
        },
        methods: {}
    })
</script>
</html>
```

### 03 Message 消息提示

<el-button :plain="true" @click="open2">成功</el-button>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">
    <template>
        <el-button :plain="true" @click="open2">成功</el-button>
        <el-button :plain="true" @click="open3">警告</el-button>
        <el-button :plain="true" @click="open1">消息</el-button>
        <el-button :plain="true" @click="open4">错误</el-button>
    </template>

</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {}
        },
        methods:{
            open1() {
                this.$message('这是一条消息提示');
            },
            open2() {
                // this.$message({
                //     message: '恭喜你，这是一条成功消息',
                //     type: 'success'
                // });
                //this代表当前Vue对象  和变量v指向同一个对象
                v.$message.success("成功消息!");
            },

            open3() {
                this.$message({
                    message: '警告哦，这是一条警告消息',
                    type: 'warning'
                });
            },

            open4() {
                this.$message.error('错了哦，这是一条错误消息');
            }
        }
    })
</script>
</html>
```

### 04 Dropdown下拉菜单

<el-dropdown-menu slot="dropdown">

-- <el-dropdown-item command="狮子头">

----

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
    <style>
        .el-dropdown-link {
            cursor: pointer;
            color: #409EFF;
        }

        .el-icon-arrow-down {
            font-size: 12px;
        }
    </style>
</head>
<body>
<div id="app">
    <h1>{{info}}</h1>
    <el-dropdown @command="handleCommand">
  <span class="el-dropdown-link">
    下拉菜单<i class="el-icon-arrow-down el-icon--right"></i>
  </span>
        <el-dropdown-menu slot="dropdown">
            <el-dropdown-item command="黄金糕">黄金糕</el-dropdown-item>
            <el-dropdown-item command="狮子头">狮子头</el-dropdown-item>
            <el-dropdown-item command="螺蛳粉">螺蛳粉</el-dropdown-item>
            <el-dropdown-item disabled command="双皮奶">双皮奶</el-dropdown-item>
            <el-dropdown-item divided command="蚵仔煎">蚵仔煎</el-dropdown-item>
        </el-dropdown-menu>
    </el-dropdown>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {
                info:""
            }
        },
        methods: {
            handleCommand(command){
                //command代表传递过来的指令,也就是点击菜单项对应的指令
                v.info=command;
            }
        }
    })
</script>
</html>
```

### 05 **Select 选择器**

<el-select>

​	 <el-option>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">
    <template>
        <el-select v-model="value" placeholder="请选择">
            <!--label显示给用户看的内容
            value设置的是选中后得到的值-->
            <el-option
                    v-for="item in options"
                    :label="item.label"
                    :value="item.value">
            </el-option>
        </el-select>
    </template>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {
                options: [{
                    value: '选项1',
                    label: '黄金糕'
                }, {
                    value: '选项2',
                    label: '双皮奶'
                }, {
                    value: '选项3',
                    label: '蚵仔煎'
                }, {
                    value: '选项4',
                    label: '龙须面'
                }, {
                    value: '选项5',
                    label: '北京烤鸭'
                }],
                value: ''
            }
        },
        methods:{

        }
    })
</script>
</html>
```

### 06 **Table 表格**[^2]

​	<el-table>

​		<el-table-column>

注意点:

​	如果表格列中的内容不是对象数组属性而是自定义效果，需要按照固定写法进行编写列

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">
    <input type="text" v-model="emp.name"  placeholder="员工姓名">
    <input type="text" v-model="emp.salary" placeholder="员工工资">
    <input type="text" v-model="emp.job" placeholder="员工工作">
    <input type="button" value="添加" @click="add()">
    <el-table :data="arr">
        <el-table-column prop="name" label="姓名" width="200"></el-table-column>
        <el-table-column prop="salary" label="工资" width="200"></el-table-column>
        <el-table-column prop="job" label="工作" width="200"></el-table-column>
        <!--如果表格列里面的内容不是对象数组的属性而是自定义的效果,
        需要按照文档中提供的这种固定写法-->
        <el-table-column label="操作" width="200">
            <!--自定义列必须添加template标签 以及slot-scope="scope"
            scope是定义的一个变量名称, 此变量里面装着当前行的相关信息
            scope.$index当前行对应的数组下标
            scope.row当前行对应的数组里面的对象
            -->
            <template slot-scope="scope">
                <el-button
                        size="mini"
                        type="danger"
                        @click="handleDelete(scope.$index, scope.row)">删除</el-button>
            </template>
        </el-table-column>
    </el-table>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {
                emp:{name:"",salary:"",job:""},
                arr:[{name:"刘备",salary:"3000",job:"销售"},
                    {name:"关羽",salary:"4000",job:"人事"},
                    {name:"张飞",salary:"5000",job:"程序员"}]
            }
        },
        methods: {
            handleDelete(i,emp){
              //i代表删除的下标  emp代表删除的对象
              v.arr.splice(i,1);
              v.$message("删除了"+emp.name);
            },
            add(){
                v.arr.push({name:v.emp.name,salary:v.emp.salary,
                    job:v.emp.job})
            }
        }
    })
</script>
</html>
```



### 07 Carousel **走马灯**

 <el-carousel>

​	<el-carousel-item>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">
    <div style="width: 500px">
        <el-carousel height="150px">
            <el-carousel-item>
                <img src="imgs/b1.jpg" width="100%" height="100%">
            </el-carousel-item>
            <el-carousel-item>
                <img src="imgs/b2.jpg" width="100%" height="100%">
            </el-carousel-item>
            <el-carousel-item>
                <img src="imgs/b3.jpg" width="100%" height="100%">
            </el-carousel-item>
        </el-carousel>
    </div>
    <h1>商品走马灯</h1>
    <div style="width: 300px">
        <el-carousel height="300px">
            <el-carousel-item v-for="url in arr">
                <!--只要属性中出现了变量则必须加上: 变成属性绑定-->
                <img :src="url" width="100%" height="100%">
            </el-carousel-item>
        </el-carousel>
    </div>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {
                arr:["imgs/a.jpg","imgs/b.jpg","imgs/c.jpg"]
            }
        },
        methods:{

        }
    })
</script>
</html>
```

### 08 **NavMenu 导航菜单**

   <el-menu>

​	<el-menu-item>

​	<el-submenu>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">
    <!--:default-active设置默认激活位置
    mode="horizontal"设置横向导航菜单 默认值为纵向
    @select添加选择事件 ,当选择了某一项时触发此事件
    -->
    <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal"
             @select="handleSelect">
        <!--el-menu-item菜单项-->
        <el-menu-item index="1">处理中心</el-menu-item>
        <!--el-submenu设置子菜单-->
        <el-submenu index="2">
            <!--设置子菜单的标题-->
            <template slot="title">我的工作台</template>
            <el-menu-item index="2-1">选项1</el-menu-item>
            <el-menu-item index="2-2">选项2</el-menu-item>
            <el-menu-item index="2-3">选项3</el-menu-item>
            <el-submenu index="2-4">
                <template slot="title">选项4</template>
                <el-menu-item index="2-4-1">选项1</el-menu-item>
                <el-menu-item index="2-4-2">选项2</el-menu-item>
                <el-menu-item index="2-4-3">选项3</el-menu-item>
            </el-submenu>
        </el-submenu>
        <!--disabled 禁用-->
        <el-menu-item index="3" disabled>消息中心</el-menu-item>
        <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
    </el-menu>
    <div class="line"></div>
    <!--
    background-color背景颜色
    text-color文本颜色
    active-text-color 激活文本颜色
    -->
    <el-menu
            :default-active="activeIndex2"
            class="el-menu-demo"
            mode="horizontal"
            @select="handleSelect"
            background-color="#545c64"
            text-color="#fff"
            active-text-color="#ffd04b">
        <el-menu-item index="1">处理中心</el-menu-item>
        <el-submenu index="2">
            <template slot="title">我的工作台</template>
            <el-menu-item index="2-1">选项1</el-menu-item>
            <el-menu-item index="2-2">选项2</el-menu-item>
            <el-menu-item index="2-3">选项3</el-menu-item>
            <el-submenu index="2-4">
                <template slot="title">选项4</template>
                <el-menu-item index="2-4-1">选项1</el-menu-item>
                <el-menu-item index="2-4-2">选项2</el-menu-item>
                <el-menu-item index="2-4-3">选项3</el-menu-item>
            </el-submenu>
        </el-submenu>
        <el-menu-item index="3" disabled>消息中心</el-menu-item>
        <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
    </el-menu>
    <h1>自定义导航菜单</h1>
    <el-menu :default-active="activeIndex" mode="horizontal"
    background-color="#0aa1ed" text-color="#fff"
    active-text-color="#0f0" @select="handleSelect">
        <el-menu-item index="1">首页</el-menu-item>
        <el-menu-item index="2">精彩活动</el-menu-item>
        <el-menu-item index="3">精品女装</el-menu-item>
        <el-menu-item index="4">品牌男装</el-menu-item>
        <el-menu-item index="5">母婴产品</el-menu-item>
        <el-menu-item index="6">数码科技</el-menu-item>
    </el-menu>
    <h1>侧边栏</h1>
    <div style="width: 300px;height: 600px;background-color: #666">
        <el-menu>
            <el-menu-item index="1">
                <i class="el-icon-menu"></i>
                <!--slot="title"设置当前文本为标题-->
                <span slot="title">导航一</span>
            </el-menu-item>
            <el-menu-item index="2">
                <i class="el-icon-edit"></i>
                <span slot="title">导航二</span>
            </el-menu-item>
            <el-submenu index="3">
                <template slot="title">
                    <i class="el-icon-delete"></i>
                    <span>导航三</span>
                </template>
                <el-menu-item index="3-1">aaa</el-menu-item>
                <el-menu-item index="3-2">bbb</el-menu-item>
                <el-menu-item index="3-3">ccc</el-menu-item>
            </el-submenu>
        </el-menu>
    </div>

</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {
                activeIndex: '3',
                activeIndex2: '1'
            }
        },
        methods:{
            handleSelect(key, keyPath) {
                //key对应的就是菜单项的index
                //keyPath 是一个数组,数组里面装的是完整路径

                //2-4-1   key=2-4-1  keyPath=["2","2-4","2-4-1"]

                console.log(key, keyPath);
            }
        }
    })
</script>
</html>
```

### 09 Layout 布局

<el-row>

<el-col>

<!--gutter设置间距 span设置所占分栏数 offset设置偏移列数-->

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
    <style>
        .c1{
            border: 1px solid red;
            height: 30px; border-radius: 5px;
        }
    </style>
</head>
<body>
<div id="app">
    <!--el-row表示一行-->
    <el-row>
        <!--el-col表示一列 一行最多24分栏
		一列满了就直接换一行-->
        <el-col span="12"><div class="c1"></div></el-col>
        <el-col span="12"><div class="c1"></div></el-col>
    </el-row>
    <el-row>
        <el-col span="8"><div class="c1"></div></el-col>
        <el-col span="8"><div class="c1"></div></el-col>
        <el-col span="8"><div class="c1"></div></el-col>
    </el-row>
    <el-row>
        <el-col span="16"><div class="c1"></div></el-col>
        <el-col span="8"><div class="c1"></div></el-col>
    </el-row>
     <!--设置居中-->
    <div style="width: 1200px;margin: 0 auto">
        <!--gutter设置间距-->
        <el-row gutter="20">
            <el-col span="16"><div class="c1"></div></el-col>
            <el-col span="8"><div class="c1"></div></el-col>
        </el-row>
    </div>
    <h1>1:3:1:1  居中 10像素的间距</h1>
    <div style="width: 1200px;margin: 0 auto">
       <el-row gutter="10">
           <el-col span="4"><div class="c1"></div></el-col>
           <el-col span="12"><div class="c1"></div></el-col>
           <el-col span="4"><div class="c1"></div></el-col>
           <el-col span="4"><div class="c1"></div></el-col>
       </el-row>
    </div>
    <h1>列偏移</h1>
    <el-row>
        <!--offset设置偏移的列数-->
        <el-col span="20" offset="4"><div class="c1"></div></el-col>
    </el-row>
    <el-row gutter="20">
        <el-col span="6"><img src="imgs/a.jpg" width="100%"></el-col>
        <el-col span="6"><img src="imgs/b.jpg" width="100%"></el-col>
        <el-col span="6"><img src="imgs/c.jpg" width="100%"></el-col>
        <el-col span="6"><img src="imgs/d.jpg" width="100%"></el-col>
    </el-row>

</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {}
        },
        methods:{

        }
    })
</script>
</html>
```

### 10 Container 布局容器

 <el-container> <el-header> <el-aside> <el-main> <el-footer>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
    <style>
        .el-header{background-color: red;}
        .el-main{
            background-color: green;
            height: 500px;
        }
        .el-footer{background-color: blue;}
    </style>
</head>
<body>
<div id="app">
    <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
        <el-footer>Footer</el-footer>
    </el-container>
    <h1>上,下(左,右)</h1>
    <el-container>
        <el-header>Header</el-header>
        <el-container>
            <el-aside width="200px">Aside</el-aside>
            <el-main>Main</el-main>
        </el-container>
    </el-container>
    <h1>左,右(上,中,下)</h1>
    <el-container>
        <el-aside width="200px">Aside</el-aside>
        <el-container>
            <el-header>Header</el-header>
            <el-main>Main</el-main>
            <el-footer>Footer</el-footer>
        </el-container>
    </el-container>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {}
        },
        methods:{

        }
    })
</script>
</html>
```

### 11 Card 卡片

<el-card>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
</head>
<body>
<div id="app">
    <div style="width: 1200px;margin: 0 auto">
        <el-row gutter="10">
            <!--v-for="i in 4"重复生成4次-->
            <el-col span="6" v-for="i in 4">
                <el-card>
                    <img src="imgs/a.jpg" width="100%">
                </el-card>
            </el-col>
        </el-row>
    </div>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {}
        },
        methods:{

        }
    })
</script>
</html>
```

### 12 Icon 图标

<i class="el-icon-edit"></i>

```html
<!--i标签是斜体的意思但是用来做图标主要是因为icon单词的首字母是i-->
<i class="el-icon-edit"></i>
<b class="el-icon-edit"></b>
<a class="el-icon-edit"></a>
<span class="el-icon-edit"></span>
<!--因为图标的大小颜色 受字体影响,所以又称为字体图标-->
<i style="color: red;font-size: 30px" class="el-icon-share"></i>
<i class="el-icon-delete"></i>
<el-button type="primary" icon="el-icon-search">搜索</el-button>
<i class="el-icon-chat-line-round">消息</i>
```



### 13 **Form 表单**

<el-form> <el-form-item>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
    <style>
        body{
            margin: 0;/*去掉自带的8个像素外边距*/
            background-image: url("imgs/bg.jpg");
            background-size: cover; /*设置背景为封面*/
            text-align: center;
        }
        h1{
            font-size: 72px;
            color: #0096dc;
            margin-bottom: 0;/*去掉下外边距*/
        }
        img{width: 100px}
        h2{
            font-size: 32px;
            color: #0096dc;
            margin-bottom: 0;
        }
    </style>
</head>
<body>
<div id="app">
    <h1>欢迎来到酷鲨商城</h1>
    <img src="imgs/shark.png" alt="">
    <h2>CoolSharkMall</h2>
    <el-card style="width: 600px;height: 300px;
    margin: 0 auto;background-color: rgba(255,255,255,0.3)">
        <!--label-width="55px" 让lable和文本框显示在一行之内-->
        <el-form label-width="55px" style="width: 400px;margin: 50px auto">
            <el-form-item label="用户名">
                <el-input type="text" placeholder="请输入用户名"></el-input>
            </el-form-item>
            <el-form-item label="密码">
                <el-input type="password" placeholder="请输入密码"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary"
                           style="position:relative;right: 23px">登录</el-button>
            </el-form-item>
        </el-form>
    </el-card>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {}
        },
        methods:{

        }
    })
</script>
</html>
```



## 6、酷鲨商城页面设计

### 01 登录页面 login

- 效果图:

​	<img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221209154812712.png" alt="image-20221209154812712" style="zoom:50%;" />

- 实现代码:

  - 涉及组件
    - 卡片、表单、按钮

  ```HTML
  <!DOCTYPE html>
  <html>
  <head>
      <meta charset="UTF-8">
      <!-- import CSS -->
      <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
      <style>
          body{
              margin: 0;/*去掉自带的8个像素外边距*/
              background-image: url("imgs/bg.jpg");
              background-size: cover; /*设置背景为封面*/
              text-align: center;
          }
          h1{
              font-size: 72px;
              color: #0096dc;
              margin-bottom: 0;/*去掉下外边距*/
          }
          img{width: 100px}
          h2{
              font-size: 32px;
              color: #0096dc;
              margin-bottom: 0;
          }
      </style>
  </head>
  <body>
  <div id="app">
      <h1>欢迎来到酷鲨商城</h1>
      <img src="imgs/shark.png" alt="">
      <h2>CoolSharkMall</h2>
      <el-card style="width: 600px;height: 300px;
      margin: 0 auto;background-color: rgba(255,255,255,0.3)">
          <!--label-width="55px" 让lable和文本框显示在一行之内-->
          <el-form label-width="55px" style="width: 400px;margin: 50px auto">
              <el-form-item label="用户名">
                  <el-input type="text" placeholder="请输入用户名"></el-input>
              </el-form-item>
              <el-form-item label="密码">
                  <el-input type="password" placeholder="请输入密码"></el-input>
              </el-form-item>
              <el-form-item>
                  <el-button type="primary"
                             style="position:relative;right: 23px">登录</el-button>
              </el-form-item>
          </el-form>
      </el-card>
  </div>
  </body>
  <!-- import Vue before Element -->
  <script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
  <!-- import JavaScript -->
  <script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
  <script>
      let v = new Vue({
          el: '#app',
          data: function () {
              return {}
          },
          methods:{
  
          }
      })
  </script>
  </html>
  ```

​	

### 02 主页面 index

- 效果图

- ![image-20221209155558255](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221209155558255.png)

- 实现代码

  - 涉及组件

    - Container布局容器
    - Layout布局
    - Card 卡片
    - NavMenu 导航菜单
    - table 表格
    - Carousel 走马灯
    - input 输入框带图片

  - 了解所学点[^3]

    - 1、元素标签占行占块(**在审视标签组成时，从空间分布**)
      - div单独占一块、p、标题单独占一行、span为行内元素、img为行内块元素，与其他元素共占一行。
    - 2、img图片设置的时候 需要自行设置高度，不设置为自身默认大小，不适合
    - 3、margin 0 auto 需要居中的元素，需要表明待居中元素的宽度，如果没有设定，可能默认为百分百，已经撑满了
    - 4、el-row 分栏标签 一行 分为24个基本块 如果在里面进行循环数组时，超过一行会自动换行还是按照24基本块算
      - 所以可以在 <el-row>标签里面的<el-col>进行循环

  - 编写思路

    - 1、了解页面中所使用的组件
    - 2、学会灵活使用标签的包含关系 (俩个挨在一起的文字，可以用统一标签包含)
    - 3、将页面进行分块分区，灵活使用组件进行拼接
    - 4、对组件的内容进行细致书写描述

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <!-- import CSS -->
        <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
        <style>
            .el-header img{
                vertical-align: middle;/*中间对齐*/
            }
            .el-header a{
                color: #666;
                text-decoration: none;
            }
            /*去除内边距*/
            .el-table .el-table__cell{
                padding: 0;
            }
        </style>
    </head>
    <body>
    <div id="app">
        <el-container>
            <el-header height="150px">
                <div style="width: 1200px;margin: 0 auto">
                    <img src="imgs/logo.png" width="300" alt="">
                    <a href="">首页</a><el-divider direction="vertical"></el-divider>
                    <a href="">热点资讯</a><el-divider direction="vertical"></el-divider>
                    <a href="">商家入驻</a><el-divider direction="vertical"></el-divider>
                    <a href="">社会招聘</a><el-divider direction="vertical"></el-divider>
                    <a href="">校园招聘</a><el-divider direction="vertical"></el-divider>
                    <a href="">帮助</a>
                </div>
                <div style="background-color: #0aa1ed">
                    <el-menu style="width: 1200px;margin: 0 auto" mode="horizontal"
                             background-color="#0aa1ed" text-color="#fff"
                             active-text-color="#0f0" @select="handleSelect">
                        <el-menu-item index="1">精彩活动</el-menu-item>
                        <el-menu-item index="2">精品女装</el-menu-item>
                        <el-menu-item index="3">品牌男装</el-menu-item>
                        <el-menu-item index="4">母婴产品</el-menu-item>
                        <el-menu-item index="5">数码科技</el-menu-item>
                        <div style="float: right;position:relative;top:10px">
                            <el-input type="text" placeholder="请输入搜索的内容">
                                <!--slot="append"设置搜索按钮嵌入到文本框里面-->
                                <el-button slot="append" icon="el-icon-search"></el-button>
                            </el-input>
                        </div>
                    </el-menu>
                </div>
            </el-header>
            <el-main style="width: 1200px;margin: 0 auto">
                <el-row gutter="20">
                    <el-col span="18">
                        <!--走马灯开始-->
                        <el-carousel height="300px">
                            <el-carousel-item>
                                <img src="imgs/b1.jpg" width="100%" height="100%">
                            </el-carousel-item>
                            <el-carousel-item>
                                <img src="imgs/b2.jpg" width="100%" height="100%">
                            </el-carousel-item>
                            <el-carousel-item>
                                <img src="imgs/b3.jpg" width="100%" height="100%">
                            </el-carousel-item>
                        </el-carousel>
                        <!--走马灯结束-->
                    </el-col>
                    <el-col span="6">
                        <el-card>
                            <h3>
                                <i style="font-weight: bold" class="el-icon-trophy">销量最高</i>
                            </h3>
                            <el-divider></el-divider>
                            <el-table :data="topArr">
                                <el-table-column label="商品排名" type="index"></el-table-column>
                                <el-table-column label="商品名" prop="title"></el-table-column>
                                <el-table-column label="销量" prop="saleCount"></el-table-column>
                            </el-table>
                        </el-card>
                    </el-col>
                </el-row>
    <!--            商品开始-->
                <el-row gutter="20">
                    <el-col  style="margin: 10px 0" span="6" v-for="p in productArr">
                        <el-card>
                            <img :src="p.url" width="100%" alt="">
                            <p style="font-size: 14px">{{p.title}}</p>
                            <p style="font-size: 12px">￥{{p.price}}  <s>{{p.oldPrice}}</s>
                                <span style="float: right">销量:{{p.saleCount}}件</span>
                            </p>
                        </el-card>
                    </el-col>
                </el-row>
    <!--            商品结束-->
            </el-main>
            <el-footer>
                <div style="background-image: url('imgs/wave.png');height: 95px">
                </div>
                <div style="text-align: center;background-color: #3f3f3f;
                color: #b1b1b1;padding: 30px 0">
                    <p>Copyright © 北京达内金桥科技有限公司版权所有 京ICP备12003709号-3 京公网安备 11010802029572号</p>
                    <p>涵盖20余门课程体系，致力于打造权威的IT职业教育学习平台</p>
                    <p>达内在线WWW.TMOOC.CN 专注于IT职业技能培训</p>
                </div>
            </el-footer>
        </el-container>
    </div>
    </body>
    <!-- import Vue before Element -->
    <script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
    <!-- import JavaScript -->
    <script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
    <script>
        let v = new Vue({
            el: '#app',
            data: function () {
                return {
                    topArr:[
                        {title:"小米手机",saleCount:1432},
                        {title:"安踏拖鞋",saleCount:987},
                        {title:"李宁毛巾",saleCount:957},
                        {title:"耐克跑鞋",saleCount:842},
                        {title:"联想电脑",saleCount:758},
                        {title:"华为电视",saleCount:235}
                    ],
                    productArr:[{title:"森马牛仔裤女宽松慢跑裤运动风2022春季新款显瘦束脚长裤复古",price:233,oldPrice:598,url:"imgs/a.jpg",saleCount:2342},
                        {title:"茵曼马甲连衣裙两件套春季新款娃娃领色织格长袖背心裙套装",price:233,oldPrice:598,url:"imgs/b.jpg",saleCount:2342},
                        {title:"雪中飞墨绿色短袖t恤女夏2022新款纯棉半袖打底体恤夏季上衣潮ins",price:233,oldPrice:598,url:"imgs/c.jpg",saleCount:2342},
                        {title:"【佟丽娅同款】鸭鸭明星同款羽绒服2021年冬季新款时尚连帽外套冬",price:233,oldPrice:598,url:"imgs/d.jpg",saleCount:2342},
                        {title:"BEASTER小恶魔鬼脸明星同款夹克毛绒保暖加厚字母印花宽松外套ins",price:233,oldPrice:598,url:"imgs/e.jpg",saleCount:2342},
                        {title:"香影毛呢外套女中长款2021年冬季新款气质韩版娃娃领紫色呢子大衣",price:233,oldPrice:598,url:"imgs/f.jpg",saleCount:2342},
                        {title:"SEMIR森马商场同款打底针织毛衣纯色高领新品显瘦",price:233,oldPrice:598,url:"imgs/g.jpg",saleCount:2342},
                        {title:"美特斯邦威女MTEE 贺岁系列中长款风衣736598",price:233,oldPrice:598,url:"imgs/h.jpg",saleCount:2342},
                        {title:"imone2021秋款黑色小西装外套女韩版学生宽松学院风外套jk外套",price:233,oldPrice:598,url:"imgs/i.jpg",saleCount:2342},
                        {title:"BEASTER 小恶魔明星同款保暖长袖街头潮流连帽卫衣情侣上衣",price:233,oldPrice:598,url:"imgs/j.jpg",saleCount:2342},
                        {title:"憨厚皇后100%绵羊皮2021秋海宁真皮皮衣女长款修身绵羊皮风衣外",price:233,oldPrice:598,url:"imgs/k.jpg",saleCount:2342},
                        {title:"美特斯邦威高腰牛仔裤女宽松小脚新款春秋彩色潮流女士牛仔",price:233,oldPrice:598,url:"imgs/a.jpg",saleCount:2342}]
                }
            },
            methods:{
                handleSelect(key,keyPath){
                    console.log(key);
                }
            }
        })
    </script>
    </html>
    ```

### 03 后台管理 admin

- 效果图 (具体参照代码示例)

  ![image-20221209202959867](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221209202959867.png)

- 实现代码

  - 涉及组件
    - Container 布局容器
    - NavMenu 导航菜单
    - icon 图标
    - table 表格

  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <meta charset="UTF-8">
      <!-- import CSS -->
      <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
  </head>
  <body>
  <div id="app">
      <el-container>
          <el-header style="background-color: #0096dc">
              <h1 style="font-size: 22px;color: white">
                  CoolShark商城后台管理系统
                  <span style="float: right;font-size: 15px">
                      欢迎XXX回来
                      <a href="">退出登录</a>
                  </span>
              </h1>
          </el-header>
          <el-container>
              <el-aside width="200px" style="overflow: hidden">
                  <!--侧边菜单开始-->
                  <el-menu @select="handleSelect">
                      <el-submenu index="1">
                          <template slot="title">
                              <i class="el-icon-s-flag"></i>
                              <span>分类管理</span>
                          </template>
                          <el-menu-item index="1-1">分类列表</el-menu-item>
                          <el-menu-item index="1-2">添加分类</el-menu-item>
                      </el-submenu>
                      <el-submenu index="2">
                          <template slot="title">
                              <i class="el-icon-picture"></i>
                              <span>轮播图管理</span>
                          </template>
                          <el-menu-item index="2-1">轮播图列表</el-menu-item>
                          <el-menu-item index="2-2">添加轮播图</el-menu-item>
                      </el-submenu>
                      <el-submenu index="3">
                          <template slot="title">
                              <i class="el-icon-shopping-cart-2"></i>
                              <span>商品管理</span>
                          </template>
                          <el-menu-item index="3-1">商品列表</el-menu-item>
                          <el-menu-item index="3-2">添加商品</el-menu-item>
                      </el-submenu>
                  </el-menu>
                  <!--侧边菜单结束-->
              </el-aside>
              <el-main>
                  <!--分类表格开始-->
                  <el-table v-if="currentIndex=='1-1'" :data="categoryArr">
                      <!--显示序号-->
                      <el-table-column type="index" label="编号"></el-table-column>
                      <!--显示分类名-->
                      <el-table-column prop="name" label="分类名称"></el-table-column>
                      <!--操作列-->
                      <el-table-column label="操作" width="200">
                          <!--自定义列必须添加template标签 以及slot-scope="scope"
                          scope是定义的一个变量名称, 此变量里面装着当前行的相关信息
                          scope.$index当前行对应的数组下标
                          scope.row当前行对应的数组里面的对象
                          -->
                          <template slot-scope="scope">
                              <el-button
                                      size="mini"
                                      type="danger"
                                      @click="categoryDelete(scope.$index, scope.row)">删除</el-button>
                          </template>
                      </el-table-column>
  
                  </el-table>
                  <!--分类表格结束-->
                  <!--轮播图表格开始-->
                  <el-table v-if="currentIndex=='2-1'" :data="bannerArr">
                      <!--显示序号-->
                      <el-table-column type="index" label="编号"></el-table-column>
                      <!--显示分类名-->
                      <el-table-column label="轮播图">
                          <!--如果表格的列显示的内容不是来自于数组里面对象的属性,而是显示一些
                          其它的标签组成的内容时,需要自定义列-->
                          <!--自定义列 必须添加template标签-->
                          <template slot-scope="scope">
                              <img :src="scope.row.url" width="150">
                          </template>
                      </el-table-column>
                      <!--操作列-->
                      <el-table-column label="操作" width="200">
                          <!--自定义列必须添加template标签 以及slot-scope="scope"
                          scope是定义的一个变量名称, 此变量里面装着当前行的相关信息
                          scope.$index当前行对应的数组下标
                          scope.row当前行对应的数组里面的对象
                          -->
                          <template slot-scope="scope">
                              <el-button
                                      size="mini"
                                      type="danger"
                                      @click="bannerDelete(scope.$index, scope.row)">删除</el-button>
                          </template>
                      </el-table-column>
  
                  </el-table>
                  <!--轮播图表格结束-->
                  <!--商品表格开始-->
                  <el-table v-if="currentIndex=='3-1'" :data="productArr">
                      <!--显示序号-->
                      <el-table-column type="index" label="编号"></el-table-column>
                      <el-table-column prop="title" width="200px" label="商品标题"></el-table-column>
                      <el-table-column prop="price" label="商品价格"></el-table-column>
                      <el-table-column prop="oldPrice" label="商品原价"></el-table-column>
                      <el-table-column prop="saleCount" label="商品销量"></el-table-column>
                      <!--显示分类名-->
                      <el-table-column label="商品图片">
                          <!--如果表格的列显示的内容不是来自于数组里面对象的属性,而是显示一些
                          其它的标签组成的内容时,需要自定义列-->
                          <!--自定义列 必须添加template标签-->
                          <template slot-scope="scope">
                              <img :src="scope.row.url" width="50">
                          </template>
                      </el-table-column>
                      <!--操作列-->
                      <el-table-column label="操作" width="200">
                          <!--自定义列必须添加template标签 以及slot-scope="scope"
                          scope是定义的一个变量名称, 此变量里面装着当前行的相关信息
                          scope.$index当前行对应的数组下标
                          scope.row当前行对应的数组里面的对象
                          -->
                          <template slot-scope="scope">
                              <el-button
                                      size="mini"
                                      type="danger"
                                      @click="productDelete(scope.$index, scope.row)">删除</el-button>
                          </template>
                      </el-table-column>
  
                  </el-table>
                  <!--商品表格结束-->
              </el-main>
          </el-container>
      </el-container>
  </div>
  </body>
  <!-- import Vue before Element -->
  <script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
  <!-- import JavaScript -->
  <script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
  <script>
      let v = new Vue({
          el: '#app',
          data: function () {
              return {
                  currentIndex:"1-1",
                  categoryArr:[{name:"精彩活动"},{name:"精品女装"},{name:"时尚男装"},
                      {name:"医药健康"},{name:"数码科技"}],
                  bannerArr:[{url:"imgs/b1.jpg"},{url:"imgs/b2.jpg"},
                      {url:"imgs/b3.jpg"}],
                  productArr:[{title:"森马牛仔裤女宽松慢跑裤运动风2022春季新款显瘦束脚长裤复古",price:233,oldPrice:598,url:"imgs/a.jpg",saleCount:2342},
                      {title:"茵曼马甲连衣裙两件套春季新款娃娃领色织格长袖背心裙套装",price:233,oldPrice:598,url:"imgs/b.jpg",saleCount:2342},
                      {title:"雪中飞墨绿色短袖t恤女夏2022新款纯棉半袖打底体恤夏季上衣潮ins",price:233,oldPrice:598,url:"imgs/c.jpg",saleCount:2342},
                      {title:"【佟丽娅同款】鸭鸭明星同款羽绒服2021年冬季新款时尚连帽外套冬",price:233,oldPrice:598,url:"imgs/d.jpg",saleCount:2342},
                      {title:"BEASTER小恶魔鬼脸明星同款夹克毛绒保暖加厚字母印花宽松外套ins",price:233,oldPrice:598,url:"imgs/e.jpg",saleCount:2342},
                      {title:"香影毛呢外套女中长款2021年冬季新款气质韩版娃娃领紫色呢子大衣",price:233,oldPrice:598,url:"imgs/f.jpg",saleCount:2342},
                      {title:"SEMIR森马商场同款打底针织毛衣纯色高领新品显瘦",price:233,oldPrice:598,url:"imgs/g.jpg",saleCount:2342},
                      {title:"美特斯邦威女MTEE 贺岁系列中长款风衣736598",price:233,oldPrice:598,url:"imgs/h.jpg",saleCount:2342},
                      {title:"imone2021秋款黑色小西装外套女韩版学生宽松学院风外套jk外套",price:233,oldPrice:598,url:"imgs/i.jpg",saleCount:2342},
                      {title:"BEASTER 小恶魔明星同款保暖长袖街头潮流连帽卫衣情侣上衣",price:233,oldPrice:598,url:"imgs/j.jpg",saleCount:2342},
                      {title:"憨厚皇后100%绵羊皮2021秋海宁真皮皮衣女长款修身绵羊皮风衣外",price:233,oldPrice:598,url:"imgs/k.jpg",saleCount:2342},
                      {title:"美特斯邦威高腰牛仔裤女宽松小脚新款春秋彩色潮流女士牛仔",price:233,oldPrice:598,url:"imgs/a.jpg",saleCount:2342}]
              }
          },
          methods:{
              handleSelect(key,keyPath){
                  if (key=="1-2"){
                      v.$message("添加分类");
                  }else if(key=="2-2"){
                      v.$message("添加轮播图");
                      window.location = "./insertBanner.html";
                  }else if(key=="3-2"){
                      v.$message("添加商品");
                  }else{ //1-1  2-1   3-1
                      v.currentIndex = key;
                  }
              },
              categoryDelete(i,category){
                  v.categoryArr.splice(i,1);
                  v.$message("删除了"+category.name);
              },
              bannerDelete(i,banner){
                  v.bannerArr.splice(i,1);
                  v.$message("删除成功!");
              },
              productDelete(i,product){
                  v.productArr.splice(i,1);
                  v.$message("删除成功!");
              }
          }
      })
  </script>
  </html>
  ```

### 04 商品详情 detail

- 效果图

![image-20221210100734699](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221210100734699.png)

- 实现代码
  - Container 布局容器
  - Layout布局分栏的应用
  - Card 卡片
  - NavMenu 导航菜单
  - Divider 分割线

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <!-- import CSS -->
    <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
    <style>
        .el-header img{
            vertical-align: middle;/*中间对齐*/
        }
        .el-header a{
            color: #666;
            text-decoration: none;
        }
        .el-table .el-table__cell{
            padding: 0;/*去掉自带的内边距*/
        }
    </style>
</head>
<body>
<div id="app">
    <el-container>
        <el-header height="150px">
            <div style="width: 1200px;margin: 0 auto">
                <img src="imgs/logo.png" width="300" alt="">
                <a href="">首页</a><el-divider direction="vertical"></el-divider>
                <a href="">热点资讯</a><el-divider direction="vertical"></el-divider>
                <a href="">商家入驻</a><el-divider direction="vertical"></el-divider>
                <a href="">社会招聘</a><el-divider direction="vertical"></el-divider>
                <a href="">校园招聘</a><el-divider direction="vertical"></el-divider>
                <a href="">帮助</a>
            </div>
            <div style="background-color: #0aa1ed">
                <el-menu style="width: 1200px;margin: 0 auto" mode="horizontal"
                         background-color="#0aa1ed" text-color="#fff"
                         active-text-color="#0f0" @select="handleSelect">
                    <el-menu-item index="1">精彩活动</el-menu-item>
                    <el-menu-item index="2">精品女装</el-menu-item>
                    <el-menu-item index="3">品牌男装</el-menu-item>
                    <el-menu-item index="4">母婴产品</el-menu-item>
                    <el-menu-item index="5">数码科技</el-menu-item>
                    <div style="float: right;position:relative;top:10px">
                        <el-input type="text" placeholder="请输入搜索的内容">
                            <!--slot="append"设置搜索按钮嵌入到文本框里面-->
                            <el-button slot="append" icon="el-icon-search"></el-button>
                        </el-input>
                    </div>
                </el-menu>
            </div>
        </el-header>
        <el-main style="width: 1200px;margin: 0 auto">
            <el-row gutter="20">
                <el-col span="12">
                    <el-card>
                        <img src="imgs/a.jpg" width="100%">
                    </el-card>
                </el-col>
                <el-col span="12">
                    <p style="font-size: 25px">森马牛仔裤女宽松慢跑裤运动风2022春季新款显瘦束脚长裤复古</p>
                    <el-divider></el-divider>
                    <p style="font-size: 15px;color: #666">
                        销量:432 浏览量:123
                    </p>
                    <p style="font-size: 25px;font-weight: bold">
                        ￥128<span style="font-size: 15px;color: #666">
                        原价:<s>998</s>
                    </span>
                    </p>
                    <el-row gutter="20" style="text-align: center">
                        <el-col span="8">
                            <el-card>
                                <img src="imgs/ewm.jpg" width="100%" alt="">
                            </el-card>
                            <p>扫描关注公众号</p>
                        </el-col>
                        <el-col span="8">
                            <el-card>
                                <img src="imgs/ewm.jpg" width="100%" alt="">
                            </el-card>
                            <p>扫描购买商品</p>
                        </el-col>
                        <el-col span="8">
                            <el-card>
                                <img src="imgs/ewm.jpg" width="100%" alt="">
                            </el-card>
                            <p>扫描下载App</p>
                        </el-col>
                    </el-row>
                </el-col>
            </el-row>
        </el-main>
        <el-footer>
            <div style="background-image: url('imgs/wave.png');height: 95px">
            </div>
            <div style="text-align: center;background-color: #3f3f3f;
            color: #b1b1b1;padding: 30px 0">
                <p>Copyright © 北京达内金桥科技有限公司版权所有 京ICP备12003709号-3 京公网安备 11010802029572号</p>
                <p>涵盖20余门课程体系，致力于打造权威的IT职业教育学习平台</p>
                <p>达内在线WWW.TMOOC.CN 专注于IT职业技能培训</p>
            </div>
        </el-footer>
    </el-container>
</div>
</body>
<!-- import Vue before Element -->
<script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
<!-- import JavaScript -->
<script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
<script>
    let v = new Vue({
        el: '#app',
        data: function () {
            return {

            }
        },
        methods:{
            handleSelect(key,keyPath){
                console.log(key);
            }
        }
    })
</script>
</html>
```

### 05 添加轮播图 insertBanner

- 效果图
  - ![image-20221210100934986](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221210100934986.png)

- 实现代码

  - upload 文件上传

  - ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <!-- import CSS -->
        <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
    </head>
    <body>
    <div id="app">
        <el-page-header
                style="background-color: #0096dc;color: white;
                        line-height: 60px"
                @back="goBack" content="添加轮播图">
        </el-page-header>
        <el-upload
                action="https://jsonplaceholder.typicode.com/posts/"
                list-type="picture-card"
                :on-preview="handlePictureCardPreview"
                :on-remove="handleRemove">
            <i class="el-icon-plus"></i>
        </el-upload>
        <el-dialog :visible.sync="dialogVisible">
            <img width="100%" :src="dialogImageUrl" alt="">
        </el-dialog>
        <el-button type="success" @click="insert()">添加轮播图</el-button>
    </div>
    </body>
    <!-- import Vue before Element -->
    <script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
    <!-- import JavaScript -->
    <script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
    <script>
        let v = new Vue({
            el: '#app',
            data: function () {
                return {
                    dialogImageUrl: '',
                    dialogVisible: false
                }
            },
            methods:{
                goBack(){
                    //返回上一页面
                    history.back();
                },
                handleRemove(file, fileList) {
                    console.log(file, fileList);
                },
                handlePictureCardPreview(file) {
                    this.dialogImageUrl = file.url;
                    this.dialogVisible = true;
                },
                insert(){
    
                }
            }
        })
    </script>
    </html>
    ```

### 06 添加商品 insertProduct

- ​	效果

  ![image-20221210101338544](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221210101338544.png)

- 实现代码

  - 涉及组件

    - Container 布局容器
    - Form 表单
    - SELECT 选择器
    - Button 按钮

  - 

  - ```html
    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="UTF-8">
        <!-- import CSS -->
        <link rel="stylesheet" href="https://cdn.staticfile.org/element-ui/2.15.9/theme-chalk/index.css">
    </head>
    <body>
    <div id="app">
        <el-page-header
                style="background-color: #0096dc;color: white;
                        line-height: 60px"
                @back="goBack" content="添加商品">
        </el-page-header>
        <el-card style="width: 600px;height: 700px;margin: 0 auto">
            <el-form label-width="80px">
                <el-form-item label="商品标题">
                    <el-input type="text"></el-input>
                </el-form-item>
                <el-form-item label="商品价格">
                    <el-input type="text"></el-input>
                </el-form-item>
                <el-form-item label="商品原价">
                    <el-input type="text"></el-input>
                </el-form-item>
                <el-form-item label="商品销量">
                    <el-input type="text"></el-input>
                </el-form-item>
                <el-form-item label="商品库存">
                    <el-input type="text"></el-input>
                </el-form-item>
                <el-form-item label="商品分类">
                     <el-select placeholder="请选择">
                         <el-option label="精彩活动" value="1"></el-option>
                         <el-option label="精品女装" value="2"></el-option>
                         <el-option label="品牌男装" value="3"></el-option>
                         <el-option label="医药健康" value="4"></el-option>
                         <el-option label="数码科技" value="5"></el-option>
                     </el-select>
                </el-form-item>
                <el-form-item label="商品图片">
                    <el-upload
                            action="https://jsonplaceholder.typicode.com/posts/"
                            list-type="picture-card"
                            :on-preview="handlePictureCardPreview"
                            :on-remove="handleRemove">
                        <i class="el-icon-plus"></i>
                    </el-upload>
                    <el-dialog :visible.sync="dialogVisible">
                        <img width="100%" :src="dialogImageUrl" alt="">
                    </el-dialog>
                </el-form-item>
                <el-form-item>
                    <el-button type="success" @click="insert()">添加商品</el-button>
                </el-form-item>
            </el-form>
        </el-card>
    </div>
    </body>
    <!-- import Vue before Element -->
    <script src="https://cdn.staticfile.org/vue/2.6.14/vue.min.js"></script>
    <!-- import JavaScript -->
    <script src="https://cdn.staticfile.org/element-ui/2.15.9/index.min.js"></script>
    <script>
        let v = new Vue({
            el: '#app',
            data: function () {
                return {
                    dialogImageUrl: '',
                    dialogVisible: false
                }
            },
            methods:{
                goBack(){
                    //返回上一页面
                    history.back();
                },
                handleRemove(file, fileList) {
                    console.log(file, fileList);
                },
                handlePictureCardPreview(file) {
                    this.dialogImageUrl = file.url;
                    this.dialogVisible = true;
                },
                insert(){
    
                }
            }
        })
    </script>
    </html>
    ```













