# Mybatis框架



# MyBatis不同映射文件中的id是否可以重复？

2022年09月07日 | 来源 : [千自学](http://1000zx.cn/) | 分类 : [MyBatis](http://1000zx.cn/mybatis/)

**可以重复，但是需要映射文件的`namespace`不同**



不同的 Xml 映射文件，如果配置了 `namespace`，那么 `id` 可以重复；如果没有配置 `namespace`，那么 `id` 不能重复。

原因就是 `namespace`+`id` 是作为 `Map<String, MapperStatement>`的 key使用的，如果没有 `namespace`，就剩下 `id`，那么，`id` 重复会导致数据互相覆盖。

有了 `namespace`，自然 `id` 就可以重复，`namespace` 不同，`namespace`+`id` 自然也就不同。

## 目录导航

| 目录                                   | 描述                                                      |
| -------------------------------------- | --------------------------------------------------------- |
| 1 Mybatis简介                          | 简述Mybatis的框架                                         |
| 2 **Mybatis环境搭建**                  | **如何在springBoot创建时，添加Mybatis依赖框架**           |
| 3 **Mybatis 代码应用流程介绍**         | **Mybatis在实际开发中是如何应用的**，具体步骤流程是怎么样 |
| 4 商品管理系统(Mybatis版)+注册登录实现 | 用一个简单案例来描述**Mybatis的实际应用**，便于简要上手   |

## 0 容易遗忘内容

1. [^1]: Mybatis Mapper接口接收数据库查询值的时候，接收值为对象的话，表示是如果查询出来的有值，<font size=5>**那么会新创一个对象去设置对应的属性，如果没有，则不会新创对象，接收的对象为null值**</font>

## 1 Mybatis简介

- Mybatis框架是目前最流行的数据持久层框架,
  - 使用Mybatis框架可以帮助程序员**自动生成JDBC代码,**
  - 程序员只需要通过注解或xml配置文件提供需要执行的SQL语句,以及对象和表的映射关系, Mybatis框架会根据此映射关系和SQL自动生成出JDBC代码,从而提高开发效率 

- Mybatis框架属于ORM框架,
  - Object Relational Mapping 对象关系映射, **指Java对象和数据库中表的对应关系**, Mybatis框架就是通过两者之间的关系 生成的JDBC代码


## 2 Mybatis环境搭建

- 如何使用Mybatis框架?

  - Idea创建工程时需要勾选 **Mybatis Framework**和 **MySQL Drive**r  

  - 创建完工程,如果pom.xml里面的mysql相关依赖报错的话 使用下面的依赖替换掉,刷新maven即可解决

    ```xml
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.15</version>
    </dependency>
    
    ```

  - 在application.properties配置文件中添加连接数据库的信息

    ```properties
    # 数据库连接地址
    spring.datasource.url=jdbc:mysql://localhost:3306/bootdb?characterEncoding=utf8&useSSL=false&serverTimezone=Asia/Shanghai&rewriteBatchedStatements=true
    # 数据库用户名&密码：
    spring.datasource.username=root
    spring.datasource.password=root
    ```

## 3 Mybatis 代码应用流程介绍

- 创建Mapper接口

  - 当前接口使用 **@Mapper**注解修饰

  - 在里面使用注解**@Insert** **@Update @Select @Delete** 注解写对应SQL

  - 里面传递的参数用**#{XXX}** 表示

    - #{XXX}在运行阶段，程序会读取到当前内容时，会自动与下面的方法的参数进行匹配，如果与参数名称不一致，则会与传输的对象进行匹配，调用**setXXX**方法，将当前值进行赋给属性

      ```java
      package cn.tedu.boot04.mapper;
      
      import cn.tedu.boot04.entity.Product;
      import org.apache.ibatis.annotations.*;
      
      import java.util.List;
      
      //此注解是将当前接口设置为映射接口,Mybatis框架会根据此接口中的内容
      //生成对应的实现类在实现类里面生成对应的JDBC代码
      @Mapper
      public interface ProductMapper {
          //#{xxx} 会从方法的参数列表中找到同名变量,
          // 如果没有同名变量则调用对象里面的同名getXXX方法
          @Insert("insert into product values(null,#{title},#{price},#{num})")
          void insert(Product product);
      
          //查询数据, 生成的JDBC代码会自动将查询到的数据封装到Product对象里面
          //并把对象装进List集合响应出来
          @Select("select id,title,price,num from product")
          List<Product> select();
      
          //删除数据
          @Delete("delete from product where id=#{id}")
          void deleteById(int id);
          //修改数据
          @Update("update product set title=#{title},price=#{price}" +
                  ",num=#{num} where id=#{id}")
          void update(Product product);
      
      }
      ```

      

  - 返回值在接收时[^1]

    - 使用 **int接收** 表示改变的行数

    - 使用 List<Product>接收，表示返回商品对象，并将对象添加进结合中

    - 使用Product接收，表示查询出来的值，如果有值则会生成一个商品对象去接收，如果没有，当前对象会为null值 

      例如 **UserMapper**

      ```java
      package cn.tdu.boot9.mapper;
      
      import cn.tdu.boot9.entity.User;
      import org.apache.ibatis.annotations.Insert;
      import org.apache.ibatis.annotations.Mapper;
      import org.apache.ibatis.annotations.Select;
      
      /**
       * @author lixiang
       * @create 2022-12-09 23:26
       */
      @Mapper
      public interface UserMapper {
          /**
           * 根据用户名去查找当前表中的对应用户信息
           *
           * @param username
           * @return
           */
          //u代表的是从数据库中查询回来的信息
          //需要根据返回的信息进行创建对象，如果没有返回信息则不进行对象创建，所以对象为null值
          @Select("SELECT password FROM user WHERE username = #{username}")
          User select(String username);
      
          /**
           * 用户注册
           *
           * @param user
           * @return
           */
          @Insert("INSERT INTO user VALUES(null,#{username},#{password},#{nickname})")
          int reg(User user);
      }
      ```

      

- Controller层调用

  - **@Autowired**

    - Mybatis与Spring框架会生成一个Mapper的实现类对象(当前对象在**@mapper**注解修饰的时候已经实现了JDBC)

    ```java
    package cn.tdu.boot9.controller;
    
    import cn.tdu.boot9.entity.Product;
    import cn.tdu.boot9.mapper.ProductMapper;
    import org.springframework.beans.factory.annotation.Autowired;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;
    
    import java.util.List;
    
    /**
     * @author lixiang
     * @create 2022-12-09 23:26
     */
    @RestController
    public class ProductController {
        /**
         * 生成一个实例去实现当前的Mapper接口并实现里面饿所有方法,用JDBC方式
         */
        @Autowired
        ProductMapper mapper;
    
        /**
         * 新增商品
         * 1、商品传入参数判断
         * 2、调用mybatis直接与数据库对接，新增商品信息
         * 3、根据返回的值判断当前是否新增成功
         * @param product
         * @return
         */
        @RequestMapping("/insert")
        public String insert(Product product) {
            int i = mapper.insert(product);
            if (i > 0) {
                return "添加成功,跳转<a href='/'>主页面</a>";
            }
            return "添加失败,跳转<a href='/'>主页面</a>";
        }
    }
    
    ```

## 4 商品管理系统(Mybatis版) + 注册和登录

### 4.1 准备工作

- 创建boot05工程  , 打3个勾  Web->Spring Web, 搜索my  勾选 Mybatis Framework  Mysql Driver

- 如果pom.xml里面 mysql相关的依赖报错 , 替换成以下依赖

  ```xml
  <dependency>
      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>8.0.15</version>
  </dependency>
  ```

- 在application.properties 里面 把链接数据库的url ,用户名和密码修改掉 

  <img src="https://shoko-photo.oss-cn-hangzhou.aliyuncs.com/img/image-20221210150527441.png" alt="image-20221210150527441" style="zoom:70%;" />

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

  

### 4.2 实现步骤

前置说明:beer:主要简述实现思路，第一个插入模块会结合代码说明，其他模块代码一致就不进行一一列举

#### 添加商品步骤	

- 在首页添加超链接 请求地址 /insert.html

- 创建insert.html 页面  页面中添加form表单 提交地址为/insert 

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

- 创建controller.ProductController, 创建insert方法处理/insert请求, 创建Product实体类, 然后在参数列表处声明

  

- 创建mapper.ProductMapper接口,  在里面添加insert方法 

  ```java
  package cn.tedu.boot04.mapper;
  
  import cn.tedu.boot04.entity.Product;
  import org.apache.ibatis.annotations.*;
  
  import java.util.List;
  
  //此注解是将当前接口设置为映射接口,Mybatis框架会根据此接口中的内容
  //生成对应的实现类在实现类里面生成对应的JDBC代码
  @Mapper
  public interface ProductMapper {
      //#{xxx} 会从方法的参数列表中找到同名变量,
      // 如果没有同名变量则调用对象里面的同名getXXX方法
      @Insert("insert into product values(null,#{title},#{price},#{num})")
      void insert(Product product);
  
      //查询数据, 生成的JDBC代码会自动将查询到的数据封装到Product对象里面
      //并把对象装进List集合响应出来
      @Select("select id,title,price,num from product")
      List<Product> select();
  
      //删除数据
      @Delete("delete from product where id=#{id}")
      void deleteById(int id);
      //修改数据
      @Update("update product set title=#{title},price=#{price}" +
              ",num=#{num} where id=#{id}")
      void update(Product product);
  
  }
  ```

- 在ProductController的insert方法中调用mapper的insert方法 给客户端响应添加完成

  ```java
  package cn.tdu.boot9.controller;
  
  import cn.tdu.boot9.entity.Product;
  import cn.tdu.boot9.mapper.ProductMapper;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.web.bind.annotation.RequestMapping;
  import org.springframework.web.bind.annotation.RestController;
  
  import java.util.List;
  
  /**
   * @author lixiang
   * @create 2022-12-09 23:26
   */
  @RestController
  public class ProductController {
      /**
       * 生成一个实例去实现当前的Mapper接口并实现里面饿所有方法,用JDBC方式
       */
      @Autowired
      ProductMapper mapper;
  
      /**
       * 新增商品
       * 1、商品传入参数判断
       * 2、调用mybatis直接与数据库对接，新增商品信息
       * 3、根据返回的值判断当前是否新增成功
       * @param product
       * @return
       */
      @RequestMapping("/insert")
      public String insert(Product product) {
          int i = mapper.insert(product);
          if (i > 0) {
              return "添加成功,跳转<a href='/'>主页面</a>";
          }
          return "添加失败,跳转<a href='/'>主页面</a>";
      }
  
      /**
       * 1、查找所有商品列表
       * 2、循环遍历集合，返回html页面给浏览器
       * @return
       */
      @RequestMapping("/select")
      public String select() {
          List<Product> list = mapper.select();
          String html = "<table border='1px'><tr><td>商品编号</td><td>商品名称</td><td>商品价格</td><td>商品库存</td><td>商品操作</td></tr>";
          for (Product product : list) {
              html += "<tr>";
              html += "<td>" + product.getId() + "</td>";
              html += "<td>" + product.getTitle() + "</td>";
              html += "<td>" + product.getPrice() + "</td>";
              html += "<td>" + product.getNum() + "</td>";
              html += "<td><a href='/delete?id=" + product.getId() + "'>删除</a></td>";
              html += "</tr>";
          }
          html += "</table>";
          return html;
      }
  
      /**
       * 根据ID删除数据库中对应的商品信息
       * @param id
       * @return
       */
      @RequestMapping("/delete")
      public String delete(Integer id) {
          int i = mapper.delete(id);
          if (i > 0) {
              return "删除成功,跳转<a href='/'>主页面</a>";
          }
          return "删除失败,跳转<a href='/'>主页面</a>";
      }
  
      /**
       * 根据ID更新数据库中对应的商品信息
       * 注意:当前实现方式存在问题，当如何一商品信息为null值时都会改变原有数据库的内部信息
       * 这边并没有对用户不想修改的信息进行非空判断
       * @param product
       * @return
       */
      @RequestMapping("/update")
      public String update(Product product) {
          int i = mapper.update(product);
          if (i > 0) {
              return "修改成功,跳转<a href='/'>主页面</a>";
          }
          return "修改失败,跳转<a href='/'>主页面</a>";
      }
  }
  ```

#### 商品列表步骤

- 在首页添加超链接 请求地址为/select
- 在ProductController里面添加select方法处理/select请求
- 在ProductMapper里面添加select方法, 通过@Select注解修饰 返回值为list集合
- 在ProductController的select方法里面调用mapper的select方法得到list集合,从boot03工程里面把准备html的代码复制到当前工程 这样数据就装进了表格标签里面并且响应给了客户端

#### 删除商品步骤

- 在复制过来的代码中包含删除商品的超链接 请求地址为/delete?id=xxx  
- 在ProductController中创建delete方法处理/delete请求, 在方法中调用mapper的deleteById方法把接收到的id传递过去,然后给客户端响应删除完成
- 实现mapper里面的deleteById方法 

#### 修改商品步骤

- 在首页添加 修改商品的超链接 请求地址为/update.html
- 创建update.html页面 , 在页面中添加form表单, 提交地址为/update, 表单里面四个文本框和一个提交按钮  
- 在ProductController中添加update方法 处理/update请求, 在方法的参数列表处声明Product对象, 用来接收传递过来的数据, 在方法中调用mapper的update方法把product对象传递过去, 最后给客户端响应 修改完成!
- 实现mapper里面的update方法 

#### 用户注册步骤

- 在首页添加注册和登录的超链接 请求地址分别是/reg.html和/login.html
- 创建reg.html注册页面 ,页面中添加form表单请求地址为/reg 表单中三个文本框和一个提交按钮,  
- 创建UserController,并添加reg方法处理/reg请求, 创建User实体类, 在方法的参数列表处声明用来接收传递过来的用户信息 
- 创建UserMapper 接口, 在里面添加insert方法
- 在UserController的reg方法中调用mapper的insert方法  给客户端响应注册成功

#### 用户登录步骤

- 创建login.html页面在页面中添加form表单 提交地址为/login,表单中有一个文本框,一个密码框和一个提交按钮  
- 在UserController里面添加login方法处理/login请求, 参数列表处声明User对象接收传递过来的用户名和密码, 在方法中调用mapper.selectByUsername方法返回值为User对象, 判断User对象的情况给客户端响应对应的内容
- 实现mapper里面的selectByUsername方法  
- 在UserController的reg方法中  注册之前 调用mapper的selectByUsername方法查询是否有此用户名, 如果查询到了内容给客户端响应 用户名已存在, 这样注册前就做了去重操作了 















