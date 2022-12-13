# 																													SpringBoot框架工程搭建及常见问题处理

## 目录导航

| 目录                              | 描述                                                 |
| --------------------------------- | ---------------------------------------------------- |
| 0 容易遗忘内容                    | 简要记录当前文件内的重点 易遗落问题                  |
| 1 工程maven配置                   | IDEA 配置maven                                       |
| 2 SpringBoot工程创建              | IDEA内部创建SpringBoot工程                           |
| 3 服务器 \| 服务器软件简介        | 简介服务器、服务软件基本概念                         |
| 4 SpringBoot 框架                 | 简介springBoot作用 与**几种创建前提约束**            |
| 5 **springBoot注解与常见易错点**  | springBoot几个基本注解 与浏览器 中 `/`路径代表的含义 |
| 6 SpringBoot 商品管理系统功能实现 | 商品管理系统JDBC实现方式实现 代码示例                |



## 0 容易遗忘内容

1. [^1]:springBoot 基本注解、浏览器 请求路径带`/` 与不带` /`区别等

2. []

## 1 工程Maven配置



- maven配置前检查当前默认maven环境是否具备

  - 找到.m2文件夹  ,检查里面是否有settings.xml配置文件
  
  <img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207143544816.png" alt="image-20221207143544816" style="zoom:50%;" />

<img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207143557666.png" alt="image-20221207143557666" style="zoom:50%;" />

- 如果.m2文件夹下面没有setting.xml配置文件,则需要从苍老师文档服务器下载此文件解压出settings.xml文件保存到.m2文件夹下面 

  <img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207143715138.png" alt="image-20221207143715138" style="zoom:50%;" />

## 2 SpringBoot工程创建

- 创建Spring Initalizer工程 
  - 修改URL为**start.aliyun.com**
  - 修改工程Name (**项目名称**)
  - Group (**项目域名**)
  - Java (**当前项目jdk版本**)

<img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207144350156.png" alt="image-20221207144350156" style="zoom:50%;" />



- 勾选 Web->Spring Web    然后点击finish

- 创建完工程后 检查Build里面是否出现绿色对勾, 如果有红色信息代表工程创建出错
  - 此时点击Maven里面的刷新Maven，用于下载更新pom文件依赖jar包

<img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207145019333.png" alt="image-20221207145019333" style="zoom:50%;" />



- 如果刷新完Maven后还是不行
  - 则 删除.m2文件夹下的repository文件夹 然后再次刷新maven, 一般可以解决
  - 如果仍然没有解决则创建一个新工程 重新测试, 如果还是不行, 则联系项目经理 现场 或远程 一对一解决


- 出现以下绿色对勾 说明工程创建成功!

  <img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207145247085.png" alt="image-20221207145247085" style="zoom:50%;" />



## 3 服务器 | 服务软件简介

功能图

​	![image-20221207151633040](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207151633040-16706416978631.png)

### 3.1 什么是服务器

- 服务器就是一台高性能的电脑
- 在电脑上安装了提供XXX服务的软件, 这台电脑就可以成为XXX服务器 
- 举例: 
  - 在电脑上安装了提供邮件收发服务的软件, 这台电脑就称为邮件服务器
  - 在电脑上安装了提供文件上传下载服务的软件, 就称为FTP服务器   
  - 在电脑上安装了数据库软件, 就称为数据库服务器  
  - 在电脑上安装了Web服务软件, 就称为Web服务器

### 3.2 Web服务软件

- 什么是Web服务软件?

  Web服务软件不具备任何业务功能, 可以理解为是一个容器, 用来装实现具体业务功能的组件(Servlet是实现具体业务功能的组件,Controller的作用是将多个有相关性的Servlet进行了一个整合, 否则一个工程里面的Servlet数量太多, 每一个业务对应一个Servlet)

