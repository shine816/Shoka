# 	HTML标签笔记

文档手册地址 : [**W3CSchool**](https://www.w3school.com.cn/tags/index.asp)

前序:

本笔记主旨内容为简要记录HTML基本常用标签的使用，方便后续进行查阅



## 目录导航

| 目录                    | 简介                                                         |
| ----------------------- | ------------------------------------------------------------ |
| 0 容易遗忘内容          | 当前笔记中 容易犯错遗忘内容收集                              |
| 1 段落标签 **p h**      | 标题h 段落p 的使用                                           |
| 2 修饰标签 **ur br...** | 特殊功能标签介绍 如下划线 换行 删除线 斜体等                 |
| 3 列表 **ol ul**        | 有序列表 无序列表的使用                                      |
| 4 图片标签 **img**      | 图片标签的使用介绍                                           |
| 5 超链接标签 **a**      | 超链接标签使用 **1、内部跳转** 2、外部跳转                   |
| 6 表格标签 **table**    | 1、表格标签table 及其内在标签元素介绍  2、**colspan rowspan**跨行跨列的使用 |
| 7 **表单标签 form**     | 1、表单提交的具体方式及组成  2、**name属性字段的含义**(表示传输给服务器的字段值) |
| 8 **输入框 input**      | 1、**输入框的多种分类 单选、多选、文本....**   2、功能性输入框的介绍 |
| 9 分区标签 **div span** | 块标签 div 行内标签 span的分区                               |



## 0 容易遗忘内容

**使用脚注方式实现链接内部跳转**

1. [^1]:超链接a实现内部跳转     **id与href=“#id”的应用**

2. [^2]: 表格标签table的colspan、**rolspan 跨行、跨列属性的应用**

3. [^3]: form表单input name属性 设置 **name可以视为对象字段值**

4. [^4]: 文本信息按钮相关 **input大家庭**

5. [^5]:select option 下拉选value的得传递 **有value没有value传输的值是什么** 

## 1 段落标签 p h

- 标题:h1-h6

```HTML
<h1 align="right">标题1</h1>
<h2 align="center">标题2</h2>
<h3>标题3</h3>
<h4>标题4</h4>
<h5>标题5</h5>
<h6>标题6</h6>
```

- ​	段落: p

```html
<p>段落1</p>
```

## 2 修饰标签 ur br...

分割线: hr

```html
<hr>
```

换行: br

```html
</br>
```

加粗: b

```html
<b>加粗</b>
```

下划线: u

```html
<u>下划线</u>
```

## 3 列表 ol ul

- 有序列表 ol  (order-list)

  ```HTML
  <ol>
      <li>列表1</li>
      <li>列表2</li>
      <li>列表3</li>
  </ol>
  ```

- 无序列表 ul (unorder-list)

  ```HTML
  <ul>
      <li>小学九年</li>
      <li>初中3年</li>
      <li>高中3年</li>
  </ul>
  ```

## 4 图片标签 img

- img

  ```html
  <img src="图片来源路径: 相对路径|绝对路径" alt="图片找不到时，显示的文本内容" title="鼠标悬浮在图片上时，显示的悬浮文字提示" width="图片宽" height="图片高" 
  ```

  - **src**

    - 相对路径 : 访问站内资源使用

      - <font size=5px color=red>**./**</font>当前目录

        ```HTML
        <img src="./a.png" alt="">
        ```

      -  ../上层级文件夹目录

        ```HTML
        <img src="../b.png" alt="">
        ```

    - 绝对路径: 一般访问站外资源

      - http || https 请求协议路径(图片盗链)

  - **alt**

    - 图片不能正常显示时，显示的文本说明

      ```HTML
      <img src="./a.png" width="50%" title="鬼刀" alt="没有此图片资源">
      ```

  - **title**
    - 图片标题 鼠标悬浮在上面时显示的文字
  - **width height**  
    - 注意点:
      - **使用宽度时，高度会进行等比例缩放**
      - 子元素默认继承上次元素的百分之百宽 但高度需要自行指定否则为0
    - 像素px 500px
    - 百分比 50% 

## 5 超链接标签 a

- a

  ```html
  <a href="连接地址: 内部跳转 && 外部跳转" id="内部链接跳转时的锚点"></a>
  ```

- 页面跳转

  - href 后面跟地址 (相对定位 | 绝对定位) 

    ```HTML
    <a href="http://www.baidu.com">超链接1</a>
    <a href="02简历练习.html">超链接2</a>
    <a href="a.png">超链接3</a>
    <!--图片标签-->
    <a href="http://www.baidu.com">
        <img src="../b.png" alt="">
    </a>
    ```

    

- **<font size=5px color=blue>内部链接跳转</font>**[^1]

  ----

  - A链接标签**,设置id属性**,表示一个锚点

  - B链接标签，**设置href, #**后面加锚点 进行跳转

    ```HTML
    <!--A --> <a id="top"></a>
    <!-- B--> <a href="#top"></a>
    
    <a id="top"></a>
    这是一个凄美的爱情故事,Tom爱上了Jerry...<br>
    ...<br>...<br>...<br>...<br>...<br>...<br>
    ...<br>...<br>...<br>...<br>...<br>...<br>
    ...<br>...<br>...<br>...<br>...<br>...<br>
    ...<br>...<br>...<br>...<br>...<br>...<br>
    ...<br>...<br>...<br>...<br>...<br>...<br>
    最后的最后 <a href="#top">回到顶部</a>
    
    ```

## 6 表格标签 table

- table

  - 标签

    - <caption> 表格标题
    - tr  
      - th 特殊列 代表表头 里面的文字默认**居中且加粗**
      - td 普通列
      - td
      - ...
    - ...

    ```HTML
    <table border="1px">
        <caption>购物车</caption>
        <tr>
            <th>商品名</th>
            <th>价格</th>
        </tr>
        <tr>
            <td>小米手机</td>
            <td>4000</td>
        </tr>
        <tr>
            <td>华为手机</td>
            <td>3000</td>
        </tr>
    </table>
    ```

  - 相关属性

    - **<font color=red>rowspan 与 colspan</font>**[^2]

      - rowspan

        - 跨行(上下)

      - colspan

        - 跨列(左右)

      - 注意点:设置的时候跨哪行哪列就把对应被跨的，删除

        <table border="1">
            <tr>
                <td colspan="2">1-1</td>
                <td rowspan="2">1-3</td>
                <td rowspan="2">1-4</td>
            </tr>
            <tr>
                <td>2-1</td>
                <td>2-2</td>
            </tr>
        </table>

    - border 边框

## 7 表单标签 form									

- **form**

  - 简述

    - 与后端进行数据交互的时候，可以通过表单将数据提交给后台

  - 属性

    - **action** 链接地址

    - **method** get/post/... 请求方式

      ```HTML
      <form action="请求连接地址" method="请求方式">
          ....<input type="text" name="属性名">
          <input type="sumit">
      </form>
      ```

  - **input**

    - 简述

      - 作为form表单提交数据里面的控件，给当前控件设置name值，就可以减数据存储进这个控件值中

      - 属性[^3]

        - **<font size=6px color=red>name</font>** 所有与数据进行交互的控件所必须有的属性，如果没有该属性则不会提交此控件的内容
        - **placeholder** 占位文本
        - **maxlength** 最大字符长度
        - **value** 设置控件的值
        - **readonly** 设置只读

      - input type = **submit** 提交按钮

        ```HTML
        <form action="http://www.tmooc.cn">
        <!--    name属性是所有控件所必须有的属性，如果没有该属性则不会提交此控件的内容-->
        <!--    placeholder占位文本，maxlength设置最大字符长度-->
        <!--    value 设置控件的值 readonly设置只读-->
            用户名:<input type="text" name="username" placeholder="用户名">
            <br>
            密码:<input type="password" name="password" placeholder="密码">
            <br>
            <input type="submit" value="注册">
        </form>
        ```

        

## 8 输入框 input

- input

  - 简述

    - 作为input控件，负责处理用户填写的数据 与部分自定义按钮的使用

  - 基本语法

    ```HTML
    <input type="类型" value="input内置属性值" placeholder="提示用户信息" name="与服务端交互时，传输给服务端的字段">
    ```

  - 基本属性
    - **name** 参数类别，所有文本信息按钮所必须有的属性
    - **value**
      - 文本信息按钮
        - 显示给页面的值
      - 功能性按钮
        - 设置修饰的文本值

### 8.1 文本信息按钮[^4]

####    8.11 单选框 radio

- **注意:单选框和多选框必须添加value属性，否则提交的内容为on**

- checked 默认选中

- > >  name表示类别，在提交给服务器参数时，所显示的字段名称,value为选中框的值

  ```HTML
  <input type="radio" name="gender" value="man" checked>男
  <input type="radio" name="gender" value="woman">女
  ```

  #### 8.12 复选框 checkbox

  ```html
  <input type="checkbox" name="hobby" value="cy">抽烟
  <input type="checkbox" name="hobby" value="hj">喝酒
  <input type="checkbox" name="hobby" value="tt">烫头
  ```

  > https://www.tmooc.cn/?username=&password=&gender=man&hobby=cy&hobby=hj&hobby=tt
  > 传输的类型:
  > &gender=man 单选框:1个参数
  > &hobby=cy&hobby=hj&hobby=tt 多选框:多个参数

####   8.13 日期选框 date

```HTML
<input type="date" name="date">
```

####  8.14 文件选择框 file

```HTML
<input type="file" name="file">
```

#### 8.15 <font color=red>下拉框选 SELECT</font> Option[^5]

<!--select下拉选里面的option标签
设置了value传输的是value的值 没有设置value传输的是框里面的值-->

- 效果图:

  - <select name="city">
        <option value="bj">北京</option>
        <option value="">上海</option>
        <option value="">广州</option>
    </select>

- 语法:

  - 说明: 当option里面

    - 没有定义value值	传输给服务器的数据city=**标签框里面的值**
    - 定义了value值  传输给服务器的数据 **city=value**

    ```HTML
    <select name="city">
        <option value="bj">北京</option>
        <option >上海</option>
        <option value="">广州</option>
    </select>
    ```
  
    

#### 8.16  文本 text

```html
用户名:<input type="text" name="username" placeholder="用户名">
```

#### 8.17 密码 password

```html
密码:<input type="password" name="password" placeholder="密码">
```

### 8.2 功能性按钮

#### 8.8.1 submit 提交

**提交数据**

```html
<input type="submit" value="注册">
```

#### 8.8.2 reset 重置

**清空提交数据**

```html
<input type="reset" value="重置">
```

#### 8.8.3 button 自定义按钮

```html
<input type="button" value="自定义按钮">
```



## 9 分区标签 div span..

- 作用 : 可以将多个有相关性的标签添加到一个分区标签里面，对多个标签进行统一管理，

  可以将分区标签理解为一个容器

- 分区标签包括 div 和 span

  - div ： 块级分区标签 ，独占一行

    ```HTML
    <div style="red" border="30px">
    ```

  - span: 行内分区标签，共占一行

    <span></span><span></span>

- html5的标准中添加了一些分区标签，作用与div一样，增加了可读写

  - header 头标签
  - footer 脚标签
  - main主题区域标签
  - nav 导航标签





















