****

# CSS样式

## 目录导航

具体样式参照:[W3School](https://www.w3school.com.cn/css/index.asp)

| 目录                                        | 简介                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| 0 容易遗忘内容                              | 当前笔记中 容易犯错遗忘内容收集                              |
| 1 CSS样式关联方式                           | 简述CSS三种关联方式 1、内联 2、内部 3、`外部`link            |
| 2 **选择器分类**                            | 简述几种选择器方式的使用<br /><br />1 原生选择器 2 分组选择器 3 子孙后代选择器 4 子元素选择器 5 **伪类选择器** |
| 3 CSS样式                                   | `颜色`color `背景`background `文本`text `字体` font `显隐方式`display等 的样式应用 |
| **3.5 盒子模型**                            | `外边距`margin(margin:0 auto实现居中)、`边框`border、`内边距`padding的使用，外边距`粘连问题`与内边距`影响元素宽高`的问题处理 |
| 4 CSS三大特性                               | 继承 层叠 `优先级` 优先级可以关注一下，优先级的定义是看元素表示的区域，区域越小优先级越高 |
| **5 定位方式 position**                     | 1、`默认定位`static、`相对定位`relative、`绝对定位`absolute、`固定定位`fixed、`浮动定位`float 的用法<br /><br />2、注意各定位方式的作用 以及偏移所对应的目标对象<br /><br />3、`绝对定位`相对父元素 需要父元素添加relative `浮动定位`float浮动完毕后 会使上面被顶掉的元素的高度归0 需要设置 **overflow:hidden** |
| 6 溢出设置 overflow                         | 简述移除overflow标签的用法                                   |
| 7 动画效果设置                              | 简述浮动时动画时间、动画效果的写法                           |
| 8 显示层级 z-index                          | 层叠 z-index的用法                                           |
| **9 行内元素inline\| inline-block垂直对其** | 主要用于处理`span`行内元素与`img`行内块元素在对其时，对齐方式问题的处理 |



## 0 容易遗忘内容

- **选择器分类**

  1. [^1]:<font size=4>属性选择器:  根据控件input类型选择控件元素</font>

  2. [^2]:<font size="4">了解分组选择器(关键字: 逗号), 子孙后代选择器(关键字: 空格)，子元素选择器(关键字: >) 的区别</font>

  2. [^3]:<font color="red" size=5>伪类选择器，需求场景:当一个链接在 不同访问状态(悬停、未访问、访问、激活)时  需要显示不同颜色</font>场景下使用:

- **CSS样式**

  1. [^4]: 宽度width 默认为上级元素宽度的百分之百，高度height 默认为当前文本高度，如果文本里面没有内容，则高度为0

  2. [^5]: **text-decoration** 文本下划线|上划线等修饰 常用来<font color=#666 size=5>设置为none ，对超链接<a>标签进行下划线去除</font>

  3. [^6]: **text-shadow** 设置文本阴影

  4. [^7]:文字font样式相关

- **元素显示方式**

  1. [^8]: inline行内元素默认是不能修改宽高的，那么<font color=red size=5>如何修改inline的宽高</font>----修改 display:inline为inline-block 

- **盒子模型**

  1. [^9]:外边距margin的偏移方向，与常用设置

  2. [^10]:<font size=5 color=red>margin粘连问题(子元素与父元素上边距叠在一起) || padding修改影响元素宽高问题</font>

  3. [^14]:<font size=5>margin 设置为 0 auto 居中不生效**可能原因是未设置当前容器宽度**</font>

- **定位方式**

  1. [^11]:绝对定位absolute **相对某个父级元素做偏移** 父元素需要设置**position为relative**表示以自己为参照点

  2. [^12]:浮动定位float **当元素的所有子元素全部浮动时,自动识别的高度为0, 后面的元素会顶上来导致显示异常**, 给元素添加**overflow:hidden** 解决此问题

- **其他**

  1. [^13]:行内元素 例如 图片与输入框常常位置不能对齐，可以使用**vertical-align :对其方式**  进行对齐

## 1 CSS样式关联方式

- 三种引入方式

  - 内联:

    - 在标签的style属性中添加样式代码

      -  弊端:不能复用
      
      ```html
      <h1 style="color: red">内联样式一</h1>
      ```

  - 内部: 

    - 在head标签里面添加style标签,标签体内写样式代码,通过选择器先找到元素对象, 然后再添加样式, 

       - 好处是可以复用, 但是只能在当前页面复用,不能多页面复用
  
    
      ```html
      <head>
          <meta charset="UTF-8">
          <title>Title</title>
          <style>
              h2{
                  color: blue;
              }
          </style>
      </head>
      ```
  
  - 外部:  **link标签引入**
  
    - 在单独的css样式文件中写样式代码, 在html页面中引入此文件即可, 这样的话是可以实现多页面复
  
      ```html
      <link rel="stylesheet" href="my.css">
      ```

## 2 选择器分类

### 2.1 原生选择器

#### 2.1.1 标签名选择器

- 元素标签名 

  ```css
  p{
      color: blue;
  }
  ```

#### 2.1.2 ID选择器

- 标签上加id属性

  ```html
  <p id="bx">冰箱</p>
  ```

- css样式添加 **#id**

  ```css
  #bx{
      color: red;
  }
  ```

#### 2.1.3 类选择器

- 标签上加上种类class属性

  ```html
  <p class="c1">洗衣机</p>
  <div class="c1">苹果</div>
  ```

- css样式添加 **.类名**

  ```css
  .c1{
      color: aqua;
  }
  ```

#### 2.1.4 属性选择器(适用于控件)[^1]

- 按照控件属性对标签进行样式设置

  ```html
  用户名:<input type="text">
  <br>
  密码:<input type="password">
  ```

  ```css
  input[type='text']{
      color: darkgreen
  }
  ```

#### 2.1.5 任意选择器

- *{样式代码块}

```
*{
    border: 1px solid red;
}
```

### 2.2 分组选择器( 逗号分隔 )[^2]

- 使用场景

  - 适用于同时对**多个标签元素**进行样式设置

- 特点

  - 将多个选择器划分为一组(中间用 **逗号 隔开** 进行分组)


  - h3,#bx,.c1 {样式代码} 

    ```css
    #bx,.c1,p{
        color: red;
    }
    ```




### 2.3 子孙后代选择器( 空格分隔 )

- 选择的元素**包含所有子孙元素** 

  - 标签

    ```html
    <div>
        <div><p>p3</p></div>
        <div>
            <div><p>p4</p></div>
        </div>
    </div>
    ```

  - 语法

    ```css
    body div div p{
        color: red;
    }
    ```

### 2.4 子元素选择器 (大于号 > )

- 用于精准匹配某一层级的元素 **不包含他的下一层级**

- 查找所有符合条件的元素节点 

  - 标签

    <div>
        <div><p>p3</p></div>
        <div>
            <div><p>p4</p></div>
        </div>
    </div>

  - 语法

    ```css
    body>div>div>p{
        color: blue;
    }
    ```

- 注意:

  - 易错点:<font color=red>**所有节点也包括直接查找内层元素开始**</font>，所以精准匹配必须指定外层

  - 标签

    - 问题:查找p2
  
      ```html
      <div>
          <p>p1</p>
          <div><p>p2</p></div>
          <div>
              <div><p>p3</p></div>
          </div>
      </div>
      ```

    - 语法

      **如果不指定外层body ,也会查找到p3，俩个div也会视为内层div开始查找**
  
      ```html
      body>div>div>p{
          color: #f3cbcb;
      }
      ```
  
      ​				
  

### 2.5 **<font color=gree>伪类选择器-适用于匹配链接a</font>** (hover..匹配元素状态)[^3]

- 使用场景:
  - **适用于一个链接在不同状态下，需要展示不同效果的需求场景**

| 关键字      | 状态描述      |
| ----------- | ------------- |
| **link**    | 未访问状态    |
| **visited** | 访问过状态    |
| **hover**   | 悬停状态      |
| **active**  | 点击/激活状态 |

- 选择器分类

  - 未访问状态 **link**

    ```css
    a:link{
        color: red;
    }
    ```

    

  - 访问过状态 **visited**
  
    ```css
    a:visited{
        color: green;
    }
    ```

  - 悬停状态 **hover**
  
    ```css
    a:hover{
        color: pink;
    }
    ```

  - 点击/激活状态 **active**
  
    ```css
    a:active{
        color: blue;
    }
    ```

## 3 CSS样式

### 3.1 颜色赋值 (rgba可以调节透明度)

- 前言:

  ```markdown
  - 三原色:  红绿蓝  RGB     Red  Green  Blue  , 每个颜色的取值范围0-255    
  - 五种颜色赋值方式:
    - 颜色单词赋值:     red/yellow/pink/purple.....
    - 6位16进制赋值:    #ff0000      
    - 3位16进制赋值:   #f00     每一位重复一次    等效ff0000
    - 3位10进制赋值:  rgb(255,0,0)   
    - 4位10进制赋值:  rgba(255,0,0,0-1)    a=alpha 设置透明度 值越小越透明  
  ```

- - ​	颜色组成
    - 颜色由 R(红色) G(绿色) B(蓝色) 组成 范围都是在0-255之间

- 五种颜色赋值方式

  - **颜色单词**

    ```css
    color: red;
    ```

  - **6位16位进制**

    ```css
    color: #00ff00;
    ```

  - 3位16进制，每位进制重复一次

    ```css
    color: #00f;   /*0000ff 每一位重复一次*/
    ```

  - **rab** 颜色

    ```css
    color: rgb(255,0,0);  
    ```

  - **ragb** 颜色+透明度

    ```css
    color: rgba(255,0,0,0.5); 
    ```

​				

### 3.2 背景 background 相关 || 宽高 

- 前言:

  | **背景关键字**          | **描述**                                                     |
  | ----------------------- | ------------------------------------------------------------ |
  | **background-image**    | **url("资源路径")**; 设置背景图片                            |
  | **background-size**     | 宽度 高度;  设置背景图片尺寸                                 |
  | **background-repeat**   | no-repeat;  禁止重复                                         |
  | **background-position** | 横向偏移值  纵向偏移值; 设置背景图片的位置,可以将偏移值换成偏移的百分比 |
  | **background-color**    | 设置背景颜色                                                 |

  

- 属性配置

  - **宽高** : width || height

    - <font size=5 color=red>默认宽高</font>[^4]

      - **宽度时上层元素的百分之百**
      - 高度是内容文本的高度

      ```css
      /*设置宽高*/
      width: 200px;
      height: 200px;
      ```

  - **背景色**: background-color

    ```css
    /*设置背景颜色*/
    background-color: red;
    ```

  - **背景图片**: background-image

    ```css
    /*设置背景图片*/
    background-image: url("../b.png");
    ```

  - **背景是否重复**: background-repeat

    ```css
    /*设置背景是否重复*/
    background-repeat: no-repeat;
    ```

  - **背景图片大小**: background-size

    ```css
    /*设置背景图片大小 宽高*/
    background-size: 100px 100px;
    ```

  - **背景图片的位置**： background-position

    - 偏移值

      ```css
      /*设置背景图片的位置:横向偏移值 纵向偏移值(从上到下)*/
      background-position: 50px 100px;
      ```

    - 偏移百分比

      ```css
      /*设置背景图片的位置:横向偏移百分比 纵向偏移百分比*/
      background-position: 50% 50%;
      ```



- 语法

  ```css
  div{
      /**
      设置元素的宽高，默认宽高:宽度是上层元素的百分之百
      高度有内容文本高度决定
      */
      /*设置宽高*/
      width: 200px;
      height: 200px;
      /*设置背景颜色*/
      background-color: red;
      /*设置背景图片*/
      background-image: url("../b.png");
      /*设置背景是否重复*/
      background-repeat: no-repeat;
      /*设置背景图片大小 宽高*/
      background-size: 100px 100px;
      /*设置背景图片的位置:横向偏移值 纵向偏移值(从上到下)*/
      background-position: 50px 100px;
      /*设置背景图片的位置:横向偏移百分比 纵向偏移百分比*/
      background-position: 50% 50%;
  }
  ```

### 3.3 文本样式

#### 	3.3.1 文本相关

- | 文本相关            | 描述                                                         |
  | ------------------- | ------------------------------------------------------------ |
  | text-align          | left \| right \| center;   设置水平对齐方式                  |
  | **text-decoration** | overline上划线 \| underline下划线 \| line-through删除线 \| none去掉文本修饰;    设置文本修饰<br /><br />常用来**去除超链接标签<a>自带的下划线** |
  | line-height         | 设置行高,默认高度包裹文本, 可以实现垂直居中                  |
  | **text-shadow**     | 设置文本阴影 : 颜色 x偏移值 y偏移值 模糊度 值越小越清晰（以下方为正向坐标抽） |

- ​	**文本对齐方式:**  

  - **text-align  : center || right || left** 

    ```css
    /*水平对齐方式*/
    text-align: center;
    ```

- **文本修饰**

  - text -decoration： line-through 删除线   || overline 上划线 || line-through 删除线 || underline 下划线

    ```css
    text-decoration: line-through;
    ```

  - <font color=red>**去除超链接下划线**</font>[^5]

    ```css
    a{
        text-decoration: none;
    }
    ```

- **设置行高**

  - line-height ：设置行高，默认值为字体大小，可以实现垂直居中

    ```css
    line-height: 50px;
    ```

- **设置文本阴影**[^6]

  - 设置文本阴影 : 颜色 x偏移值 y偏移值 模糊度 值越小越清晰（以下方为正向坐标抽）

  - text-shadow :  red 10px 10px 3px;

    ```css
    /*设置文本阴影:颜色 x偏移值 y偏移值 模糊度 值越小越清晰*/
    text-shadow: red 10px 10px 3px;
    ```

####   3.3.2 字体相关[^7]

- | 字体相关                           | 描述                                                         |
  | ---------------------------------- | ------------------------------------------------------------ |
  | font-size                          | **font-size:20px;**  <br /><br />**设置字体大小**            |
  | font-weight                        | **font-weight:bold/normal;** <br /><br />**设置字体加粗**    |
  | font-family                        | **font-family: xxxx,xxx,xxx;**  <br /><br />**设置字体，多个字体中间用,隔开** |
  | font-style                         | **font-style:italic;** <br /><br />**设置斜体**              |
  | **font**（font-size + font-style） | **font: 30px xxx,xxx,xxx;**  <br /><br />**设置字体大小** **+ 字体类型** |

- **设置字体大小**

  - font-size

    ```css
    font-size: 30px;
    ```

- **设置字体加粗**

  - font-weight：normal....

    ```css
    font-weight: normal;/*去掉加粗*/
    ```

- **设置字体**

  - font-family: 字体样式;

    ```css
    /*设置字体*/
    font-family: cursive;
    ```

- **设置斜体**

  - font-style: 类型;

    ```css
    /*设置斜体*/
    font-style: italic;
    ```

- **设置字体大小** **+ 字体类型**

  - font: 字体大小 字体类型;

    ```css
    /*设置字体大小 + 斜体*/
    font:50px cursive;
    ```

​			

### 3.4 元素显示方式

#### 3.4.1 display分类

| 显示方式         | 描述                                                         |
| ---------------- | ------------------------------------------------------------ |
| **none**         | 隐藏元素                                                     |
| **inline**       | **行内元素, 特点: 共占一行,不能修改宽高, 包括:<font size=5>span,b,i,u,s,超链接a</font>** |
| **block**        | 块级元素, 特点: 独占一行并可以修改宽高, 包括:h1-h6,p,div     |
| **inline-block** | 行内块元素,特点: 共占一行并可以修改宽高,包括:**input,img**   |

显示方式display的分类

- **none** 
  -  隐藏元素
- **inline** （span、a...） 
  - **行内元素, 特点: 共占一行,不能修改宽高, 包括:span,b,i,u,s,超链接a**
- **block** （div...）
  -  块级元素, 特点: 独占一行并可以修改宽高, 包括:h1-h6,p,div
- **inline-block** （**img...**）
  -  行内块元素,特点: 共占一行并可以修改宽高,包括:input,img

#### 3.4.2 如何设置inline的宽高[^8]

- 默认情况下inline宽高是不能修改的 (修改不生效) 如

  - a超链接标签、span标签

- 如果要进行宽高修改需要对他们进行设置

  - **display: inline-block**，将inline进行修改

  - a标签的设置
  
    ```css
    a{
        color:white;
        background-color: #0aa1ed;
        width: 132px;
        height: 40px;
        display: inline-block;
        text-align: center;
        line-height: 40px;
        text-decoration: none;
        /*设置圆角*/
        border-radius: 3px;
    }
    ```
  



### 3.5 盒子模型

#### 前言

- 盒子模型= content内容+margin外边距+border边框+padding内边距

- 盒子模型用来控制元素的显示效果:

- | 模型类型          | 描述               |
  | ----------------- | ------------------ |
  | content内容       | 控制内容的显示宽高 |
  | **margin外边距**  | 控制元素的显示位置 |
  | border边框        | 控制边框效果       |
  | **padding内边距** | 控制元素内容的位置 |

- ![image-20221129152034049](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221129152034049.png)	

#### 3.5.1 盒子模型之Content内容

- 用来控制元素的显示宽高
- 相关样式:
  - width 设置宽度
  - height 设置高度
- 两种赋值方式:
  - 像素 
  - 上级元素的百分比
- **行内元素不能修改宽高,如果必须修改则将元素改成块级或行内块**

#### 3.5.2 盒子模型之Margin外边距[^9]

| 简述                                                         | 详细描述                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 元素排列规则                                                 | 文档流中，元素默认从上往下，从左往右排列                     |
| **margin元素的偏移是以上，左位置为参照点，在那边的元素不动，右下的元素进行偏移** | 当我们设置上和左外边距时，会导致盒子自身位置发生变化，如果设置右和下外边距，则改变其他盒子位置 |
| **关于font-size** p段落标签的字体大小表示段落高度，与上下外边距等长 | **p外边距的默认值与元素的font-size字体大小相等 **当字体大小设置为32时，p的段落标签会上下都设置等长度的外边距，用于分段 |
| **上下相邻添加外边距，取最大值，左右相邻添加外边距取和       | 上下相邻彼此添加外边距,取最大值. 左右相邻彼此添加外边距 两者相加（上下取最大，左右取和 |
| <font color=red size=5>**粘连问题**</font>                   | 当元素的上边缘和上级元素的上边缘重叠时,给**父级**元素添加上外边距会出现粘连问题, 给上级元素添加 overflow:hidden解决此问题 |

- <font size=4>注意事项:</font>

  - margin设置左上外边距，自己发生偏移，上下外边距，对应方向元素发生偏移

  - **p外边距的默认值与元素的font-size字体大小相等**
    - 当字体大小设置为32时，p的段落标签会上下都设置等长度的外边距，用于分段

  - 元素距上级元素或相邻兄弟元素的距离称为外边距

- <font size=4>**赋值方式**:</font>

  - **margin-left/right/top/bottom:10px;**

    -  单独某一个方向添加外边距

  - **margin:10px;**

    -  四个方向添加外边距

  - **margin:10px 20px;**

    -  上下和左右赋值 左右auto时为居中

  - **margin:10px 20px 30px 40px;**

    -  上右下左顺时针赋值

  - **margin: 0px auto居中**[^14]

    - <font color=blue>注意点: 有时候使用了外边距居中但没有效果，可能是因为**当前元素宽度没有设置**，默认继承上级元素100%，已经是居中满屏了，所以调用会不生效</font>

  - html

    ```HTML
    <div id="d1"></div>
    <div id="d2"></div>
    ```

  - css

    ```CSS
    	 #d1{
                width: 100px;
                height: 100px;
                border: 1px solid red;
                /*单独某一个方向添加外边距*/
                margin-left: 100px;
                margin-top: 100px;
                margin-bottom: 50px;
                margin-right: 50px;
                /*四个方向添加外边距*/
                margin: 50px;
                /*上下和左右赋值*/
                margin: 50px 100px;
                /*外边距实现居中
                 左右auto代表自动,左右自动则为居中*/
                margin: 0 auto;
                /*上右下左顺时针赋值*/
                margin: 10px 20px 30px 40px;
            }
            #d2{
                width: 100px;
                height: 100px;
                border: 1px solid red;
                /*上下相邻 彼此添加外边距 取最大值*/
                margin-top: 50px;
            }
    ```

    

- <font size=4>**注意:**</font>
  - **<font color=blue>上下相邻彼此添加外边距,取最大值. 左右相邻彼此添加外边距 两者相加（上下取最大，左右取和）</font>**
  - **行内元素上下外边距无效**
  - **粘连问题**: 当元素的上边缘和上级元素的上边缘重叠时,给元素添加上外边距会出现粘连问题, 给上级元素添加 overflow:hidden解决此问题

#### 3.5.3 盒子模型之border边框

- 作用:控制边框效果

- 赋值方式:
  - border: 
    - 粗细 样式 颜色; 四个方向添加边框
  - border-left/right/top/bottom:
    - 粗细 样式 颜色; 单独某一个方向添加边框
  
- **border-radius**:10px; 设置圆角 值越大越圆

- HTML

  ```HTML
     <div id="d1">边框测试</div>
  ```

- CSS

  ```CSS
   	#d1{
              width: 200px;
              height: 200px;
              border: 10px dotted red;
              /*值越大越圆，超过宽高的一半时为正圆*/
              border-radius: 200px;
          }
  ```

#### 3.5.4 盒子模型之Padding内边距

- 作用: 控制元素内容的位置
- 赋值方式: 和外边距类似
  - **padding-left/right/top/bottom:10px;** 
    - 单独某个方向赋值
  - **padding:10px;**
    -  四个方向赋值
  - **padding:10px 20px;** 
    - 上下和左右赋值
  - **padding:10px 20px 30px 40px;** 
    - 上右下左顺时针赋值
- 默认情况下给元素添加内边距会影响元素的宽高, 给元素添加box-sizing:border-box;后则不会影响宽高

#### 3.5.5 margin粘连问题 || padding修改影响元素宽高问题[^10]

​	margin 问题1:

​	   当元素的上边缘和上级元素的**上边缘重叠**时,给父级元素添加上外边距会出现粘连问题（俩个元素绑定移动）

   处理方式:

​		给上级元素添加  **overflow:hidden**

​	示意代码:

- html

  ```html
  <div id="big">
      <div></div>
  </div>
  ```

- css

  ```CSS
  		#big{
              width: 200px;
              height: 200px;
              background-color: red;
              overflow: hidden;/*解决子元素粘连问题*/
          }
          #big>div{
              width: 50px;
              height: 50px;
              background-color: green;
              margin-left: 100px;
              /*当元素的上边缘和上级元素的上边缘重叠时,
              给元素添加上外边距会出现粘连显示异常,
              给上级元素添加overflow:hidden解决*/
              margin-top: 100px;
          }
  ```

  

   padding 问题2:

​		默认情况下给元素添加内边距padding会影响元素的宽高,

- html

  ```html
   <div id="d2">内边距测试</div>
  ```

- css

  ```CSS
   	#d2{
              width: 100px;
              height: 100px;
              border: 1px solid red;
              /*给元素添加内布距的时候，会影响元素宽高*/
              padding-left: 100px;
              padding-top: 100px;
              /*设置内边距不影响元素宽高*/
              box-sizing: border-box;
          }
  ```

  

​	处理方式:

​		元素添加   **box-sizing:  border-box;**   后则不会影响宽高

## 4 CSS三大特性

- 继承性
  - 元素可以继承上级元素**文本和字体**相关的样式，部分标签自带效果不受继承影响，比如:超链接的字体颜色
  
- 层叠性
  - 多个样式可以作用在同一个元素之上层叠显示，多个选择器可能选择到同一个元素，如果作痛的样式不同则全部生效
  - 如果作用的样式相同在，则由优先级决定
  
- 优先级(作用范围越小优先级越高)
  - 指选择器的优先级，**作用范围越小优先级越高**，继承属于间接选中元素所以优先级最低
  
  - !**important** 可以指定元素的CSS样式 表示优先级为最高
  
     `color: green !important;`
  
  - **!important > id > class > 标签名 >继承**
  
- HTML

  ```HTML
  <p id="p1">p1</p>
  <div>
      <p>p2</p>
      <span>span1</span>
      <a href="">超链接</a>
  </div>
  ```

- CSS

  ```CSS
        #p1{
              color: blue;
          }
          p{
              color: green !important;
          }
          div{
              color: red;
          }
  ```

## 5 定位方式 postion

| 定位方式              | 是否脱离文档流 | 应用场景                                                     | 参照点                                                       |
| --------------------- | -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 静态定位 static       | false          | 默认场景 元素从左往右从上往下 按照文档流进行排序             | 默认                                                         |
| **相对定位 relative** | false          | **需要对元素进行位置微调**                                   | 参照自己原先文档流所处位置                                   |
| **绝对定位 absolute** | **true**       | 需要往页面中添加一个元素并**实现层叠效果** 同时不能影响其他元素的位置 | 1、默认参照body<br /><br />2、给父元素添加**relative** 参照父元素 |
| 固定定位 fixed        | **true**       | 需要把元素**固定**在页面中的**某个位置**                     | 参数body                                                     |
| 浮动定位 flow****     | **true**       | **把一列数据排序成一行数据**                                 |                                                              |

前言:

- ​	文档流
  - 什么叫文档流: **元素按照从上到下，从左到右排列的有序顺序，可以视为一条流**
  - 脱离文档流
    - **元素原先文档流的位置腾出来，下面的元素会自动依次占据原先元素的位置，所以会导致元素层叠**
  - 不脱离文档流
    - 元素原先的位置依旧保留，元素本身位置可以任意移动 relative相对定位的作用

### 5.1 静态定位 static	

- ​	默认的定位方式
  - 格式
    -  **postion：static**
  - 特点
    - 元素以左上为基准，块级元素从上往下依次排列，行内元素从左向右依次排列
    - 默认情况下无法实现元素层叠效果

### 5.2 相对定位 relative(实现微调)

- 格式: 
  - **position :relative;**
- 特点:
  -  元素**不脱离文档流**(不管元素显示到什么位置,都占着原来的位置) ,默认相对于自己原先位置进行偏移
  -  通过**left/right/top/bottom** 相对于**元素初始位置**做偏移
- **应用场景:**
  -  **当需要对页面中某一个元素位置进行微调时使用**

- HTML

  ```HTML
  <div>div1</div>
  <div>div2</div>
  <div>div3</div>
  ```

- CSS

  ```CSS
   div{
              text-align: center;
              width: 100px;
              height: 100px;
              border: 1px solid red;
          }
          div:hover{/*鼠标悬浮在上面 可以实现元素发生细微偏移效果*/
              /*静态定位，通过外边距移动元素，
              其他元素会受影响*/
              /*margin: 20px 0 0 20px;*/
              /*设置相对定位*/
              position: relative;
              /*让元素相对于初始化做偏移，其他元素不会移动 可以实现层叠效果*/
              top:20px;
              left: 20px;
          }
  ```

### 5.3 绝对定位 absolute(实现添加层叠)

- 格式:
  - **position:absolute;**
- 特点: 
  - 元素**脱离文档流**(不占原来的位置), 通过left/right/top/bottom 相对于窗口(默认)
  - <font size = 5 color=red>以某一个上级元素做参考点进行位置偏移</font>   [^11]
    - 绝对定位默认是以body作为参照点，如果想要以某个元素作为参照点
    - (如果相对于**某个上级元素**做偏移需要将上级元素设置为相对定位) 上级元素设置为<font  size = 5 color=red> **postion:relative** </font>   
-  **应用场景:**
  -  **当需要往网页面中添加一个元素并且需要实现层叠效果,**这个元素又不能影响其它元素的位置的时候**

- HTML

  ```HTML
  <body>
      <div id="d2">
          <div>
              <div> </div>
          </div>
      </div>
      <div id="d1">div1</div>
      <div id="d3">div2</div>
      <div id="d4">div3</div>
  </body>
  ```

- CSS

  ```CSS
      <style>
          div{
              text-align: center;
              width: 100px;
              height: 100px;
              border: 1px solid red;
          }
          #d1{
              /*设置为绝对定位,脱离文档流后面的元素会顶上来*/
              /*不指定大小后面的同层级会顶上来*/
              position: absolute;
              /*!*默认相对于窗口做偏移*!*/
              bottom: 10px;
              right: 10px;
          }
          #d2{
              width: 200px;
              height: 200px;
              background-color: red;
              margin: 100px 0 0 100px;
              /*写谁里面就是以谁为参照物*/
              position: relative;
          }
          #d2>div{
              width: 100px;
              height: 100px;
              margin: 50px 0 0 50px;
              background-color: blue;
  
          }
          #d2>div>div{
              width: 50px;
              height: 50px;
              background-color: green;
              position: absolute;
              left: 0;
              top: 0;
          }
      </style>
  ```

### 

### 5.4 固定定位 fixed(固定位置)

- 格式: position:fixed;

- 特点: 元素脱离文档流,通过left/right/top/bottom相对于窗口做位置偏移

- 应用场景: **当需要将某个元素固定在窗口的某个位置时使用.**

- HTML

  ```HTML
  <div id="d1"></div>
      <div id="d2"></div>
      <img src="../b.png" alt="">
      <img src="../b.png" alt="">
  </div>
  ```

- CSS

  ```CSS
    #d1{
              width: 1000px;
              height: 100px;
              background-color: red;
              /*设置固定定位，脱离文档流*/
              position: fixed;
              top:0;/*让元素贴着窗口最上方*/
          }
          #d2{
              width: 50px;
              height: 200px;
              background-color: blue;
              position: fixed;
              bottom: 0;
              right: 0;
          }
          body{
              /*让body里面的内容往下移动100像素*/
              padding-top:100px;
          }
  ```

### 

### 5.5 浮动定位 flow(列换行)[^12]

- 格式:

   -  **float:left/right**

- 特点: 

   - 元素脱离文档流, 从当前行向左或向右浮动, **当撞到上级元素的边缘或其它浮动元素时停止.**

- 应用场景: 

   - **当需要将纵向排列的元素改成横向排列时使用浮动定位**

- 一行装不下时会自动换行, 换行时有可能被卡主

- 遇到的问题:

   - **当元素的所有子元素全部浮动时,自动识别的高度为0, 后面的元素会顶上来导致显示异常**, 给元素添加**overflow:hidden** 解决此问题

   **如何处理在未定位高度时，元素全部上浮导致空间被下面的其他元素顶上来导致的异常**

​	给元素添加 overflow : hidden 解决问题

- HTML

  ```HTML
  <ul>
          <li><a href="">首页</a></li>
          <li><a href="">免费课</a></li>
          <li><a href="">直播课</a></li>
          <li><a href="">线上班</a></li>
          <li><a href="">线下班</a></li>
      </ul>
      <div>
          <div id="d1"></div>
          <div id="d2"></div>
          <div id="d3"></div>
      </div>
  ```

- CSS

  ```CSS
   body>div{
              /*继承只有文本或字体实现继承*/
              width: 200px;
              /*height: 200px;*/
              border: 1px solid red;
              /*
              在元素边框为定义高度时
              当元素的所有子元素全部浮动后
              则自动识别的高度为0，后面浮动的元素会顶上来，导致修饰异常，
              添加以下样式解决此问题*/
  
              /*主要用于处理边框为一条线的问题*/
              overflow: hidden;
          }
          #d1{
              width: 50px;
              height: 50px;
              background-color: red;
              float: left;
          }
          #d2{
              width: 50px;
              height: 50px;
              background-color: green;
              float: left;
          }
          #d3{
              width: 50px;
              height: 50px;
              background-color: blue;
              float: left;
          }
          ul{
              list-style-type: none;
              margin: 0;
              padding: 0;
          }
          li{
              float: left;
              margin-right: 20px;
          }
  ```



## 6 溢出设置 overflow

- 作用:

  - 用于设置**超出部分**的显示效果

- overflow 类型:

  - visible 显示(默认)
  - scroll 滚动显示
  - hidden 超出部分隐藏

  ```css
  /*设置超出部分怎样显示
  visible 显示(默认)
  scroll 滚动显示
  */
  overflow: hidden;
  ```

## 7 动画效果设置

- 设置动画持续时间

```css
/*设置动画持续时间*/
transition-duration: 1s;
```

- 悬浮修改倍数

  ```css
  #t_l_div>img:hover{
      transform: scale(1.1);
  }
  ```

## 8 显示层级 z-index （层叠优先级）

- 作用: 

  - 元素出现层叠时，控制元素的显示层级(数值越大，越靠上层级)

- 默认排序:

  - 没有设置z-index的情况下，默认层叠等级是按照代码顺序，代码靠后的在上

    ```css
    #d1{
        width: 100px;
        height: 50px;
        background-color: red;
        position: absolute;
        z-index: 1;
    }
    #d2{
        width: 50px;
        height: 100px;
        background-color: blue;
        position: absolute;
        z-index: 0;
    }
    ```

## 9 行内元素 inline|inline-block的垂直对其方式[^13]

- 用于处理什么问题:

  - 行内元素 位置不能对其的问题 
  - 图片与输入框常常位置不能对齐

- 关键字

  - **vertical-align :对其方式** 

- 对其方式

  - top 上对齐
  - middle 中间对齐
  - bottom 下对齐
  - baseline 基线对齐(默认)

- 示例

  - 
    
    ```css
    body>img{
        width: 320px;
        /*行内元素的垂直对齐方式
        top 上对齐
        middle 中间对齐
        bottom 下对齐
        baseline 基线对齐(默认)*/
        vertical-align: bottom;
        height: 320px;
    }
    ```