- Web服务软件做了哪些事儿?

  - 负责搭建底层的网络连接  

  - 负责根据客户端请求的静态资源路径找到对应的静态资源文件,并响应给客户端 

    `http://localhost:8080/reg.html`  

  - 负责根据客户端请求的动态资源路径找到对应的Controller以及里面的方法并且调用

    `http://localhost:8080/loginUser`    -> UserController 里面的login方法

- 在创建SpringBoot工程时,如果勾选了Web->Spring Web  则会在工程中内置一个Tomcat Web服务软件

### 3.3 后端的SSM三大框架

- SpringMVC: 从第二阶段开始接触 一直讲到第四阶段
- Spring: 第四阶段
- Mybatis: 从第三阶段到第四阶段
- 这三个框架的作用是提高后端程序员实现具体业务功能时的开发效率     

## 4 SpringBoot框架作用与约束

### 4.1 SpringBoot的作用

> - **没有SpringBoot**:
>   - 在创建的空工程中需要引入其它框架时,除了要在pom.xml文件里面添加大量的依赖信息以外,还需要添加对应的配置文件,在配置文件里面要书写大量的配置信息,这些工作都是由我们程序员完成的
> - **有了springBoot**
>   - 引入其它框架只需要在创建工程时打钩的方式引入其它框架, 不需要添加配置文件和配置信息 大大提高了构建工程的效率 

### 4.2 如何处理客户端的静态资源请求(定制约束)

- 静态资源文件放在工程的**static**文件夹下面
  - 约束: 静态文件页面需要在static目录下


### 4.3 如何处理客户端的动态资源请求(定制)

- 在**工程自带的包里面创建controller**包,在里面创建HelloController  在Controller里面添加处理请求的方法 
  - 约束:controller运行类需要以springBoot运行类的包为父包


### 4.4 客户端发出请求的几种方式:

1. 在浏览器的地址栏中书写请求路径 回车后发出请求
2. 通过页面中的超链接发出请求 
3. 通过页面中的form表单发出请求 

### 4.5 404错误码解决方案

- 代表找不到资源
- 两种情况:
  - 静态资源找不到:    请求的是页面或文件
    - 检查客户端请求的路径是否正确
    - 检查静态资源文件所在位置是不是正确(一般在static文件夹下面) 
    - 如果以上都正确, ReBuild工程后 重启工程再测试
  - 动态资源找不到:    请求的是Controller
    - 检查客户端请求的路径是否正确
    - 检查controller包是否创建在工程自带的包里面 
    - 检查Controller注解是否添加
    - 检查RequestMapping注解里面处理的路径和客户端发出的请求路径是否一致
    - 如果以上都正确,ReBuild工程后 重启工程再测试

## 5 SpringBoot 注解与常见易错点[^1]

### 5.1 注解 

####   @ResponseBody注解

- 添加此注解后,可以通过返回值的方式给客户端响应数据

  ```java
  @RequestMapping("/reg")
  @ResponseBody
  public String reg(User user){
      System.out.println("user = " + user);
      //获取数据库连接
      try (Connection conn = DBUtil.getConnection()){
          //准备插入数据的SQL语句
          String sql = "insert into user values(null,?,?,?)";
          //创建执行SQL语句的对象
          PreparedStatement ps = conn.prepareStatement(sql);
          //替换SQL语句中的?
          ps.setString(1,user.getUsername());
          ps.setString(2,user.getPassword());
          ps.setString(3,user.getNickname());
          //执行SQL语句
          ps.executeUpdate();
      } catch (SQLException throwables) {
          throwables.printStackTrace();
      }
  
      return "注册成功!";
  }
  ```

#### @Controller注解

- 标注在Controller层上，让springBoot在查找类时，表示当前为处理请求的类，进行纳入

#### @RestController注解

- 使用此注解后 相当于每一个处理请求的方法上面都添加了**@ResponseBody**注解

#### @RequestMapping ("/url")注解

- 标注在方法上，用于浏览器请求报文中的请求路径

### 5.2 html 页面中 `/url` 与 `url`的区别

- `url`为相对路径

  - 相对于当前页面所处的位置，把最后面的路径替换为url
    - 当前页面路径
      - `http://localhost:8080/abc/index.html`
    - 跳转后路径
      - `http://localhost:8080/abc/url`

- `/url`为绝对路径

  - 工程根路径`http://127.0.0.1:8080` + /url

- `http://localhost:8080/hello`绝对路径

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <h1>工程首页</h1>
  <!--相对路径: 相对于当前页面所处位置
  http://localhost:8080/index.html
  http://localhost:8080/hello
  http://localhost:8080/abc/index.html
  http://localhost:8080/abc/hello
  -->
  <a href="hello">相对路径</a>
  <!--绝对路径里面第一个/ 代表的是工程的根路径http://localhost:8080/
  /hello =   http://localhost:8080/hello
  推荐使用这种绝对路径, 相对路径和当前页面所处位置有关系,如果页面位置发生改变
  很有可能导致页面的超链接失效
  -->
  <a href="/hello">绝对路径1</a>
  <!--下面这种绝对路径 一般只有访问站外资源时使用-->
  <a href="http://localhost:8080/hello">绝对路径2</a>
  <h1>通过form表单发出请求</h1>
  <form action="/hello">
      <input type="text" name="info">
      <input type="submit">
  </form>
  <hr>
  <a href="/param.html">传参测试</a>
  <a href="/bmi.html">BMI测试</a>
  
  </body>
  </html>
  ```

  

### 5.3 页面修改后，刷新工程快捷键

- 如果只是对页面内容进行了改动 不需要重启工程, 只需要<font size=6>**ctrl+shift+f9**</font>即可

### 5.4 Controller中接收参数的几种方式

1. **通过`HTTPServletRequest`对象获取参数**    

   ![image-20221207172123286](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207172123286.png)

2. **通过在方法的`参数列表处声明的方式`接受参数**

   ![image-20221207172147006](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207172147006.png)

3. **通过在方法的参数列表处声明`自定义对象`的方式,将接收到的参数封装到对象里面**

   ![image-20221207173532461](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221207173532461.png)

## 6 SpringBoot 商品管理系统功能实现(JDBC方式)

### 实现功能说明

- 使用**springBoot**作为系统框架，采用**JDBC**连接数据库的形式，根据前端页面传递的参数信息，对数据库里面的商品数据进行增删改查与查询操作。
- 项目实现结构图
  - ![image-20221210144716615](https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221210144716615.png)

### 准备工作

- 创建工程boot03工程   打钩 WEb->Spring Web

- 建库

  ```sql
  create database bootdb charset=utf8;
  
  use bootdb;
  
  create table user(id int primary key auto_increment, username varchar(50),
  
  password varchar(50),nickname varchar(50));
  ```

- 建表:

  ```sql
  use bootdb;
  
  create table product
  (id int primary key auto_increment,
   title varchar(50),
   price double(10,2),
   num int);
  ```

- 把上一个工程中的util包以及DBUtil 复制到boot03工程

  DBUtil: 用于获取数据库连接的连接池

  ```java
  package com.tedu.boot2.util;
  
  import com.alibaba.druid.pool.DruidDataSource;
  
  import java.sql.Connection;
  import java.sql.SQLException;
  
  /**
   * @author lixiang
   * @create 2022-11-24 11:50
   * 管理数据库连接
   */
  public class DBUtil {
      //阿里提供的连接池(重复使用连接，管理连接梳理)
      private static DruidDataSource dds;
      /**
       * 静态方法初始化数据库运行实例
       */
      static{
          try {
              //1.获取数据库驱动运行类实例
              //Class.forName("com.mysql.cj.jdbc.Driver");
              //1、设置数据库用户名，密码，最大连接数，初始连接数,连接数据的URL
              dds = new DruidDataSource();
              dds.setUsername("root");
              dds.setPassword("kelan");
              dds.setUrl("jdbc:mysql://localhost:3306/bootdb?characterEncoding=utf8&useSSL=false&serverTimezone=Asia/Shanghai&rewriteBatchedStatements=true");
              dds.setInitialSize(10);
              dds.setMaxActive(20);
          } catch (Exception e) {
              e.printStackTrace();
          }
      }
  
      /**
       * 获取MySQL数据库连接(库名、连接信息需要进行自定义配置)
       * @return
       */
      public static Connection getConnection() throws SQLException {
          //2、获取数据库连接
          //return DriverManager.getConnection("jdbc:mysql://localhost:3306/birdbootdb?characterEncoding=utf8&useSSL=false&serverTimezone=Asia/Shanghai&rewriteBatchedStatements=true", "root", "kelan");
          return dds.getConnection();
      }
  }
  
  ```

  

- 把上一个工程中和数据库相关的两个依赖 复制到boot03工程 刷新maven

  - Mysql依赖
  - 线程池连接依赖
  - lombok依赖

  ```xml
  <!-- Mysql依赖 -->
  <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.15</version>
  </dependency>
  <!-- 德鲁伊连接池依赖 -->
  <dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>druid</artifactId>
      <version>1.1.21</version>
  </dependency>
  
  <!-- lombok依赖 实体类getset等方法注解创建 -->
  <dependency>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
      <version>1.18.16</version>
  </dependency>
  ```

  

  - 创建首页index.html页面  运行工程 `http://127.0.0.1:8080` 访问 检查是否可以正常启动

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <h1>商品管理系统(Mybatis版)</h1>
  <a href="/insert.html">添加商品</a>
  <a href="/select">商品列表</a>
  <a href="/update.html">修改商品</a>
  <hr>
  <a href="/reg.html">注册</a>
  <a href="/login.html">登录</a>
  </body>
  </html>
  ```

​			

### 实现步骤

 前置说明:beer:主要简述实现思路，第一个插入模块会结合代码说明，其他模块代码一致就不进行一一列举

- #### 添加商品步骤:

  - 在首页添加超链接  请求地址为/insert.html页面

  - 创建insert.html页面  在页面中添加form表单请求地址为/insert 页面中是三个文本框和一个提交按钮

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
    <h1>添加商品页面</h1>
    <form action="/insert">
      <input type="text" name="title" placeholder="标题">
      <input type="text" name="price" placeholder="价格">
      <input type="text" name="num" placeholder="库存">
      <input type="submit" value="添加">
    </form>
    </body>
    </html>
    ```

  - 创建Product实体类

    ```java
    package cn.tedu.boot6.entity;
    
    import lombok.Data;
    
    /**
     * @author lixiang
     * @create 2022-12-08 20:16
     */
    @Data
    public class Product {
        private Integer id;
        private String title;
        private Double price;
        private Integer num;
    }
    ```

  - 创建controller.ProductController 在里面添加insert方法处理/insert请求 

    

  - 在insert方法的参数列表处声明Product对象 用来接收传递过来的商品信息,  方法里面通过jdbc代码把商品信息保存到商品表里面

    ```java
    package cn.tedu.boot03.controller;
    
    import cn.tedu.boot03.entity.Product;
    import cn.tedu.boot03.util.DBUtil;
    import org.springframework.stereotype.Controller;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.ResponseBody;
    import org.springframework.web.bind.annotation.RestController;
    
    import java.sql.Connection;
    import java.sql.PreparedStatement;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.util.ArrayList;
    import java.util.List;
    //使用此注解后 相当于每一个处理请求的方法上面都添加了@ResponseBody注解
    @RestController
    public class ProductController {
        @RequestMapping("/insert")
        public String insert(Product product){
            //soutp 输出数据
            System.out.println("product = " + product);
            //获取数据库连接
            try (Connection conn = DBUtil.getConnection()){
                //创建执行的SQL语句
                String sql = "insert into product values(null,?,?,?)";
                //创建执行SQL语句的对象
                PreparedStatement ps = conn.prepareStatement(sql);
                //替换掉SQL语句里面的?
                ps.setString(1,product.getTitle());
                ps.setDouble(2,product.getPrice());
                ps.setInt(3,product.getNum());
                //执行SQL语句
                ps.executeUpdate();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            return "添加完成!<a href='/'>返回首页</a>";
        }
    
        @RequestMapping("/select")
        public String select(){
            //创建一个集合 用来装商品对象
            ArrayList<Product> list = new ArrayList<>();
            //获取连接
            try (Connection conn = DBUtil.getConnection()){
                String sql = "select id,title,price,num from product";
                PreparedStatement ps = conn.prepareStatement(sql);
                //执行查询
                ResultSet rs = ps.executeQuery();
                while(rs.next()){
                    int id = rs.getInt(1);
                    String title = rs.getString(2);
                    double price = rs.getDouble(3);
                    int num = rs.getInt(4);
                    //把查询到的数据封装到对象里面
                    Product p = new Product();
                    p.setId(id);
                    p.setTitle(title);
                    p.setPrice(price);
                    p.setNum(num);
                    //把对象装进list集合
                    list.add(p);
                }
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            //把list集合里面的数据装进一个table标签里面
            String html = "<table border='1'>";
            html+="<tr><th>id</th><th>标题</th><th>价格</th><th>库存</th><th>操作</th></tr>";
            //遍历商品集合
            for (Product p : list) {
                html+="<tr>";
                html+="<td>"+p.getId()+"</td>";
                html+="<td>"+p.getTitle()+"</td>";
                html+="<td>"+p.getPrice()+"</td>";
                html+="<td>"+p.getNum()+"</td>";
                //             /delete?id=5
                html+="<td><a href='/delete?id="+p.getId()+"'>删除</a></td>";
                html+="</tr>";
            }
            html+="</table>";
            //此时html里面是表格标签+数据
            return html;  // setContentType("text/html;charset=utf-8")
        }
    
        @RequestMapping("/delete")
        public String delete(int id){
            System.out.println("id = " + id);
            try (Connection conn = DBUtil.getConnection()){
                String sql = "delete from product where id=?";
                PreparedStatement ps = conn.prepareStatement(sql);
                ps.setInt(1,id);
                ps.executeUpdate();//执行SQL语句
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            return "删除完成!<a href='/select'>返回列表页面</a>";
        }
    
        @RequestMapping("/update")
        public String update(Product product){
            System.out.println("product = " + product);
            try(Connection conn = DBUtil.getConnection()) {
                String sql =
                        "update product set title=?,price=?,num=? where id=?";
                PreparedStatement ps = conn.prepareStatement(sql);
                ps.setString(1,product.getTitle());
                ps.setDouble(2,product.getPrice());
                ps.setInt(3,product.getNum());
                ps.setInt(4,product.getId());
                ps.executeUpdate();//执行修改
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            return "修改完成!<a href='/select'>返回列表页面</a>";
        }
    }
    ```

- #### 商品列表页面步骤:

  - 在首页添加超链接 请求地址为/select   动态请求
  - 在ProductController里面添加select方法处理/select请求, 方法中准备一个List集合,把查询到的所有数据封装到Product对象里面 然后再装进List集合里面,准备一个装html和数据的字符串,把表格标签和集合里面的数据装进去,  最后把这个字符串响应给客户端

- #### 删除商品步骤:

  - 在拼接表格标签时 添加一个操作列,  然后每一行里面添加一个删除的超链接,请求地址为/delete?id=xxx    
  - 在Controller里面添加delete方法处理/delete 请求, 接收传递过来的id , 在方法中通过jdbc代码把id对应的数据删除即可,  最后响应给客户端 删除完成!

- #### 修改商品步骤:

  - 在首页index.html页面中添加修改超链接 请求地址为/update.html
  - 创建update.html页面, 在页面中添加form表单 请求地址为/update 在表单里面添加四个文本框和一个提交按钮 
  - 在ProductController中添加update方法处理/update请求, 在参数列表处声明Product对象用来接收传递过来的参数,  在方法中通过JDBC代码把数据库里面的数据修改成Product对象里面的数据, 最后给客户端响应修改完成.
