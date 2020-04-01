Big Data --Senior

## VScode

vscode 目录树的缩进设置：

[![img](pic/c2fdfc039245d6880c54608eabc27d1ed21b2442.png)](https://iknow-pic.cdn.bcebos.com/c2fdfc039245d6880c54608eabc27d1ed21b2442)

文件-设置-首选项-搜索 treein ，改一下控制树缩进就好

### html

插件：

```
HTML CSS Support
HTML Snippets
HTML Preview
open in browser
```

## IDEA

```
Ctrl + Shift + E：访问最近写代码的位置
```



## Java Web

BS架构：Browser/Server，有浏览器端/客户端 和服务器

CS架构：Client/Server，有安装包/客户端和服务器

![1583930684414](/home/cxy/%25E6%2596%2587%25E6%25A1%25A3/Big-data/pic/1583930684414.png)

```mermaid
graph LR
	subgraph 客户端/Browser
	HTML/CSS/JS
	end
	
	subgraph 服务器端/Tomcat
	Servlet
	end
	
	HTML/CSS/JS --HTTP协议--> Servlet
	Servlet --HTTP协议--> HTML/CSS/JS

	
```

### 1. HTML

#### 1. 什么是HTML

1. HTML指的==超文本标记语言(Hyper Text Markup Language)==，是一种用来描述网页的语言。超文本指的是除了可以包含文字之外，还可以包含图片、链接、音乐、视频、程序等内容。

2. HTML网页的组成

   ![1583930847738](/home/cxy/%25E6%2596%2587%25E6%25A1%25A3/Big-data/pic/1583930847738.png)

3. 常用的HTML标签

   1. html     根标记

   2. head     头标记

   3. body     体标记

   4. a           超链接

      ```html
      <!-- 超链接  href:可以指定应用内或者是应用外的任意地址 -->
       <a href="http://www.baidu.com">点我查看</a>
      ```
   
      ==相对路径：==
   
      ```html
      <!--   ../../ 表示上两级目录    -->
      <a href="../../target.html">hhh</a>
      ```
   
      ==target==属性：设置要跳转的页面在何处打开
   
   >_self : 默认，在当前页面打开
      >
   >_blank: 在新的标签页打开
   
      ==base== 可 设置全局的target属性
   
      ```html
   <base target="_blank">
      ```

      
   
   5. form     表单
   
      - 使用form标签创建一个表单
   
      - action属性：指定服务器地址（表单将被提交的地址）
   
      - method属性：指定表单的请求方式
   
        > get：默认值，发送一个GET请求，用户输入的数据通过地址栏传输
        >
        > post：发送一个POST请求，用户输入的数据通过请求体进行传输
        >
        > 区别：get的地址栏会显示name属性的键值对，post不会显示。但是按F12，点network监听一下，header里会显示用户和密码，http协议本身就是不安全的
   
      
   
      - 表单中的表达项用input表示，不同的表单项通过type指定，value属性指定按钮上显示的文字 
      - 用户输入数据通过name属性进行携带，并以键值对的形式发送到服务器，多个键值对之间用&分隔
      -   键值对如：`username=cxy&password=123456 `，name相当于键，用户输入的内容为值
   
      ```html
      <!-- 表单: 收集用户的信息，提交到后台服务器 -->
      <form action="success.html" method="POST">
          
          用户名：<input type="text" name="username"><br/>
          密码：<input type="password" name="password"><br/>
          <input type="submit" value="登录">
      
      </form>
      ```
   
   6. table     表格
   
      - tr   行
   
      - th   标题列  自带居中并加粗的效果
   
      - td   普通列
   
      - colspan 跨列合并单元格
   
      - rowspan 跨行合并单元格
   
      - align = “center” 居中
   
        ```html
        <table border = "lpx" align="center" width = "60" cellspacing = 0>
                <tr>
                    <th>ID</th>
                    <th>name</th>
                    <th>gender</th>
                    <th>age</th>
                    <th>birthday</th>
        
                </tr>
                <tr align="center">
                    <td align="center">100</td>
                    <td>cxy</td>
                    <!-- 跨行合并单元格 -->
                    <td rowspan="2">female</td>
                    <td>23</td>
                    <td>-</td>
                </tr>
        
                <tr align="center">
                    <td align="center">100</td>
                    <td>cc</td>
                    <td>female</td>
                    <td>23</td>
                    <td>-</td>
                </tr>
        
                <tr align="center">
                    <td align="center">100</td>
                    <td>wwh</td>
                    <td>male</td>
                    <!-- 跨列合并单元格 设置colspan属性 -->
                    <td colspan="2" align="center"> 22</td>
                </tr>
        
            </table>
        ```

### 2. CSS

- 整个标签

  > 标签选择器

- 标签里面设置属性

  > id选择器
  >
  > 类选择器

- 分组选择器

  > 为不同类别的选择器设置相同的属性

```css
<head>
    <style type="text/css">
    /*标签选择器*/
    h1{
        color: yellow;
    }
    h2{
        background-color: antiquewhite;
    }

    /*id选择器
      格式：#id属性值
    */
    #p1{
        color: aqua;
    }

    /*类选择器
      格式：.class属性值
    */
    .p2{
        color: yellowgreen;
    }

    /*分组：将各个选择器用逗号分隔*/
    #p1,.p2{
        font-size: 22px;
    }
    </style>
</head>
```

颜色的表示方式：

1. 英文单词：red

2. rgb 值 ：rgb(250,0,0)

3. 使用 16 进制数：#FF0000  不区分大小写，从左到右两位一组，分别表示 R G B

   

### 3. Web

 [01_JavaWeb.html](ref/01_JavaWeb.html) 

#### web服务器

服务器主要用来接收或响应客户端发来的请求，当前使用最广的服务器：==Tomcat==

修改端口号：修改安装目录下的 `conf/service.xml` 里的启动端口号8080

#### 第一个web动态工程

[IDEA创建web工程](<https://www.cnblogs.com/wfhking/p/9395774.html>)

1. 运行web工程会自动展示此页面，工作空间内的此页面会被自动copy到服务器，然后在服务器中访问web/index.html页面

2. web/WEB-INF下需要自己建两个文件夹：**classes**（设置输出路径到此处,运行工程后工作空间内的类会加载到此处）, **lib**（设置为 dependency 后，用来放工程jar包）

3. 工程中服务器的工作路径选择 tomcat 的源路径。Eclipse中==web 目录会被 copy 到 tomcat 的 webapps下，同时把 web 改为工程名==。IDEA 中需自己设置路径，即 project structure 中 artifact 的目录。

4. index页面中按 F12，刷新看index的Headers 

   报文：分为 行、头、体

   > 浏览器发给服务器的是 ==请求报文==，分为请求行、请求头、请求体
   >
   > ```
   > //请求头
   > Request Headers
   > //请求行
   > GET /Web_tomcat_war_exploded/ HTTP/1.1
   > //请求体
   > Host: localhost:8080
   > Connection: keep-alive
   > Cache-Control: max-age=0
   > Upgrade-Insecure-Requests: 1
   > User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.149 Safari/537.36
   > Sec-Fetch-Dest: document
   > Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
   > Sec-Fetch-Site: none
   > Sec-Fetch-Mode: navigate
   > Sec-Fetch-User: ?1
   > Accept-Encoding: gzip, deflate, br
   > Accept-Language: zh-CN,zh;q=0.9
   > Cookie: Idea-c3466856=bdab302f-9076-4c60-a7e9-778b2a6ffd03
   > If-None-Match: W/"714-1584880762014"
   > If-Modified-Since: Sun, 22 Mar 2020 12:39:22 GMT
   > ```
   >
   > 服务器发给浏览器的是 ==响应报文==，分为响应行、响应头、响应体
   >
   > ```
   > //响应头
   > Response Headers
   > //响应行
   > HTTP/1.1 200
   > //响应体
   > Date: Sun, 22 Mar 2020 12:43:30 GMT
   > Accept-Ranges: bytes
   > ETag: W/"714-1584880762014"
   > Last-Modified: Sun, 22 Mar 2020 12:39:22 GMT
   > Content-Type: text/html
   > Content-Length: 714
   > ```

#### 3.1 登录功能实现—LoginServlet

1)        Servlet  

2)        Request请求对象

3)        Response响应对象

##### 1 什么是Servlet

1. Servlet是Sun公司制定的一套技术标准，包含与Web应用相关的一系列接口，是Web应用实现方式的<u>宏观解决方案</u>。而具体的 ==Servlet 容器（Tomcat）负责提供标准的实现==。

2. Servlet作为服务器端的一个组件，它的本意是“服务器端的小程序”（==Tomcat中会有多个Servlet，每一个Servlet都负责处理一件事，如登录、注册==）。Servlet的实例对象由Servlet容器负责创建；Servlet的方法由容器在特定情况下调用；Servlet容器会在Web应用卸载时销毁Servlet对象的实例。

   ```mermaid
   graph LR
   
   	Cient --HTTP--> Servlet_登录
   	Servlet_登录 --HTTP--> Cient
   	subgraph Tomcat
   	Servlet_注册
   	Servlet_登录
   	Servlet_忘记密码
   	...
   	end
   ```

3. 简单可以理解为  ==Servlet就是用来处理客户端的请求的== 

##### 2 Servlet开发规则

新建一个Servlet

##### 3 Servlet类的相关方法

- doGet：处理客户端的get方式的请求

- doPost：处理客户端的post方式的请求

- service：根据具体的请求方式去调用对应的doGet、doPost 方法

  >  ①      在Servlet的顶层实现中，在service方法中调用的具体的doGet或者是doPost
  >
  >  ②      在实际开发Servlet的过程中，可以选择重写doGet以及doPost  或者 直接重写service方法来处理请求。

#####4 Servlet在web.xml中的配置

```xml
<!--注册Servlet-->
<servlet>
  <!-- 给Servlet取名，一般写类名.取的名字前后必须一致-->
  <servlet-name>helloServlet</servlet-name>
  <!-- 配置Servlet实现类的全类名，Servlet容器会利用反射帮我们创建对象-->
  <servlet-class>com.atguigu.servlet.helloServlet</servlet-class>
</servlet>
    
<!--映射Servlet。如果用户发送多个请求，需要知道是谁发的-->
<servlet-mapping>
  <servlet-name>helloServlet</servlet-name>
  <!--配置映射的请求地址,在浏览器的地址栏输入MyFirstServlet的时候才发起请求-->
  <url-pattern>/MyFirstServlet</url-pattern>
</servlet-mapping>
```

Servlet 3.0之后可以在Servlet中使用注解直接配置URL。需要在Servlet中导入`import javax.servlet.annotation.WebServlet;` 。然后使用

```java
@WebServlet(name = "AutoServlet",urlPatterns = "/AutoServlet")
//注意urlPatterns那里要写/  
//也可以如下：
@WebServlet("/AutoServlet")
```

==name  和 urlPatterns 对应 web.xml 中的 <url-name> 和 <url-pattern>== 

就可以直接配置了，然后通过所输入的URL可以直接访问到。

##### 5 request 和 response 的使用

==request== 的作用

- 获取请求参数

- 获取项目虚拟路径

- 转发

  ![img](pic/转发.png)

==response== 的作用

- 给浏览器响应一个字符串或一个页面
- 重定向

==转发和重定向的区别：==

1. 转发只发一次请求，即AutoServlet。重定向发了2次请求：AutoServlet 和 success.html
2. 转发浏览器地址栏无变化，重定向有变化
3. 转发可以访问WEB-INF目录下的资源，==重定向不可以访问WEB-INF目录下的资源==
4. 转发可以共享request域中的内容，重定向不可以

##### 6. 登录之获取链接

```mermaid
graph LR
	subgraph 前端
	表单
	end
	
	subgraph 服务器
	Servlet
	end
	
	subgraph 数据库
	MySql
	end
	
	表单 --> Servlet
	Servlet --> 表单
	
	Servlet --JDBC--> MySql
```

##### 7. 绝对路径与相对路径

因为在login中使用 相对路径 ../LoginServlet 导致二次登录时又到了上级目录，所以使用绝对路径来解决此问题

绝对路径

- 以 ==/ 开头的路径即为绝对路径==     / 代表的意义：

  > 1. 如果地址由浏览器解析， / 代表： http://localhost:8080/。如：
  >
  >    > - html标签中的路径，如：
  >    >
  >    >   > - a 标签中的 href 属性中的路径
  >    >   > - form 标签中的 action 属性中的路径等
  >    >
  >    > - 重定向中的路径
  >    >
  >    >   
  >
  > 2. 如果由服务器解析， / 代表： http://localhost:8080/Web_Exercise_war_exploded/ (即服务器中项目的地址。注意==不要随便改tomcat自动创建的URL地址==，如：http://localhost:8080/Web_Exercise_war_exploded/，不要强行去掉_war_exploded，就算把artifact中的路径一起改也不行），如：
  >
  >    > - web.xml中url-pattern标签中的路径
  >    > - 转发中的路径
  >
  > 

- ==head 里==的 base 标签中的href可以将相对路径变为绝对路径，因为它会加到body里href属性里的地址前面

  	```html
    	<head>
    	  <meta charset="UTF-8">
    	  <title>Insert title here</title>   
    	  <base href="http://localhost:8080/Web_Exercise_war_exploded/"></head>
  ```

index.html , login.html, login_success.html , LoginServlet.java 中的路径也需改为绝对路径

#### 3.2 登录页面中的错误提示

- JSP页面
- EL 表达式
- js 的简单应用

##### 1. JSP

- JSP全称Java Server Pages，顾名思义就是**运行在java服务器中的页面**，也就是在我们JavaWeb中的动态页面，其==本质就是一个Servlet==。
- 其本身是一个动态网页技术标准，它的主要构成有HTML网页代码、Java代码片段、JSP标签几部分组成，后缀是 .jsp
- 相比于Servlet，JSP更加善于处理显示页面，而Servlet跟擅长处理业务逻辑，两种技术各有专长，所以一般我们会将Servlet和JSP结合使用，Servlet负责业务，JSP负责显示。
- 一般情况下， 都是Servlet处理完的数据，转发到JSP，JSP负责显示数据的工作
- JSP的基本语法:

- 本质上就是一个Servlet

  

  **JSP基本语法**

- 1. ==JSP脚本片段== 

     作用：用来在里面写Java代码

     ```jsp
     <!-- 1.JSP脚本片段
     		作用：用来在里面写Java代码
     	 -->
     	 <%
     	 	for(int i = 0 ; i < 5 ; i ++){
     	 		//out.print("今天天气好晴朗，处处好风光！");
     	 %>		
     	 <h2>今天天气好晴朗，处处好风光！</h2>
     	 <%
     	 	}
     	 %>
     ```

  2. ==JSP表达式==

     - - 作用：用来输出对象

     - - ```jsp
         <%="我是通过JSP表达式输出的" %>
         ```

  3. JSP 的隐含对象

     - out（JspWriter）：相当于response.getWriter()获取的对象，用于在页面中显示信息。
     - config（ServletConfig）：对应Servlet中的ServletConfig对象。
     - page（Object）：对应当前Servlet对象，实际上就是this。
     - ==pageContext==（PageContext）：当前页面的上下文，也是一个域对象。
     - exception（Throwable）：错误页面中异常对象
     - ==request==（HttpServletRequest）：HttpServletRequest对象
     - response（HttpServletResponse）：HttpServletResponse对象
     - ==application==（ServletContext）：ServletContext对象
     - ==session==（HttpSession）：HttpSession对象

     只需要掌握高亮的4个域对象

  4. ==JSP 的四个域对象==

     ==这4个域对象有不同的生命周期==

     - page域

       > 范围：当前页面（页面关掉 对象消失）
       > ==对应的域对象==：即用来调用域内方法的对象
       >
       > > page对应的域对象 ： pageContext
       >
       > 域对象的类型：PageContext

     - request域

       > 范围：当前请求（一次请求，转发还是一次请求，重定向是新的请求）
       > 对应的域对象：request
       > 域对象的类型：HttpServletRequest

     - session域

       > 范围：当前会话（一次会话，只要浏览器不关闭都可以拿到它的请求）
       > 对应的域对象：session
       > 域对象的类型：HttpSession

     - application域

       >范围：当前 Web 应用（服务器关掉应用停止）
       >对应的域对象：application
       >域对象的类型：ServletContext

     

     四个域对象都以下三个方法：

     - void setAttribute(String key , Object value)
     - Object getAttribute(String key)
     - void removeAttribute(String key)

     ```jsp
     <%
     	 	pageContext.setAttribute("pageKey", "pageValue");
     	 	request.setAttribute("reqKey", "reqValue");
     	 	session.setAttribute("sessKey", "sessValue");
     	 	application.setAttribute("appKey", "appValue");
     %>
     	 <h1>在当前页面中获取四个域中的属性值</h1>
     	 page域中的属性值：<%=pageContext.getAttribute("pageKey") %><br>
     	 request域中的属性值：<%=request.getAttribute("reqKey") %><br>
     	 session域中的属性值：<%=session.getAttribute("sessKey") %><br>
     	 application域中的属性值：<%=application.getAttribute("appKey") %><br>
     ```

     

     四个域对象的使用规则：能用小的就不用大的

     

**登录失败后添加错误提示**

在LoginServlet 判断用户名密码的时候 加入

```java
request.setAttribute("msg","用户名或密码不正确");
```

然后在登录界面中：

```jsp
用户名称：<input type="text" name=username><span style="color: red"><%= request.getAttribute("msg") == null ? "": request.getAttribute("msg")%></span> 
```

##### 2. EL（Expression Language）

- 格式：==${表达式}==
- 作用：主要用来输出域对象中的属性值

1. EL是JSP内置的表达式语言，用以访问页面的上下文以及不同作用域中的对象 ，==输出对象属性的值==，或执行简单的运算或判断操作。EL在得到某个数据时，会自动进行数据类型的转换。
2. **EL** 表达式用于代替JSP表达式 `<%= %>` 在页面中做输出操作。
3. EL表达式仅仅用来读取数据，而不能对数据进行修改。
4. 使用EL表达式输出数据时，**如果有则输出数据，如果为null则什么也不输出。**
5. EL 表达式的语法

> EL表达式查询的规则：
>
> > 1. 先从page域中开始查找，找到后直接返回，不再向其他域中查找，如果找不到再去request域中查找，以此类推...
> >
> > 2. 如果在application域中仍找不到则返回空串
> >
> > 3. ==EL 提供了四个Scope对象==，用来精确获取指定域中的属性值。优先级由高到低:
> >
> >    > - pageScope
> >    >
> >    >   > 获取page域中的属性值
> >    >
> >    > - requestScope
> >    >
> >    >   > 获取request域中的属性值
> >    >
> >    > - sessionScope
> >    >
> >    >   > 获取session域中的属性值
> >    >
> >    > - applicationScope	
> >    >
> >    >   > 获取application域中的属性值
>
> > ```jsp
> > <%
> > //创建Employee对象
> > Employee employee = new Employee(1,"吴秀波",new Department(1001,"出轨门"));
> > //将employe对象放到page域中
> > pageContext.setAttribute("star", employee);
> > %>
> > 
> > 通过EL表达式输出Employee对象的lastName：${pageScope.star.lastName }<br>
> > 通过EL表达式输出Employee对象的dept属性的name属性值：${pageScope.star.dept.name }<br>
> > 
> > 通过EL表达式输出Employee类中getOutName方法的返回值：${pageScope.star.outName }<br>
> > 
> > star.后面调用的是employee对象里的get的方法，名字是将get方法去掉get，首字母变成小写
> > ```

##### 3. JavaScript

1. 在1995年时，由[Netscape](http://baike.baidu.com/view/153922.htm)公司的[Brendan 	Eich](http://baike.baidu.com/view/2135520.htm)，在[网景导航者](http://baike.baidu.com/view/1350596.htm)浏览器上首次设计实现而成。[Netscape](http://baike.baidu.com/view/153922.htm)在最初将其脚本语言命名为[LiveScript](http://baike.baidu.com/view/2373233.htm)，因为[Netscape](http://baike.baidu.com/view/153922.htm)与[Sun](http://baike.baidu.com/subview/24856/10322735.htm)合作，网景公司管理层希望它外观看起来像[Java](http://baike.baidu.com/subview/29/12654100.htm)，因此取名为JavaScript。

2. 特性

   > - 脚本语言。JavaScript是一种解释型的脚本语言,C、C++、Java等语言先编译后执行,	而JavaScript是在程序的运行过程中逐行进行解释。
   > - 基于对象。JavaScript是一种基于对象的脚本语言,它不仅可以创建对象,也能使用现有的对象。
   > - 简单。JavaScript语言中采用的是弱类型的变量类型,对使用的数据类型未做出严格的要求,是基于Java基本语句和控制的脚本语言。
   > - 动态性。JavaScript是一种采用事件驱动的脚本语言,它不需要经过Web服务器就可以对用户的输入做出响应。
   > - 跨平台性。JavaScript脚本语言不依赖于操作系统,仅需要浏览器的支持。因此一个JavaScript脚本在编写后可以带到任意机器上使用,前提是机器上的浏览器支	持JavaScript脚本语言,目前JavaScript已被大多数的浏览器所支持

3. 编写位置

   1.  编写到HTML中<script>标签中

      ```html
      <head>
        <script type="text/javascript">
          
        </script>
      </head>
      ```

   2.  写在外部的 .js 文件中。然后通过script标签引入

   ```html
   <script type="text/javascript" src="script.js"></script>
   ```

4. JavaScript的事件驱动

   - 用户事件：用户操作，例如单击、鼠标移入、鼠标移出等

   - 系统事件：由系统触发的事件，例如文档加载完成

   - 常用的事件

     > onload：当整个文档都加载完成之后再执行函数中的内容
     >
     >  onclick：给按钮对象绑定单击事件
     >
     >  onblur
     >
     >  onfocus
     >
     >  onmouseover
     >
     >  onmouseout

5. ==BOM==

   - Borwser Object Model 浏览器对象模型
   - 浏览器对象模型提供了独立于内容的、可以与浏览器窗口进行互动的对象结构。BOM由多个对象组成，其中代表浏览器窗口的Window对象是BOM的顶层对象，其他对象都是该对象的子对象
   - 常用的对象(window的子对象)

    document  history    location    screen   navigator    frames

6. ==DOM==

   - Document Object Model 文档对象模型

   - document对象: window对象的一个属性，代表当前HTML文档，包含了整个文档的树形结构。获	取document对象的本质方法是：window.document，而“window.”可以省略

   - DOM树

     ![image-20200324215533469](pic/DOM树.png)

   - 元素查询

     

     | 功能               | API                                     | 返回值             |
     | ------------------ | --------------------------------------- | ------------------ |
     | 根据id值查询       | document.getElementById(“id值”)         | 一个具体的元素节点 |
     | 根据标签名查询     | document.getElementsByTagName(“标签名”) | 元素节点数组       |
     | 根据name属性值查询 | document.getElementsByName(“name值”)    | 元素节点数组       |



#### 3.3 注册

##### 1 jQuery

1. jQuery是为了==简化==JavaScript开发而生的一个小型的框架，jQuery和 \$ 是相等的，我们==通常使用 \$ 代替 jQuery 这个单词==

   ```javascript
   //当整个文档都加载完成之后再执行函数中的内容
   
   //在JavaScript中
   window.onload = function(){
     //1.获取按钮对象
     var btnEle = document.getElementById("btnId");
     //2.给按钮对象绑定单击事件
     btnEle.onclick = function(){
     //3.弹出提示框
     alert("Hello JavaScript!");
     };
   };
   
   //在jQuery中
   $(function(){
   		//获取按钮对象并给它绑定单击事件
   		$("#btnId").click(function(){
   			//弹出提示框
   			alert("Hello jQuery!");
   		});
   	});
   ```

   

   - 基本选择器

     > - ID选择器 ：`$("#id属性值")`
     > - 类选择器：`$(".class属性值")`
     > - 标签选择器：$("html标签")

   - 常用的方法

     > 1. attr()
     >
     >    - 获取或设置标签的属性值
     >    - 对象.attr("属性名")：获取属性值
     >    - 对象.attr("属性名","属性值")：设置属性值
     >
     > 2. text()和html()方法
     >
     >    - 获取或设置成对出现的标签中的文本值
     >
     >    - 对象.text()：获取文本值
     >
     >    - 对象.text("新值")：设置文本值
     >
     >    - html()方法与text()方法的唯一区别是html方法可以解析html标签
     >
     >      详见：Java_Web/day03/Web_Ex/项目下的 login.js
     >
     > 3. val()
     >
     >    - 获取或设置input标签的value属性值
     >
     >    - 对象.val()：获取value属性值
     >
     >    - 对象.val("新值")：设置value属性值
     >
     >      详见：Java_Web/day03/Web_Ex/项目下的 login.js
     >
     > 4. 事件
     >
     >    - click()：单击事件
     >    - change()：内容改变的事件
     >
     > 5. 正则表达式
     >
     >    ```javascript
     >    $(function(){
     >      //给提交按钮绑定单击事件
     >      $("#sub").click(function(){
     >    	//获取用户输入的用户名
     >    	var username = $("#username").val();
     >    	//设置一个验证用户名是否符合规则的正则表达式
     >    	//var userReg = /a/;//  /a/表示只要用户名内有a就可以提交表单
     >      // ^设置开头的格式限制，_-表示允许_和-开头{}内的内容限制用户名长度
     >    	var userReg = /^[a-zA-Z0-9_-]{3,6}$/;
     >    	//验证用户名是否符合规则
     >    	var flag = userReg.test(username);
     >    	if(!flag){
     >    		alert("请输入3-6位的字母、数字、下划线或减号的用户名！");
     >    		return false;
     >    	}
     >      });
     >    });
     >    ```

   

#####  2. Ajax

- AJAX 是 Asynchronous JavaScript And XML 的简称。直译为，异步的 JS 和XML。
- AJAX的实际意义是，不发生页面跳转、异步载入内容并改写页面内容的技术。
- AJAX也可以简单的理解为通过 JS 向服务器发送请求。

1. 同步处理

​	AJAX出现之前，我们访问互联网时一般都是同步请求，也就是当我们通过一个页面向	服务器发送一个请求时，在服务器响应结束之前，我们的整个页面是不能操作的，也就	是直观上来看他是卡主不动的。

​	这就带来了非常糟糕的用户体验。首先，同步请求时，用户只能等待服务器的响应，而	不能做任何操作。其次，如果请求时间过长可能会给用户一个卡死的感觉。最后，同步	请求的最大缺点就是即使整个页面中只有一小部分内容发生改变我们也要刷新整个页	面。

2. 异步处理

 而异步处理指的是我们在浏览网页的同时，通过AJAX向服务器发送请求，发送请求的过程中我们浏览网页的行为并不会收到任何影响，甚至主观上感知不到在向服务器发送请求。当服务器正常响应请求后，响应信息会直接发送到AJAX中，AJAX可以根据服务器响应的内容做一些操作。

 使用AJAX的异步请求基本上完美的解决了同步请求带来的问题。首先，发送请求时不会影响到用户的正常访问。其次，即使请求时间过长，用户不会有任何感知。最后，AJAX可以根据服务器的响应信息局部的修改页面，而不需要整个页面刷新。

**通过 $.ajax 发送 Ajax请求**

```javascript
$("#btnId").click(function(){
	//通过$.ajax()方法发送Ajax请求
	/*
		url：必须的。用来设置请求地址
		type：可选的。用来设置发送请求的请求方式，默认是get
		data：可选的。用来设置请求参数
		success：可选的。用来设置回调函数，响应成功之后系统会自动调用该函数，
				响应数据会以参数的形式传入到该函数中
		dataType：可选的。用来设置响应数据的类型，默认是text，还可以设置xml、json等		
	*/
	$.ajax({
		url:"${pageContext.request.contextPath }/AjaxServlet",
		type:"get",
		data:"username=admin&password=123456",
		success:function(res){
			//将响应信息设置到span标签中
			$("#res").text(res);
		},
		dataType:"text"
	});
});
```

**通过 \$.get() 或 \$.post() 发送Ajax请求**

get 和 post 指请求的 method，post请求用\$.post

```javascript
$("#btnId2").click(function(){
	//通过$.get/post()方法发送Ajax请求
	/*
		$.get(url, [data], [callback], [type])
			url：必须的。用来设置请求地址
			data：可选的。用来设置请求参数
			callback：可选的。用来设置一个回调函数，响应成功之后系统会自动调用该函数，
					响应数据会以参数的形式传入到该函数中
			type：可选的。用来设置响应数据的类型		
	*/
	//设置请求地址
	var url = "${pageContext.request.contextPath }/AjaxServlet";
	//设置请求参数
	var params = "username=admin&password=666666";
// 			$.get(url,params,function(res){
// 				//将响应数据设置到span标签中
// 				$("#res2").text(res);
// 			},"text");
	//通过$.post()发送一个post请求
	$.post(url);
});
```

##### 3. JSTL

- JSP 的标准标签库，使用它需要导入以下jar包

  > jstl.jar
  >
  > standard.jar

- 使用c标签需要导入核心标签库

  ```javascript
  <%@ taglib uri=*"http://java.sun.com/jsp/jstl/core"* prefix=*"c"* %> 
  ```

- if 标签

  ```javascript
   	 <%
  	 	int age = 86;
  	 	pageContext.setAttribute("age", age);
  	 %>
  	 <c:if test="${age < 18 }">
  	 	禁止未成年人入内！
  	 </c:if>
  	  <c:if test="${age > 18 }">
  	 	请尽情浏览，注意身体！！！
  	 </c:if>
  	 <%
  ```

- forEach 标签

 ```javascript
<%
  List<String> list = new ArrayList();
 	 	list.add("吉沢明步");
 	 	list.add("蓝泽润");
 	 	list.add("京香JULIA");
 	 	list.add("潘金莲");
 	 	list.add("文章");
 	 	list.add("白百何");
 	 	list.add("李小璐");
 	 	list.add("林丹");
 	 	list.add("吴秀波");
  //将list放到page域中
  pageContext.setAttribute("stars", list);
%>
<hr>
<!-- forEach标签：相当于Java中的for循环
    items属性：接收一个要遍历的集合
    var属性：设置一个遍历接收遍历到的值，同时会以变量值为key将遍历到的值放到page域中
 -->
<c:forEach items="${stars }" var="star">
  <a href="#">${pageScope.star }</a><br>
</c:forEach>
<!--
 ```



- empty运算符

- > 用来判断一个字符串或一个集合是否为空
  >
  > ```javascript
  > empty运算符：主要用来判断一个字符串或一个集合是否为空
  >  -->
  > <c:if test="${empty pageScope.stars }">
  >   世界很美好，没有人乱搞！！！
  > </c:if>
  > ```

#### 3.4 登录功能实现-登录成功跳转主页面

- Session会话 
- Cookie  
- [JSTL](#3. JSTL)

##### 1. Cookie

**Cookie的运行原理**

​      1.第一次向服务器发送请求时在服务器端创建一个Cookie对象

​      2.将Cookie对象发送给浏览器

​      3.以后浏览器再发请求就会携带着该Coolie对象

​      4.服务器通过不同的Cookie来区别不同的用户

1. HTTP是==无状态协议==，服务器不能记录浏览器的访问状态，也就是说==服务器不能区分中两次请求是否由一个客户端发出==。这样的设计严重阻碍的Web程序的设计。如：在我们进行网购时，买了一条裤子，又买了一个手机。由于http协议是无状态的，如果不通过其他手段，服务器是不能知道用户到底买了什么。而Cookie就是解决方案之一。

2. Cookie实际上就是服务器==保存在浏览器上==的一段信息。浏览器有了Cookie之后，每次向服务器发送请求时都会同时将该信息发送给服务器，服务器收到请求后，就可以根据该信息处理请求。

   

 **Cookie的用途**

1. 网上商城购物车
2. 用户登录状态的保持

**Cookie的限制性**

1. Cookie作为请求或响应报文发送，无形中增加了网络流量

2. Cookie是明文传送的安全性差

3. 各个浏览器对Cookie有限制，使用上有局限

   

##### 2. session

**Session的运行原理：**

1. 第一次向服务器发送请求时==在服务器端创建一个Session对象==，该对象有一个全球唯一的ID
2. 在创建Session对象的同时会创建一个特殊的Cookie对象，该Cookie对象的名字是一个固定值：==JSESSIONID==， 该Cookie对象的==值==就是Session对象的==ID==值，并且将该Cookie对象发送给浏览器
3. 以后浏览器再发送请求就会携带着这个特殊的Cookie对象
4. 服务器获取Cookie对象的值之后寻找与之对应的Session对象，以此来区分不同的用户 



##### 3.5 完成注销功能及钝化和活化

==注销==：使session对象失效

==钝化==：服务器关闭时，session及session里的用户从内存持久化到硬盘，叫钝化

==活化==：服务器再启动时，会从硬盘反序列化到内存，叫活化

##### 3.6 主页面访问权限控制

**过滤器**

    1) 对于WEB应用来说，过滤器是一个驻留在服务器中的WEB组件，他可以截取客户端和WEB资源之间的请求和响应信息。WEB资源可能包括Servlet、JSP、HTML页面等
    2) 当服务器收到特定的请求后，会先将请求交给过滤器，程序员可以在过滤器中对请求信息进行读取修改等操作，然后将请求信息再发送给目标资源。目标资源作出响应后，服务器会再次将响应转交给过滤器，在过滤器中同样可以对响应信息做一些操作，然后再将响应发送给服务器。
    3) 也就是说过滤器可以在WEB资源收到请求之前，浏览器收到响应之前，对请求和响应信息做一些相应的操作。
    4) 在一个WEB应用中可以部署多个过滤器，多个过滤器就组成了一个过滤器链，请求和响应必须在经过多个过滤器后才能到达目标

**过滤器的使用**
    1) 通过实现Filter接口完成过滤器的开发

```java
//filterSevelet设置，urlPatterns的值表示拦截地址，也可以用 servletNames
//拦截路径发出请求时，filter将决定是否拦截
@WebFilter(filterName = "HelloFilter",urlPatterns = "/index.jsp")
//放行请求,不写此句则表示拦截
chain.doFilter(req, resp);
```

- 作用：用来==拦截用户的请求==，但是Filter只拦截请求==不拦截响应==

- 我们还可以为同一个资源设置多个过滤器，多个过滤器的拦截顺序由web.xml中的filter-mapping　标签对，在前的先拦截，在后的后拦截。如果不设置，则按filter创建的先后顺序，后创建的优先。

  ![filter](pic/filter.png)

- 以拦截index.jsp页面为例创建两个拦截器

- - HelloFilter
  - HelloFIlter2

##### 3.5 在线人数统计

**监听器**

- Lisener 监听器用来监听ServletRequest、HttpSession、ServletContext对象的生命周期和三个域中的属性变化

- 分类

  > 1. 1. 生命周期 
  >    2. 数据绑定			

- 掌握==ServletContext==的生命周期监听器

- > ServletContextListener
  >
  > > - 通过该接口创建的监听器服务器已启动该对象就被创建
  > >
  > > - 服务器关闭该对象就销毁

- - 

## Maven

#### XML

1. XML--可扩展标记语言eXtensible Markup Language
2. 由W3C组织发布，目前推荐遵守的是W3C组织于2000年发布的XML1.0规范
3. XML的使命，就是以一个统一的格式，组织有关系的数据，为不同平台下的应用程序服务
4. XML用来==传输和存储数据==，HTML用来显示数据
5. XML没有预定义标签，均为==自定义标签==

##### xml 用途

1. 配置文件

   > -  JavaWeb 中的 web.xml
   > - C3P0中的c3p0-config.xml

2. 数据交换格式

   > - ==Ajax==
   > -  WebService

3. 数据存储

    保存关系型数据

   

##### xml 语法

1. XML文档组成

   > - XML声明
   >
   >   > 1. version属性指定XML版本，固定值是1.0
   >   > 2. encoding指定的字符集，是告诉解析器使用什么字符集进行解码，而编码是由文本		编辑器决定的
   >
   > - CDATA区
   >
   >   > 1. 当XML文档中需要写一些程序代码、SQL语句或其他不希望XML解析器进行解析的内容时，就可以写在CDATA区中
   >   >
   >   > 2. XML解析器会将CDATA区中的内容原封不动的输出
   >   >
   >   >    > CDATA区的定义格式：`<![CDATA[…]]>`

2. 语法规则

   - XML声明要么不写，要写就写在第一行，并且前面没有任何其他字符
   - 只能有一个根标签
   - 标签必须正确结束
   - 标签不能交叉嵌    
   - 严格区分大小写
   - 属性必须有值，且必须加引号
   - 标签不能以数字开头
   - 注释不能嵌套

3. xml解析

   >- XML解析是指通过解析器读取XML文档，解释语法，并将文档转化成对象
   >- 常用的解析方式
   >
   >> DOM（Document Object Model）
   >>
   >>  SAX（Simple API for XML）
   >
   >- DOM 和SAX解析的对比
   >
   >  ![Dom_SAX](pic/Dom_SAX.png)
   >
   >- Dom4j解析示例
   >
   >  ```java
   >  				//创建解析对象
   >          SAXReader saxReader = new SAXReader();
   >  
   >          //解析xml文档
   >          Document document = saxReader.read("students.xml");
   >  
   >          //获取根标签student
   >          Element rootElement = document.getRootElement();
   >  
   >          //获取所有的student标签
   >          List<Element> stus = rootElement.elements("student");
   >  ```

   

#### JSON

1. AJAX一开始使用的时XML的数据格式，XML的数据格式非常简单清晰，容易编写，但是由于XML中包含了过多的标签，以及十分复杂的结构，解析起来也相对复杂，所以目前来讲，AJAX中已经几乎不使用XML来发送数据了。取而代之的是一项新的技术JSON。
2. JSON是 **JavaScript Object Notation** 的缩写，是JS提供的一种数据交换格式。
3. JSON对象本质上就是一个JS对象，但是这个对象比较特殊，它可以直接转换为字符串，在不同语言中进行传递，通过工具又可以转换为其他语言中的对象。
4. 如下一个JSON对象：

```json
1 {“name”:”sunwukong” , ”age”:18 , ”address”:”beijing” }
2 这个对象中有三个属性name、age和address
3 如果将该对象使用单引号引起了，那么他就变成了一个字符串
4 ‘{“name”:”sunwukong” , ”age”:18 , ”address”:”beijing” }’
5 变成字符串后有一个好处，就是可以在不同语言之间传递。
6 比如，将JSON作为一个字符串发送给Servlet，在Java中就可以把JSON字符串转换为一个Java对象。
```

##### JSON 的数据类型

1. 字符串

   用“”表示，不能使用单引号。

2. 数字 ： 123.4

3. 布尔值：true、false

4. null

5. 对象：{“name”:”sunwukong”, ”age”:18}

6. 数组：[1,”str”,true]

##### JS中操作JSON

1. 创建JSON对象

   ```json
   //对象用{}括起来，属性名必须使用""括起来；属性名和属性值之间使用冒号分隔；多个属性之间使用逗号分隔
   var jsonObj = {"name":"孙悟空","age":520};
   ```

2. 创建JSON数组

   ```json
   var jsonArray = ["猪八戒",1000,false,null,jsonObj];
   ```

3. JSON对象转换为JSON字符串

   ```json
   var objToStr = JSON.stringify(jsonObj);
   ```

4. 声明一个JSON字符串

   ```json
   var jsonStr = '{"name":"白骨精","age":18}';
   ```

5. 将JSON字符串转换为JSON对象

      ```json
   var strToObj = JSON.parse(jsonStr);
   ```



##### 在Java中操作JSON

1. 在Java中可以从文件中读取JSON字符串，也可以是客户端发送的JSON字符串，所以第一个问题，我们先来看如何将一个JSON字符串转换成一个Java对象。

2. 首先解析JSON字符串我们需要导入第三方的工具，目前主流的解析JSON的工具大概有三种json-lib、jackson、gson。三种解析工具相比较json-lib的使用复杂，且效率较差。而Jackson和gson解析效率较高。使用简单，这里我们以gson为例讲解。

3. Gson是Google公司出品的解析JSON工具，使用简单，解析性能好。

4. Gson中解析JSON的核心是Gson的类，解析操作都是通过该类实例进行。

5. JSON字符串转换为对象

   ```json
   String json = "{\"name\":\"张三\",\"age\":18}";
   Gson gson = new Gson();
   //转换为集合
   Map<String,Object> stuMap = gson.fromJson(json, Map.class);
   //如果编写了相应的类也可以转换为指定对象
   Student fromJson = gson.fromJson(json, Student.class);
   ```

6. 对象转换为JSON字符串

   ```json
   Student stu = new Student("李四", 23);
   Gson gson = new Gson();
   //{"name":"李四","age":23}
   String json = gson.toJson(stu);
   		
   Map<String , Object> map = new HashMap<String, Object>();
   map.put("name", "孙悟空");
   map.put("age", 30);
   //{"age":30,"name":"孙悟空"}
   String json2 = gson.toJson(map);
   List<Student> list = new ArrayList<Student>();
   list.add(new Student("八戒", 18));
   list.add(new Student("沙僧", 28));
   list.add(new Student("唐僧", 38));
   //[{"name":"八戒","age":18},{"name":"沙僧","age":28},
   {"name":"唐僧","age":38}]
   String json3 = gson.toJson(list);		
        // 如果将一个数组格式的json字符串转换成java对象需要用到
        //Gson提供的一个匿名内部类： TypeToken
   	TypeToken tk= new TypeToken<List<User>>(){};
   	List<User> list2 = gson.fromJson(json,tk.getType());
   	System.out.println(list2.get(0));
   ```

   


#### 第一个Maven工程

1. 创建约定的目录结构

Hello

> - src
>
> > - main
> >
> > > - java
> > >
> > > - resources
> >
> > - test
> >
> > > - java
> > >
> > > - resources
>
> - pom.xml

```
main目录用于存放主程序。
test目录用于存放测试程序。
java目录用于存放源代码文件。
resources目录用于存放配置文件和资源文件。
```

2. 创建Maven的核心配置文件pom.xml

   ```pom
   <?xml version="1.0" ?>
   <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
   	<modelVersion>4.0.0</modelVersion>
   
   	<groupId>com.atguigu.maven</groupId>
   	<artifactId>Hello</artifactId>
   	<version>0.0.1-SNAPSHOT</version>
   
   	<name>Hello</name>
   	  
   	<dependencies>
   		<dependency>
   			<groupId>junit</groupId>
   			<artifactId>junit</artifactId>
   			<version>4.0</version>
   			<scope>test</scope>
   		</dependency>
   	</dependencies>
   </project>
   
   ```

3. 编写主代码

   在src/main/java/com/atguigu/maven目录下新建文件Hello.java

   ```java
   package com.atguigu.maven;
   
   public class Hello {
       public String sayHello(String name) {
           return "Hello"+name + "!";
       }
   }
   ```

4. 编写测试代码

   ```java
   package com.atguigu.maven;
   import org.junit.Test;
   import static junit.framework.Assert.*;
   
   public class HelloTest {
       public void testHello(String name) {
           Hello hello = new Hello();
           String results = hello.sayHello("caixiyu");
           assertEquals("Hello caixiyu",results);
       }
   }
   ```

5. 运行几个基本的Maven命令

   ```shell
   #打开终端，进入Hello项目根目录(pom.xml文件所在目录)：
   $ mvn compile  #查看根目录变化
   $ mvn clean    #再次查看根目录变化
   $ mvn  compile  #查看根目录变化
   $mvn  test-compile  #查看target目录的变化
   $ mvn  test  #查看target目录变化
   $ mvn  package  #查看target目录变化
   $ mvn  install  #查看本地仓库的目录变化
   ```

   **Maven 核心概念**

   1. 1. POM

         Project Object Model：项目对象模型。将Java工程的相关信息封装为对象作为便于操作和管理的模型。Maven工程的核心配置。可以说学习Maven就是学习pom.xml文件中的配置。

      2. 约定的目录结构

         现在JavaEE开发领域普遍认同一个观点：约定>配置>编码。意思就是能用配置解决的问题就不编码，能基于约定的就不进行配置。而Maven正是因为指定了特定文件保存的目录才能够对我们的Java工程进行自动化构建。目录结构含义参见前面的描述。

      3. 坐标

         - Maven的坐标

           > 使用如下三个向量在Maven的仓库中唯一的确定一个Maven工程。
           >
           > - ==g==roupId：公司或组织的域名倒序+当前项目名称
           >
           > - ==a==rtifactId：当前项目的模块名称
           >
           > - ==v==ersion：当前模块的版本
           >
           >   ```pom
           >   <groupId>com.atguigu.maven</groupId>
           >   <artifactId>Hello</artifactId>
           >   <version>0.0.1-SNAPSHOT</version>
           >   ```

         - 如何通过坐标到仓库中查找jar包？

         > 1. 将 gav三个向量连起来
         >
         >    ```
         >    com.atguigu.maven+Hello+0.0.1-SNAPSHOT
         >    ```
         >
         > 2. 以连起来的字符串作为目录结构到仓库中查找
         >
         >    ```
         >    com/atguigu/maven/Hello/0.0.1-SNAPSHOT/Hello-0.0.1-SNAPSHOT.jar
         >    ```

         ※注意：我们自己的Maven工程必须 `mvn install`才会进入仓库。

         

      4. **依赖**

         1. 

         - 当A jar包需要用到B jar包中的类时，我们就说A对B有依赖。配置的基本形式是使用dependency标签指定目标jar包的坐标。例如：

           ```pom
           <dependencies>
           		<dependency>
           			<groupId>junit</groupId>
           			<artifactId>junit</artifactId>
           			<scope>test</scope>
           </dependency>
           ```

         - 直接依赖和间接依赖

         如果A依赖B，B依赖C，那么A→B和B→C都是直接依赖，而A→C是间接依赖。

         1. 

         **依赖的范围**

         - compile

           > - main目录下的Java代码**可以**访问这个范围的依赖
           >
           > - test目录下的Java代码**可以**访问这个范围的依赖
           >
           > - 部署到Tomcat服务器上运行时**要**放在WEB-INF的lib目录下
           >
           >   例如：对Hello的依赖。主程序、测试程序和服务器运行时都需要用到

         

         - test

           > - main目录下的Java代码**不能**访问这个范围的依赖
           > - test目录下的Java代码**可以**访问这个范围的依赖
           > - 部署到Tomcat服务器上运行时**不会**放在WEB-INF的lib目录下
           >
           > 例如：对junit的依赖。仅仅是测试程序部分需要。

         - provided

           > - main目录下的Java代码**可以**访问这个范围的依赖
           > - test目录下的Java代码**可以**访问这个范围的依赖
           > - 部署到Tomcat服务器上运行时**不会**放在WEB-INF的lib目录下
           >
           > 例如：servlet-api在服务器上运行时，Servlet容器会提供相关API，所以部署的时候不需要。

         - 其它

           > runtime、import、system等。各个依赖范围的作用可以概括为下图：
           >
           > ![image-20200327190913887](pic/image-20200327190913887.png)

         

         **依赖的传递性**

         当存在间接依赖的情况时，主工程对间接依赖的jar可以访问吗？这要看间接依赖的jar包引入时的依赖范围——只有依赖范围为compile时可以访问。

         

         **依赖的原则：解决jar包冲突**

         1. 路径最短者优先

            ![image-20200327191105439](pic/image-20200327191105439.png)

         2. 路径相同时先声明者优先

         ​			![image-20200327191201357](pic/image-20200327191201357.png)

         这里“声明”的先后顺序指的是dependency标签配置的先后顺序。

         

         **依赖的排除**

         1. 有的时候为了确保程序正确可以将有可能重复的间接依赖排除。请看如下的例子：

         假设当前工程为public，直接依赖environment。environment依赖commons-logging的1.1.1对于public来说是间接依赖。当前工程public直接依赖commons-logging的1.1.2 

         加入exclusions配置后可以在依赖environment的时候排除版本为1.1.1的commons-logging的间 接依赖

         1. ```pom
            <dependency>
            	<groupId>com.atguigu.maven</groupId>
            	<artifactId>Environment</artifactId>
            	<version>0.0.1-SNAPSHOT</version>
            	<!-- 依赖排除 -->
            	<exclusions>
            		<exclusion>
            			<groupId>commons-logging</groupId>
            			<artifactId>commons-logging</artifactId>
            		</exclusion>
            	</exclusions>
            </dependency>
            <dependency>
            	<groupId>commons-logging</groupId>
            	<artifactId>commons-logging</artifactId>
            	<version>1.1.2</version>
            </dependency>
            ```

         2. 

         **统一管理目标jar包的版本**

         以对Spring的jar包依赖为例：Spring的每一个版本中都包含spring-core、spring-context等jar包。我们应该导入版本一致的Spring jar包，而不是使用4.0.0的spring-core的同时使用4.1.1的spring-context。

         问题是如果我们想要将这些jar包的版本统一升级为4.1.1，是不是要手动一个个修改呢？显然，我们有统一配置的方式

         

         

      5. 仓库

         - 分类

         > 本地仓库：为当前本机电脑上的所有Maven工程服务。
         >
         > 远程仓库
         >
         > ![maven仓库](pic/maven仓库.png)
         >
         > > 1.  私服：架设在当前局域网环境下，为当前局域网范围内的所有Maven工程服务。
         > > 2. 中央仓库：架设在Internet上，为全世界所有Maven工程服务。
         > > 3. 中央仓库的镜像：架设在各个大洲，为中央仓库分担流量。减轻中央仓库的压力，同时更快的响应用户请求。

         - 仓库中的文件

           1. Maven的插件
           2. 我们自己开发的项目的模块
           3. 第三方框架或工具的jar包

           ​	※不管是什么样的jar包，在仓库中都是按照坐标生成目录结构，所以可以通过统一的方式查询或依赖。

           

      6. 生命周期

         ​	Maven生命周期定义了各个构建环节的执行顺序，有了这个清单，Maven就可以自动化的执行构	建命令了。

         

         Maven有三套相互独立的生命周期，分别是：

         > - Clean Lifecycle在进行真正的构建之前进行一些清理工作。
         > - Default Lifecycle构建的核心部分，编译，测试，打包，安装，部署等等。
         > - Site Lifecycle生成项目报告，站点，发布站点。

         再次强调一下它们是**相互独立的**，你可以仅仅调用clean来清理工作目录，仅仅调用site来生成站点。当然你也可以直接运行 **mvn clean install site** 运行所有这三套生命周期。

         

         每套生命周期都由一组阶段(Phase)组成，我们平时在命令行输入的命令总会对应于一个特定的阶段。比如，运行mvn clean，这个clean是Clean生命周期的一个阶段。有Clean生命周期，也有clean阶段。

         1. 

         **clean生命周期**

         Clean生命周期一共包含了三个阶段：

         > - pre-clean 执行一些需要在clean之前完成的工作
         >
         > - clean 移除所有上一次构建生成的文件
         > - post-clean 执行一些需要在clean之后立刻完成的工作

         

         **Site生命周期**

         > - pre-site 执行一些需要在生成站点文档之前完成的工作
         > - site 生成项目的站点文档
         > - post-site 执行一些需要在生成站点文档之后完成的工作，并且为部署做准备
         > - site-deploy 将生成的站点文档部署到特定的服务器上

         1. 这里经常用到的是site阶段和site-deploy阶段，用以生成和发布Maven站点，这可是Maven相当强大的功能，Manager比较喜欢，文档及统计数据自动生成，很好看。

         

         **Default生命周期**

         Default生命周期是Maven生命周期中最重要的一个，绝大部分工作都发生在这个生命周期中。这里，只解释一些比较重要和常用的阶段：

         > - validate
         > - generate-sources
         > - process-sources
         > - generate-resources
         > - process-resources 复制并处理资源文件，至目标目录，准备打包。
         > - **compile** 编译项目的源代码。
         > - process-classes
         > - generate-test-sources
         > - process-test-sources
         > - generate-test-resources
         > - process-test-resources 复制并处理资源文件，至目标测试目录。
         > - **test-compile** 编译测试源代码。
         > - process-test-classes
         > - **test** 使用合适的单元测试框架运行测试。这些测试代码不会被打包或部署。
         > - prepare-package
         > - **package** 接受编译好的代码，打包成可发布的格式，如JAR。
         > - pre-integration-test
         > - integration-test
         > - post-integration-test
         > - verify
         > - **install**将包安装至本地仓库，以让其它项目依赖。
         > - deploy将最终的包复制到远程的仓库，以让其它开发人员与项目共享或部署到服务器上运行。

         

         **生命周期与自动化构建**

         **运行任何一个阶段的时候，它前面的所有阶段都会被运行**，例如我们运行mvn install 的时候，代码会被编译，测试，打包。这就是Maven为什么能够自动执行构建过程的各个环节的原因。此外，Maven的插件机制是完全依赖Maven的生命周期的，因此理解生命周期至关重要。

      7. 插件和目标

         - Maven的核心仅仅定义了抽象的生命周期，具体的任务都是交由插件完成的。
         - 每个插件都能实现多个功能，每个功能就是一个插件目标。
         - Maven的生命周期与插件目标相互绑定，以完成某个具体的构建任务。

         例如：compile就是插件maven-compiler-plugin的一个功能；pre-clean是插件maven-clean-plugin的一个目标。

         

      8. 继承

         由于非compile范围的依赖信息是不能在“依赖链”中传递的，所以有需要的工程只能单独配置。此时如果项目需要将各个模块的junit版本统一为4.9，那么到各个工程中手动修改无疑是非常不可取的。使用继承机制就可以将这样的依赖信息统一提取到父工程模块中进行统一管理。

         **创建父工程**

         创建父工程和创建一般的Java工程操作一致，唯一需要注意的是：打包方式处要设置为pom。

         在子工程中引用父工程

         在父工程中管理依赖

      9. 聚合

         将多个工程拆分为模块后，需要手动逐个安装到仓库后依赖才能够生效。修改源码后也需要逐个手动进行clean操作。而使用了聚合之后就可以批量进行Maven工程的安装、清理工作。

         在总的聚合工程中使用modules/module标签组合，指定模块工程的相对路径即可

         ```
         <modules>
         	<module>../Hello</module>
         	<module>../HelloFriend</module>
         	<module>../MakeFriends</module>
         </modules>
         ```

         

6. 

#### 第二个Maven工程

关键：对Hello的依赖

这里Hello就是我们的第一个Maven工程，现在HelloFriend对它有依赖。那么这个依赖能否成功呢？更进一步的问题是：HelloFriend工程会到哪里去找Hello呢？

答案是：本地仓库。任何一个Maven工程会根据坐标到本地仓库中去查找它所依赖的jar包。如果能够找到则可以正常工作，否则就不行。



##  Spring

#### 概述

1. Spring是一个开源框架 	

2. Spring为==简化==企业级开发而生，使用Spring，JavaBean就可以实现很多以前要靠EJB(Enterprise Java Beans)才能实现的功能。同样的功能，在EJB中要通过繁琐的配置和复杂的代码才能够实现，而在Spring中却非常的优雅和简洁。 	

3. Spring是一个**IOC**(DI)和**AOP**容器框架。

4. Spring的优良特性

   > **依赖注入**：DI——Dependency Injection，反转控制(IOC)最经典的实现。
   >
   >  **面向切面编程**：Aspect Oriented Programming——AOP
   >
   >  **一站式**：在IOC和AOP的基础上可以整合各种企业应用的开源框架和优秀的第三方    类库（实际上Spring 自身也提供了表述层的SpringMVC和持久层的Spring JDBC）。

5. Spring模块

![image-20200327231815063](pic/image-20200327231815063.png)

#### 搭建Spring环境

1. 创建Maven版的Java工程

   ![img](pic/1068501-20180914191722384-1695467171.png)

   ![img](pic/1068501-20180914191929721-1110836003.png)

   

   <img src="pic/20180104102227025" alt="img" style="zoom:120%;" />

   <img src="pic/20180104102149285" alt="img" style="zoom:120%;" />

   <img src="pic/20180104102307530" alt="img" style="zoom:120%;" />

   

   

2. 加入Spring相关jar包的依赖Tips: Spring自身JAR包：

   > spring-beans-4.0.0.RELEASE.jar
   >
   > spring-context-4.0.0.RELEASE.jar
   >
   > spring-core-4.0.0.RELEASE.jar
   >
   > spring-expression-4.0.0.RELEASE.jar
   >
   >  commons-logging-1.1.1.jar

   

   在加入依赖时，**实际**只需要加入对 spring-context的依赖即可,Maven会根据依赖信息，将其他的jar包的依赖一并加入.

```pom
 <dependencies>
        <!-- beans  -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-beans</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

        <!-- context -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

        <!-- core -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

        <!-- expression -->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-expression</artifactId>
            <version>4.0.0.RELEASE</version>
        </dependency>

 </dependencies>
```

下载依赖包的过程可能比较慢，可从本地导入：

```
mvn install:install-file -Dfile=spring-context-4.0.0.RELEASE.jar  -DgroupId=org.springframework -DartifactId=spring-context  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-beans-4.0.0.RELEASE.jar  -DgroupId=org.springframework -DartifactId=spring-beans  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-core-4.0.0.RELEASE.jar -DgroupId=org.springframework -DartifactId=spring-core  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-expression-4.0.0.RELEASE.jar -DgroupId=org.springframework -DartifactId=spring-expression  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile= commons-logging-1.1.1.jar -DgroupId=org.springframework -DartifactId= commons-logging  -Dversion=4.0.0 -Dpackaging=jar

mvn install:install-file -Dfile=spring-context-support-4.0.0.RELEASE.jar -DgroupId=org.springframework -DartifactId= spring-context-support  -Dversion=4.0.0 -Dpackaging=jar
spring-context-support-4.0.0.RELEASE.jar
```

3. 在Spring Tool Suite工具中通过如下步骤创建Spring的配置文件

1. > - src/main/resources 下：New XML file->Spring Bean Configuration File
   >
   > - 为文件取名字 例如：applicationContext.xml

​	

#### HelloWorld

1. 目标：使用Spring创建对象，为属性赋值

2. 创建HelloWorld类

   ```java
   
   ```

   

3. d

4. 

报错解决：

> - 版本号5已过时：将Settings中的Java compiler中的 Target codebite version 在Project structure中改为 和当前工程下当前Project下的Java version ， current language level 以及 Module 中的 language level同步
> - 一直不能更新dependency，看看是不是没有更改maven的仓库的位置

## Linux

### 1. Linux文件与目录结构

#### Linux文件

Linux系统中一切皆文件。

#### Linux目录结构

![img](pic/003vPl7Rty6E8kZRlAEdc690.jpg)

==**/bin**==：
 bin是Binary的缩写, 这个目录存放着最经常使用的命令。

**/sbin**：
 s就是Super User的意思，这里存放的是系统管理员使用的系统管理程序。

**==/home==**：
用户的主目录，在Linux中，每个用户都有一个自己的目录，一般该目录名是以用户的账号命名的。

==**/root**==：
该目录为系统管理员，也称作超级权限者的用户主目录。

**==/boot==：**
这里存放的是启动Linux时使用的一些核心文件，包括一些连接文件以及镜像文件。

**/dev ：**
dev是Device(设备)的缩写, 该目录下存放的是Linux的外部设备，在Linux中访问设备的方式和访问文件的方式是相同的。

**==/etc==：**
这个目录用来存放所有的系统管理所需要的配置文件和子目录。

==**/lib**==：
这个目录里存放着系统最基本的动态连接共享库，其作用类似于Windows里的DLL文件。几乎所有的应用程序都需要用到这些共享库。

**/lost+found**：
这个目录一般情况下是空的，当系统非法关机后，这里就存放了一些文件。

**==/media==**：
 linux系统会自动识别一些设备，例如U盘、光驱等等，当识别后，linux会把识别的设备挂载到这个目录下。

**==/mnt==**：
系统提供该目录是为了让用户临时挂载别的文件系统的，我们可以将光驱挂载在/mnt/上，然后进入该目录就可以查看光驱里的内容了。

**==/opt==**：
 这是给主机额外安装软件所摆放的目录。比如你安装一个ORACLE数据库则就可以放到这个目录下。默认是空的。

**/proc**：
这个目录是一个虚拟的目录，它是系统内存的映射，我们可以通过直接访问这个目录来获取系统信息。
这个目录的内容不在硬盘上而是在内存里，我们也可以直接修改里面的某些文件，比如可以通过下面的命令来屏蔽主机的ping命令，使别人无法ping你的机器：



**/selinux**：
 这个目录是Redhat/CentOS所特有的目录，Selinux是一个安全机制，类似于windows的防火墙，但是这套机制比较复杂，这个目录就是存放selinux相关的文件的。

**/srv**：
 该目录存放一些服务启动之后需要提取的数据。

**/sys**：

 这是linux2.6内核的一个很大的变化。该目录下安装了2.6内核中新出现的一个文件系统 sysfs 。

sysfs文件系统集成了下面3种文件系统的信息：针对进程信息的proc文件系统、针对设备的devfs文件系统以及针对伪终端的devpts文件系统。

该文件系统是内核设备树的一个直观反映。

当一个内核对象被创建的时候，对应的文件和目录也在内核对象子系统中被创建。

**/tmp**：
这个目录是用来存放一些临时文件的。

==**/usr**==：
 这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下，类似于windows下的program files目录。

**/usr/bin：**
系统用户使用的应用程序。

**/usr/sbin：**
超级用户使用的比较高级的管理程序和系统守护程序。

**/usr/src：**
内核源代码默认的放置目录。

**==/var==**：
这个目录中存放着在不断扩充着的东西，我们习惯将那些经常被修改的目录放在这个目录下。包括各种日志文件。

**/run**：
是一个临时文件系统，存储系统启动以来的信息。当系统重启时，这个目录下的文件应该被删掉或清除。如果你的系统上有 /var/run 目录，应该让它指向 run。

### 2. VI/VIM编辑器

- VI是Unix操作系统和类Unix操作系统中最通用的文本编辑器。

- VIM编辑器是从VI发展出来的一个性能更强大的文本编辑器。可以主动的以==字体颜色==辨别语法的正确性，方便程序设计。VIM与VI编辑器完全兼容。

  ![img](pic/vi-vim-cheat-sheet-sch.gif)

#### 三种模式

##### 1. 一般模式

以vi打开一个档案就直接进入一般模式了（这是**默认的模式**）。在这个模式中， 你可以使用『上下左右』按键来移动光标，你可以使用『删除字符』或『删除整行』来处理档案内容， 也可以使用『复制、贴上』来处理你的文件数据。

| yy        | ==复制==游标所在的那一行(常用)                               |
| :-------- | ------------------------------------------------------------ |
| p, P      | p 为将已复制的数据==粘贴==在光标下一行，P 则为粘贴在游标上一行 |
| u         | ==撤销==上一步                                               |
| y数字y    | 复制多行。在行首输入: y想要复制的行数y,在想要粘贴处按p       |
| dd        | ==删除==光标所在的一整行                                     |
| x         | 向后删除一个字符 (相当于 [del] 按键)                         |
| X         | 向前删除一个字符(相当于 [backspace] 亦即是退格键) 	(常用) |
| yw        | 复制一个词                                                   |
| dw        | 删除一个词                                                   |
| shift+^   | 移动到行头                                                   |
| shift+$   | **移动到行尾**                                               |
| gg或者1+G | **移动到页头**                                               |
| G         | **移动到页尾**                                               |
| 数字+G    | **移动到目标行**                                             |
|           |                                                              |

##### 2. 编辑模式

在一般模式中可以进行删除、复制、粘贴等的动作，但是无法编辑文件内容！要等到你按下『i, I, o, O, a, A, r, R』等任何一个字母之后才会进入编辑模式。

注意了！通常在Linux中，按下这些按键时，在画面的左下方会出现『INSERT或 REPLACE』的字样，此时才可以进行编辑。而如果要回到一般模式时， 则必须要按下『Esc』这个按键即可退出编辑模式。

| 进入输入或取代的编辑模式 |                                                              |
| ------------------------ | ------------------------------------------------------------ |
| i, I                     | 进入输入模式(Insert mode)：  	i 为『从目前光标所在处输入』， I 为『在目前所在行的第一个非空格符处开始输入』。 	(常用) |
| a, A                     | 进入输入模式(Insert mode)：  	a 为『从目前光标所在的下一个字符处开始输入』， A 	为『从光标所在行的最后一个字符处开始输入』。(常用) |
| o, O                     | 进入输入模式(Insert mode)：  	这是英文字母 o 的大小写。o 为『在目前光标所在的下一行处输入新的一行』； 	O 为在目前光标所在处的上一行输入新的一行！(常用) |
| r, R                     | 进入取代模式(Replace mode)：  	r 只会取代光标所在的那一个字符一次；R会一直取代光标所在的文字，直到按下 	ESC 为止；(常用) |
| [Esc]                    | 退出编辑模式，回到一般模式中(常用)                           |

##### 3.指令模式

**在一般模式当中**，输入『 **: / ?**』3个中的任何一个按钮，就可以将光标移动到最底下那一行。

在这个模式当中， 可以提供你『搜寻资料』的动作，而读取、存盘、大量取代字符、离开 vi 、显示行号等动作是在此模式中达成的！

**基本语法**

| :w             | 写入/==保存==                                  |
| -------------- | ---------------------------------------------- |
| :!             | ==强制执行==                                   |
| :q             | ==离开== vi                                    |
| :wq            | 储存后离开，若为 :wq! 则为强制储存后离开       |
| **:wq!**       | 强制保存退出                                   |
| / 要查找的词   | n 查找下一个，N 往上查找                       |
| ? 要查找的词   | n是查找上一个，N是往下查找                     |
| :set nu        | 显示行号                                       |
| :set nonu      | 关闭行号                                       |
| ZZ（shift+zz） | 没有修改文件直接退出，如果修改了文件保存后退出 |

##### 模式间转换

![vim-vi-workmodel](pic/vim-vi-workmodel.png)



### 查看网络IP和网关



##### 设置

1. 停止Network-manager的服务

   ```shell
   $ sudo service network-manager stop
   ```

2. 设置IP地址

   ```shell
   #备份原有配置文件
   $ cp /etc/network/interfaces  /etc/network/interfacesbak   
   
   $ sudo vim /etc/network/interfaces
   
   #输入下面的设置
   auto eth0  #开机自动连接网络
   iface eth0 inet static   #static表示使用固定ip，dhcp表述使用动态ip
   address 192.168.1.10   #设置ip地址
   netmask 255.255.255.0  #设置子网掩码
   gateway 192.168.1.2    #设置网关
   ```

3. 设置DNS服务器

   ```shell
   #备份原有dns配置文件
   $ cp  /etc/resolv.conf   /etc/resolv.confbak    
   
   #编辑配置文件
   $ sudo vim /etc/resolv.conf
   
   #添加以下内容
   nameserver 114.114.114.114   #设置首选dns
   nameserver 8.8.8.8   #设置备用dns
   ```

4. 启动Network-manager的服务

```
sudo service network-manager start
```

5. ping

   ![ifconfig](pic/ifconfig.png)

   ping一下 wlp1s0 inet处的ip地址，看是否能通

### 修改主机名称

修改linux的主机映射文件（hosts文件）

（1）进入Linux系统查看本机的主机名。通过hostname命令查看

（2）如果感觉此主机名不合适，我们可以进行修改。通过编辑/etc/sysconfig/network文件

###关闭防火墙

- 基本语法

  > service 服务名 start		：开启服务
  >
  > service  服务名 stop		：关闭服务
  >
  > service  服务名 restart	：功能描述：重新启动服务
  >
  > service  服务名 status	 ：功能描述：查看服务状态

- chkconfig 设置后台服务的自启配置

  > chkconfig   		 ：查看所有服务器自启配置
  >
  > chkconfig 服务名 off   ：关掉指定服务的自动启动
  >
  > chkconfig 服务名 on   ：开启指定服务的自动启动
  >
  > chkconfig 服务名 --list	：查看服务开机启动状态

- 

![image-20200328195114196](pic/image-20200328195114196.png)

### Linux 常用命令

#### 1. man

man ：获得帮助信息

```shell
man [命令或配置文件]		（功能描述：获得帮助信息）
```

| 信息        | 功能                   |
| ----------- | ---------------------- |
| NAME        | 命令的名称和单行描述   |
| SYNOPSIS    | 怎样使用命令           |
| DESCRIPTION | 命令功能的深入讨论     |
| EXAMPLES    | 怎样使用命令的例子     |
| SEE ALSO    | 相关主题（通常是手册页 |

#### 2. help 获得shell内置命令的帮助信息

help 命令	（功能描述：获得shell内置命令的帮助信息）

#### 3. 常用快捷键

| ctrl + C | 停止进程                |
| -------- | ----------------------- |
| ctrl + L | 清屏；彻底清屏是：reset |
| ctrl+ Q  | 退出                    |

#### 4. 文件目录类命令

- pwd ：显示当前工作目录的绝对路径

- ls ：列出目录的内容

  > - -a ：全部的文件，连同隐藏档( 开头为 . 的文件) 一起列出来(常用)
  > - -l ：长数据串列出，包含文件的属性与权限等等数据；(常用)

- cd 切换目录

  > - cd ~或 cd：回到自己的家目录
  > - ==cd -==  ： 回到上一次所在目录
  > - cd ..  ：回到当前目录的上一级目录
  > - cd -P ：跳转到实际物理路径，而非快捷方式路径

- mkdir：创建一个新的目录

  > 参数-p ：创建多级目录

- rmdir：删除一个空的目录

- touch： 创建空文件

  > 可直接 `vim 文件名`  , 这样可以直接打开

- cp： 复制文件或目录

  > ```
  > cp [选项] source dest 				: 复制source文件到dest
  > ```
  >
  > 参数 -r ：递归复制整个文件夹

- rm： 移除文件或目录

  > ```
  > rm [选项] deleteFile			（功能描述：递归删除目录中所有内容）
  > ```
  >
  > > -r : ==递归删除目录==中所有内容
  > > -f : 强制执行删除操作，而不提示用于进行确认。
  > > -v :显示指令的详细执行过程

- mv : 移动文件与目录或重命名

- cat： 查看文件内容

  > -n ：显示所有行的行号，包括空行。

- more： 文件内容分屏查看器

  > more指令是一个基于VI编辑器的文本过滤器，它以全屏幕的方式按页显示文本文件的内容。more指令中内置了若干快捷键，详见操作说明。
  >
  > ```
  > more 要查看的文件
  > ```
  >
  > 操作说明：
  >
  > - 空白键 (space) ：代表向下翻一页；
  > - Enter：代表向下翻『一行』；
  > - q：代表立刻离开 more ，不再显示该文件内容。
  > - Ctrl+F：滚动一屏
  > - Ctrl+B：返回上一屏
  > - = ：输出当前行的行号
  > - :f ：输出文件名和当前行的行号

- less ：分屏显示文件内容

  less指令用来分屏查看文件内容，它的功能与more指令类似，但是比more指令更加强大，支持各种显示终端。less指令在显示文件内容时，并不是一次将整个文件加载之后才显示，而是根据显示需要加载内容，对于显示**大型文件具有较高的效率**。

  > ```
  > less 要查看的文件
  > ```
  >
  > - 空格键：翻动一页；
  > - [pagedown]：向下翻动一页
  > - [pageup]：向上翻动一页；
  > - /字串：向下搜寻『字串』的功能；n：向下查找；N：向上查找；
  > - ?字串 ：向上搜寻『字串』的功能；n：向上查找；N：向下查找；
  > - q：离开 less 

- echo：输出内容到控制台

  ```
  echo [选项] [输出内容]
  ```

  > -e： 支持反斜线控制的字符转换
  >
  > 转义字符：
  >
  > > - `\\`   : 输出\本身
  > > - \n：换行符
  > > - \t： 制表符，也就是Tab键

- head ：显示文件头部内容

  head用于显示文件的开头部分内容，默认情况下head指令显示文件的前10行内容。

  > ```
  > head 文件
  > ```
  >
  > > -n <行数> ：指定显示头部内容的行数
  > >
  > > ```
  > > head -n 5 文件      （功能描述：查看文件头5行内容，5可以是任意行数）
  > > ```

- tail :输出文件尾部内容
  tail用于输出文件中尾部的内容，默认情况下tail指令显示文件的后10行内容。

  > -n<行数> ：输出文件尾部n行内容
  > -f ：显示文件最新追加的内容，监视文件变化

- ==`>` ：覆盖 和 >> ：追加==

  > （1）ll >文件       ：列表的内容写入文件a.txt中（**覆盖写**）
  >
  > （2）ll >>文件	 ：列表的内容**追加**到文件aa.txt的末尾
  >
  > （3）cat 文件1 > 文件2	（功能描述：将文件1的内容覆盖到文件2）
  >
  > （4）echo “内容” >> 文件

- ln ：软链接
  软链接也成为符号链接，类似于windows里的==桌面快捷方式==，有自己的数据块，主要存放了链接其他文件的路径。

  > ```
  > ln -s [原文件或目录] [软链接名]	
  > ```
  >
  > 经验技巧
  >
  > > 删除软链接： rm -rf 软链接名，而不是rm -rf 软链接名/
  > >
  > > 查询：通过ll就可以查看，列表属性第1位是l，尾部会有位置指向。

- history： 查看已经执行过历史命令

#### 5. 时间日期类

- date [OPTION]... [+FORMAT]

> - -d<时间字符串> ：显示指定的“时间字符串”表示的时间，而非当前时间
>
> - -s<日期时间> ：设置系统日期时间
>
> - <+日期时间格式> ：指定显示时使用的日期时间格式
>
>   > - date								（功能描述：显示当前时间）
>   > - date +%Y					  （功能描述：显示当前年份）
>   > - date +%m					（功能描述：显示当前月份）
>   > - date +%d					 （功能描述：显示当前是哪一天）
>   > - date "+%Y-%m-%d %H:%M:%S"		（功能描述：显示年月日时分秒）

- cal： ==查看日历==

  ```
  cal ： 显示本月日历
  cal [年份]			：显示某年日历
  ```

#### 6. 用户管理命令

- useradd： 添加新用户

  ```
  useradd [选项]用户名
  ```

  > useradd -g 组名 用户名	（功能描述：添加新用户到某个组）

- passwd ：设置用户密码

  ```
  passwd 用户名
  ```

- id： 查看用户是否存在

  ```
  id 用户名
  ```

- cat  /etc/passwd： 查看创建了哪些用户

- su ：切换用户

  > su 用户名称 ：切换用户，只能获得用户的执行权限，不能获得环境变量
  >
  > su - 用户名称 ：切换到用户并获得该用户的环境变量及执行权限

- userdel： 删除用户

  > userdel 用户名：删除用户但保存用户主目录
  >
  > userdel -r 用户名：用户和用户主目录，都删除

- who ：查看登录用户信息

  > whoami：显示自身用户名称
  >
  > who am i：显示**登录用户**的用户名

- sudo ：设置普通用户具有root权限

- usermod ：修改用户

  > ```
  > usermod -g 用户组 用户名
  > ```
  >
  > -g : 修改用户的初始登录组，给定的组必须存在

  

#### 7. 用户组管理命令

- groupadd: 新增组

  ```
  groupadd 组名
  ```

- groupdel ：删除组

  ```
  groupdel 组名
  ```

- groupmod 修改组

  ```
  groupmod -n 新组名 老组名
  ```

- cat  /etc/group ：查看创建了哪些组

  

#### 8. 文件权限类

Linux系统是一种典型的多用户系统，不同的用户处于不同的地位，拥有不同的权限。为了保护系统的安全性，Linux系统对不同的用户访问同一文件（包括目录文件）的权限做了不同的规定。在Linux中我们可以使用ll或者ls -l命令来显示一个文件的属性以及文件所属的用户和组。

每个文件的属性由左边第一部分的10个字符来确定：

![363003_1227493859FdXT](pic/363003_1227493859FdXT.png)

##### 1. 位：

> - 0首位表示类型
>
>   > 在Linux中第一个字符代表这个文件是目录、文件或链接文件等等
>   >
>   > - \- ：文件
>   > - d： 代表目录
>   > -  l： 链接文档(link file)；
>
> - 第1-3位确定属主（该文件的所有者）拥有该文件的权限。---User
>
> - 第4-6位确定属组（所有者的同组用户）拥有该文件的权限，---Group
>
> - 第7-9位确定其他用户拥有该文件的权限 ---Other



##### 2. rxw作用文件和目录的不同解释

- 作用到文件：

  > - [ r ]代表可读(read): 可以读取，查看
  > - [ w ]代表可写(write): 可以修改，但是**不代表可以删除该文件，删除一个文件的前提条件是对该文件所在的目录有写权限，才能删除该文件.**
  > - [ x ]代表可执行(execute):可以被系统执行

- 作用到目录：

  > - [ r ]代表可读(read): 可以读取，ls查看目录内容
  > - [ w ]代表可写(write): 可以修改，目录内创建+删除+重命名目录
  > - [ x ]代表可执行(execute):可以进入该目录

![image-20200328215637080](pic/image-20200328215637080.png)

如果查看到是文件：链接数指的是硬链接个数。创建硬链接方法：

```
ln [原文件] [目标文件]	
```

如果查看的是文件夹：链接数指的是子文件夹个数。

#####  3. chmod 改变权限

![image-20200328220059923](pic/image-20200328220059923.png)

第一种方式变更权限

```
chmod [{ugoa}{+-=}{rwx}] 文件或目录
```

> u:所有者 g:所有组 o:其他人 a:所有人(u、g、o的总和

第二种方式变更权限

```
chmod  [mode=421 ]  [文件或目录]
```

> r=0x100   w=0x010  x=0x001      rwx=4+2+1=7

##### 5. chown 改变所有者

```
chown [选项] [最终用户] [文件或目录]  ： 改变文件或者目录的所有者
```

> -R ：递归操作

##### chgrp 改变所属组

```
chgrp [最终用户组] [文件或目录]
```



#### 9. 文件查找类

- find ：查找文件或者目录

  find指令将从指定目录向下递归地遍历其各个子目录，将满足条件的文件显示在终端。

  ```
  find [搜索范围/路径] [选项]
  ```

  > - -name<查询方式> ：按照指定的文件名查找模式查找文件
  >
  >   ```shell
  >    find xiyou/ -name “*.txt”
  >   ```
  >
  > - -user<用户名> ：查找属于指定用户名所有文件
  >
  >   ```shell
  >   find xiyou/ -user cxy
  >   ```
  >
  > - -size<文件大小> ：按照指定的文件大小查找文件。
  >
  >   ```sh
  >   find /home -size +204800
  >   ```

- grep 过滤查找及“|”管道符

  管道符，“|”，表示==将前一个命令的处理结果输出传递给后面的命令处理==

  ```
  grep [选项 ] [查找内容] [源文件]
  ```

  > -n : 显示匹配行及行号。
  >
  > ```
  > ll  |  grep -n test
  > ```
  >
  > ==-r : 递归操作==

- which ：查找命令
  查找命令在==哪个目录下==

  ```
  which [命令]
  ```

#### 10. 压缩和解压类

- gzip/gunzip 压缩

  ```
  gzip [文件]	 ：压缩文件，只能将文件压缩为*.gz文件
  gunzip [文件.gz]	 ：解压缩文件命令
  ```

  > 经验技巧
  >
  > - **只能压缩文件**不能压缩目录
  >
  > - **不保留原来的文件**

- zip/unzip 压缩

  > ```
  > zip  [选项] [XXX.zip]  [将要压缩的内容] ：压缩文件和目录的命令）
  > ```
  >
  > > -r : 压缩目录
  >
  > ```
  > unzip [选项] [XXX.zip] ：解压缩文件）
  > ```
  >
  > > -d<目录> : 指定解压后文件的存放目录

  zip 压缩命令在window/linux都通用，可以压缩目录且保留源文件。

  

- ==tar 打包==

  > ```
  > tar  [选项] [XXX.tar.gz]  [将要打包进去的内容]：打包目录，压缩后的文件格式.tar.gz
  > ```
  >
  > - -z ：打包同时压缩
  >
  > - ==-c==：产生.tar打包文件
  >
  > - -v ：显示详细信息
  >
  > - -f：指定压缩后的文件名
  >
  > - ==-x==：解包.tar文件
  >
  >   ```shell
  >   #可将多个文件或目录打包，放在后面用空格隔开即可
  >   tar -zcvf xiyou.tar.gz xiyou/ xiyou/
  >   
  >   #解压到当前目录
  >   tar -zxvf houma.tar.gz
  >   #解压到其它路径，需加 -C
  >   tar -zxvf xiyou.tar.gz -C /opt
  >   ```

  

#### 11. 磁盘分区类

- df : 查看磁盘空间使用情况 

  ```
  df  [选项]
  ```

  > -h : 以人们较易阅读的 GBytes, MBytes, KBytes 等格式自行显示；

-  fdisk :查看分区 

  > -l : 显示所有硬盘的分区列表

- mount/umount :挂载/卸载

  对于Linux用户来讲，不论有几个分区，分别分给哪一个目录使用，它总归就是一个根目录、一个独立且唯一的文件结构。

  Linux中每个分区都是用来组成整个文件系统的一部分，它在用一种叫做“挂载”的处理方法，它整个文件系统中包含了一整套的文件和目录，并将一个分区和一个目录联系起来，要载入的那个分区将使它的存储空间在这个目录下获得。

  > ```
  > mount [-t vfstype] [-o options] [device dir ]：挂载设备
  > umount [设备文件名或挂载点] ：卸载设备
  > ```
  >
  > > - -t vfstype: 指定文件系统的类型，通常不必指定。mount 会自动选择正确的类型。常用类型有：
  > >
  > >   > - 光盘或光盘镜像：iso9660
  > >   > - DOS fat16文件系统：msdos
  > >   > - Windows 9x fat32文件系统：vfat
  > >   > - Windows NT ntfs文件系统：ntfs
  > >   > - Mount Windows文件网络共享：smbfs
  > >   > - UNIX(LINUX) 文件网络共享：nfs
  > >
  > > - -o options : 主要用来描述设备或档案的挂接方式。常用的参数有：
  > >
  > >   > - loop：用来把一个文件当成硬盘分区挂接上系统
  > >   > - ro：采用只读方式挂接设备
  > >   > - rw：采用读写方式挂接设备
  > >   > - iocharset：指定访问文件系统所用字符集
  > >
  > > - device : 要挂接(mount)的设备
  > >
  > > - dir :设备在系统上的挂接点(mount point)

  

#### 12. 进程线程类

进程是正在执行的一个程序或命令，每一个进程都是一个运行的实体，都有自己的地址空间，并占用一定的系统资源。

- ps :查看当前系统进程状态

  > ```
  > ps aux  | grep xxx	：查看系统中所有进程
  > ```
  >
  > > -a : 选择所有进程
  > > -u : 显示所有用户的所有进程
  > > -x :显示没有终端的进程
  >
  > ps aux显示信息说明:
  >
  > > - USER：该进程是由哪个用户产生的
  > > - PID：进程的ID号
  > > - %CPU：该进程占用CPU资源的百分比，占用越高，进程越耗费资源；
  > > - %MEM：该进程占用物理内存的百分比，占用越高，进程越耗费资源；
  > > - VSZ：该进程占用虚拟内存的大小，单位KB；
  > > - RSS：该进程占用实际物理内存的大小，单位KB；
  > > - TTY：该进程是在哪个终端中运行的。其中tty1-tty7代表本地控制台终端，tty1-tty6是本地的字符界面终端，tty7是图形终端。pts/0-255代表虚拟终端。
  > > - STAT：进程状态。常见的状态有：R：运行、S：睡眠、T：停止状态、s：包含子进程、+：位于后台
  > > - START：该进程的启动时间
  > > - TIME：该进程占用CPU的运算时间，注意不是系统时间
  > > - COMMAND：产生此进程的命令名
  >
  > ```
  > ps -ef | grep xxx ：可以查看子父进程之间的关系
  > ```
  >
  > ps -ef显示信息说明: 
  >
  > > UID：用户ID
  > >
  > > PID：进程ID
  > >
  > > PPID：父进程ID
  > >
  > > C：CPU用于计算执行优先级的因子。数值越大，表明进程是CPU密集型运算，执行优先级会降低；数值越小，表明进程是I/O密集型运算，执行优先级会提高
  > >
  > > STIME：进程启动的时间
  > >
  > > TTY：完整的终端名称
  > >
  > > TIME：CPU时间
  > >
  > > CMD：启动进程所用的命令和参数


- kill :终止进程

```
kill  [选项] 进程号 ：通过进程号杀死进程
killall 进程名称 ：通过进程名称杀死进程，也支持通配符，这在系统因负载过大而变得很慢时很有用
```

> -9 ：表示强迫进程立即停止

- pstree 查看进程树

```
pstree [选项]
```

> -p：显示进程的PID 
> -u：显示进程的所属用户

- top 查看系统健康状态

```
top [选项]	
```

> -d 秒数 ：指定top命令每隔几秒更新。默认是3秒在top命令的交互模式当中可以执行的命令
>
> -i：使top不显示任何闲置或者僵死进程。
> -p：通过指定监控进程ID来仅仅监控某个进程的状态。

操作说明

> | 操作 | 功能                          |
> | ---- | ----------------------------- |
> | P    | 以CPU使用率排序，默认就是此项 |
> | M    | 以内存的使用率排序            |
> | N    | 以PID排序                     |
> | q    | 退出top                       |



查询结果字段解释

第一行信息为任务队列信息

第二行为进程信息

第三行为CPU信息

- netstat: 显示网络统计信息和端口占用情况

```
	netstat -anp |grep 进程号	（功能描述：查看该进程网络信息）
	netstat -nlp	| grep 端口号	（功能描述：查看网络端口号占用情况）
```

> -n: 拒绝显示别名，能显示数字的全部转化成数字
> -l：仅列出有在listen（监听）的服务状态
> -p：表示显示哪个进程在调用

#### 13. crond：服务管理

重新启动crond服务

```
service crond restart
```

##### crontab 定时任务设置

```
crontab [选项]
```

> -e: 编辑crontab定时任务
> -l：查询crontab任务
> -r：删除当前用户所有的crontab任务

参数说明:

> 1. `crontab -e` 进入crontab编辑界面。会打开vim编辑你的工作。
>
>    \* * * * * 执行的任务
>
>    > | 项目    | 含义                     | 范围                    |
>    > | ------- | ------------------------ | ----------------------- |
>    > | 第一个* | 一小时当中的第几==分==钟 | 0-59                    |
>    > | 第二个* | 一天当中的第几小==时==   | 0-23                    |
>    > | 第三个* | 一个月当中的第几==天==   | 1-31                    |
>    > | 第四个* | 一年当中的第几==月==     | 1-12                    |
>    > | 第五个* | 一周当中的==星期==几     | 0-7（0和7都代表星期日） |
>
> 2. 特殊符号
>
>    | *    | 代表任何时间。比如第一个“*”就代表一小时中每分钟都执行一次的意思 |
>    | ---- | ------------------------------------------------------------ |
>    | ，   | 代表不连续的时间。比如“0 8,12,16 * * * 命令”，就代表在每天的8点0分，12点0分，16点0分都执行一次命令 |
>    | -    | 代表连续的时间范围。比如“0 5  *  *  1-6命令”，代表在周一到周六的凌晨5点0分执行命令 |
>    | */n  | 代表每隔多久执行一次。比如“*/10  *  *  *  *  命令”，代表每隔10分钟就执行一遍命令 |
>
> 3. 特定时间执行命令
>
>    | 命令         | 含义                                       |
>    | ------------ | ------------------------------------------ |
>    | 45 22 * * *  | 在22点45分执行命令                         |
>    | 0 17 * * 1   | 每周1 的17点0分执行命令                    |
>    | 0 5 1,15 * * | 每月1号和15号的凌晨5点0分执行命令          |
>    | 40 4 * * 1-5 | 每周一到周五的凌晨4点40分执行命令          |
>    | */10 4 * * * | 每天的凌晨4点，每隔10分钟执行一次命令      |
>    | 0 0 1,15 * 1 | 每月1号和15号，每周1的0点0分都会执行命令。 |
>
>    ------
>
>    注意：星期几和几号最好不要同时出现，因为他们定义的都是天。非常容易让管理员混乱。
>
>    ```shell
>    # 每隔1分钟，向/root/bailongma.txt文件中添加一个11的数字
>    */1 * * * * /bin/echo ”11” >> /root/bailongma.txt
>    ```

#### 14. 软件包管理

##### RPM

RPM（RedHat Package Manager），RedHat软件包管理工具，类似windows里面的setup.exe

 是Linux这系列操作系统里面的打包安装工具，它虽然是RedHat的标志，但理念是通用的。

RPM包的名称格式：

```
Apache-1.3.23-11.i386.rpm

apache ： 软件名称
1.3.23-11：软件的版本号，主版本和此版本
i386：是软件所运行的硬件平台，Intel 32位微处理器的统称
rpm：文件扩展名，代表RPM包
```

- RPM查询命令（rpm -qa）

  ```
  rpm -qa	：查询所安装的所有rpm软件包
  rpm -qa | grep [rpm软件包]：查询和筛选所安装的rpm软件包
  ```

- RPM卸载命令（rpm -e）

  ```
  rpm -e [选项]
  ```

  > -e：卸载软件包
  > --nodeps：卸载软件时，不检查依赖。这样的话，那些使用该软件包的软件在此之后可能就不能正常工作了。

- RPM安装命令（rpm -ivh）

  ```
  rpm [选项] [RPM包全名]
  ```

  > -i：-i=install，安装
  > -v：-v=verbose，显示详细信息
  > -h：-h=hash，进度条
  > --nodeps：--nodeps，不检测依赖进度

- 

##### YUM仓库配置

YUM（全称为 ==Yellow dog Updater, Modified==）是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包，无须繁琐地一次次下载、安装

![image-20200329232335223](pic/image-20200329232335223.png)

**常用命令**

```
yum [选项] [参数]
```

> 选项说明：
>
> > -y：对所有提问都回答“yes”
>
> 参数说明：
>
> > install：安装rpm软件包
> > update：更新rpm软件包
> > check-update：检查是否有可用的更新rpm软件包
> >
> > remove：删除指定的rpm软件包
> > list：显示软件包信息
> > clean：清理yum过期的缓存
> > deplist：显示yum软件包的所有依赖关系







## Git & GitHub

![image-20200330184830055](pic/image-20200330184830055.png)

### 1. Git

#### 1. 工作区,本地库(Repository)和暂存区

![image-20200330195118832](pic/image-20200330195118832.png)

##### 1. 创建版本库

在项目文件夹内，执行:  

```
git  init
```

##### 2. 提交文件

新建文件后，通过

```shell
git  status  #进行查看文件状态
git  add [ 文件名] #将文件添加到暂存区
git  commit #提交文件到本地库
编写注释 ，完成提交
git  commit  –m “注释内容”# 直接带注释提交
```

##### 3. 查看文件提交记录

```shell
git  log  [文件名]     #进行查看历史记录
git log  --pretty=oneline [文件名]      #简易信息查看
```

##### 4.回退历史

```shell
git  reset  --hard HEAD^   #回退到上一次提交
git  reset  --hard HEAD~n  #回退n次操作
```

##### 5. 版本穿越

```shell
git  reflog  [文件名]   #查看历史记录的版本号
git  reset  --hard  版本号  #回退n次操作
```

#####6. 还原文件

```shell
git  checkout -- [文件名]   #还原文件
```

##### 7. 删除某个文件

先删除文件
再git add 再提交

#### 2. 分支

![image-20200330200334935](pic/image-20200330200334935.png)

##### 创建分支

```shell
git  branch  <分支名> # 创建分支
git branch –v   #查看分支
```

#####切换分支

```shell
git checkout  <分支名>
git checkout  –b  <分支名> #创建并切换分支
```

#####合并分支
```shell
git  checkout  master #先切换到主干   
git  merge  <分支名>
```

**冲突：**

![image-20200330210854523](pic/image-20200330210854523.png)

![image-20200330210920372](pic/image-20200330210920372.png)

### 2. GitHub

![image-20200330211417710](pic/image-20200330211417710.png)

![image-20200330211451653](pic/image-20200330211451653.png)

##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
git  remote  add  origin  https://github.com/user111/Helloworld.git
```

> <==远端代号==> 是指远程链接的代号，一般直接用origin作代号，也可以自定义。
> <==远端地址==> 默认远程链接的url

##### 2. 增加远程地址推送到远程库

```shell
git  push   <远端代号>    <本地分支名称>
git  push  origin  master
```

>  <分支名称>  是指要提交的分支名字，比如master。

##### 3. 从GitHub上克隆一个项目

```shell
git  clone   <远端地址>   <新项目目录名>

#命令执行完后，会自动为这个远端地址建一个名为origin的代号
git  clone  https://github.com/user111/Helloworld.git   hello_world 
```

> <项目目录名>  是指为克隆的项目在本地新建的目录名称，可以不填，默认是GitHub的项目名

##### 4. 从GitHub更新项目

```shell
git  pull   <远端代号>   <远端分支名>
git pull origin  master
```

![image-20200330213849832](pic/image-20200330213849832.png)

![image-20200330213934657](pic/image-20200330213934657.png)

![image-20200330213945329](pic/image-20200330213945329.png)

![image-20200330214500571](pic/image-20200330214500571.png)

### 3. 在idea中使用Git

### 4. 分支

#### Git开发流程

简单来说就是，一个项目的成员们在工作中统一使用Git的工作方式

![image-20200330221926737](pic/image-20200330221926737.png)

![image-20200330221935950](pic/image-20200330221935950.png)

![image-20200330221947709](pic/image-20200330221947709.png)

#### 分支种类

- 主干分支 master
       主要负责管理正在运行的生产环境代码。永远保持与正在运行的生产环境完全一致。

- 开发分支   develop
       主要负责管理正在开发过程中的代码。一般情况下应该是最新的代码

- bug修理分支  ==hotfix==
       主要负责管理生产环境下出现的紧急修复的代码。 从主干分支分出，修理完毕并测试上线后，并回主干分支。并回后，视情况可以删除该分支

- 发布版本分支  release
       较大的版本上线前，会从开发分支中分出发布版本分支，进行最后阶段的集成测试。该版本上线后，会合并到主干分支。生产环境运行一段阶段较稳定后可以视情况删除

- 功能分支    feature
       为了不影响较短周期的开发工作，一般把中长期开发模块，会从开发分支中独立出来。 开发完成后会合并到开发分支。

  ![image-20200330222133828](pic/image-20200330222133828.png)

  

### GitLab —“自架私服版”的GitHub





##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
```

##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
```

##### 1. 增加远程地址

```shell
git remote add  <远端代号>   <远端地址> 
```

## Shell

**什么是SHELL？**

​	    [Shell](https://www.baidu.com/s?wd=Shell&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)俗称壳（用来区别于内核），是指“提供使用者使用界面”的软件，就是一个==命令行解释器==。

**SHELL的版本**
　　早在UNIX年代，发展者众多，所以由于shell依据发展者的不同就有许多版本，比如sh,C SHell,K SHell,还有TCSH等，每一种Shell都各有特点。当然也有我们的bash,bash这个shell是Bourne  Shell的增强版本，也是基于GNU的架构下发展出来的。

**sh和bash的区别**
　　bash是sh的增强版本。bash 是一个为[GNU](https://www.baidu.com/s?wd=GNU&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)项目编写的Unix [shell](https://www.baidu.com/s?wd=shell&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)，也就是[linux](https://www.baidu.com/s?wd=linux&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)用的[shell](https://www.baidu.com/s?wd=shell&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)。



```mermaid
graph TD
			subgraph 外部应用程序
			subgraph Shell
			subgraph Linux内核
			硬件
			end
			end
			end
```

查看shell版本：

```shell
cxy@Cxy:~$ cat /etc/shells
# /etc/shells: valid login shells
/bin/sh
/bin/bash
/bin/rbash
/bin/dash
```

### Shell 脚本

Shell 脚本（shell script），是一种为 shell 编写的脚本程序。业界所说的 shell 通常都是指 shell 脚本，但读者朋友要知道，shell 和 shell script 是两个不同的概念。简单的说**shell脚本可以放平时我们操作终端的命令**

### 1．Shell脚本入门

脚本以

```shell
# !/bin/bash
```

开头，意在指定解析器

#### 第一个Shell脚本：helloworld

1. 创建脚本

```sh
vim [文件名].sh
```

2. 写脚本

```shell
#!/bin/bash
echo "helloworld"
```

####  脚本的常用执行方式

1. 采用bash或sh+脚本的相对路径或绝对路径（不用赋予脚本+x权限）

```shell
$ sh helloworld.sh 
$ bash helloworld.sh 
```

2. 采用输入脚本的绝对路径或相对路径执行脚本（必须具有可执行权限+x）

   ```shell
   chmod 777 helloworld.sh
    ./helloworld.sh 
   ```

==注意==：第一种执行方法，本质是bash解析器帮你执行脚本，所以脚本本身不需要执行权限。第二种执行方法，本质是脚本需要自己执行，所以需要执行权限。

#### 第二个Shell脚本：多命令处理

```shell
$ touch batch.sh
$ vi batch.sh

#在batch.sh中输入如下内容

\#!/bin/bash

cd /home/atguigu
touch cls.txt
echo "I love cls" >>cls.txt
```

### 2. Shell中的变量

#### 1.系统变量

常用系统变量

`$HOME、$PWD、$SHELL、$USER等`

```shell
#查看系统变量的值
echo $HOME

#显示当前Shell中所有变量
set
```

#### 2 自定义变量

1．基本语法

（1）定义变量：变量=值

（2）撤销变量：==unset== 变量

（3）声明静态变量：readonly变量，注意：不能unset

2．变量定义规则

​	（1）变量名称可以由字母、数字和下划线组成，但是不能以数字开头，环境变量名建议大写。

​	（2==）等号两侧不能有空格==

​	（3）在bash中，==变量默认类型都是字符串类型==，无法直接进行数值运算。

​	（4）变量的值如果有空格，需要使用双引号或单引号括起来。

3．案例实操

```shell
A=5
echo $A

unset A
echo $A

D="I love banzhang"
```

#### 3.特殊变量

##### $n

1．基本语法

​	`$n`	:   n为数字

- `$0`代表该脚本名称
- `$1-$9`代表第1到第9个参数，10以上的参数，10以上的参数需要用大括号包含，如${10}

```shell
$ vim parameter.sh

#输入：
\#!/bin/bash

echo "$0  $1   $2"

$ bash parameter.sh cls  xz
```

##### $#

```
$# ：获取所有输入参数个数，常用于循环
```

```shell
$ vim parameter.sh

#输入：
\#!/bin/bash

echo "$#"

$ bash parameter.sh cls  xz cl
```

##### `$*、$@`

```
$* ：代表命令行中所有的参数，把所有的参数看成一个整体 
@* : 代表命令行中所有的参数，	把每个参数区分对待
```

```shell
$ vim parameter.sh

#输入：
\#!/bin/bash

\#!/bin/bash

echo "$0  $1   $2"
echo $#
echo $*
echo $@

cxy@Cxy:~$ bash t.sh 1 2 3
t.sh  1   2
3
1 2 3
1 2 3
```

##### $？

1．基本语法

$？ ：最后一次执行的命令的返回状态。

> 如果这个变量的值为0，证明上一个命令正确执行
>
> 如果这个变量的值为非0，则证明上一个命令执行不正确了

### 3. 运算符

- `$((运算式))`
- `$[运算式]`
- expr + , - , \*,  /,  %    加，减，乘，除，取余

注意：==expr运算符间要有空格==

```shell
S=$(((2+3)*4))
#20

S=$[(2+3)*4]
#20

$ expr 2 + 3
5

expr `expr 2 + 3` \* 4
20
```

###4. 条件判断

```
[ condition ]
```

注意：

- condition前后要有空格
- 条件非空即为true，[ atguigu ]返回true，[] 返回false。



常用判断条件

- 两个整数之间比较

  > | -lt 小于（less than）						-le 小于等于（less equal） |      |
  > | ------------------------------------------------------------ | ---- |
  > | -eq 等于（equal）							-gt 大于（greater than） |      |
  > | -ge 大于等于（greater equal）	-ne 不等于（Not equal）     |      |

- 按照文件==权限==进行判断

  > - -r 有读的权限（read）	
  > - -w 有写的权限（write）
  > - -x 有执行的权限（execute）

- 按照文件==类型==进行判断

  > - -f 文件存在并且是一个常规的文件（file）
  > - -e 文件存在（existence）		
  > - -d 文件存在并是一个目录（directory）

```shell
$ [ 23 -ge 22 ]
$ echo $?
0

$ [ -w helloworld.sh ]
$ echo $?
0

$ [ -e /home/atguigu/cls.txt ]
$ echo $?
```

- 多条件判断（&& 表示前一条命令执行成功时，才执行后一条命令，|| 表示上一条命令执行失败后，才执行下一条命令）

  ```shell
  $ [ condition ] && echo OK || echo notok
  OK
  
  $ [ condition ] && [ ] || echo notok
  notok
  ```

### 5. 流程控制（重点）

#### if 判断

```shell
if [ 条件判断式 ];then 
  程序 
fi

#或者 

if [ 条件判断式 ]
then
					程序 
					elif [ 条件判断式 ]
					then
										程序
					else
										程序
fi 
```

（1）[ 条件判断式 ]，中括号和条件判断式之间必须有空格

（2）==if后要有空格==

```shell
#!/bin/bash
if [ $1 -eq "1" ]
then
        echo "banzhang zhen shuai"
elif [ $1 -eq "2" ]
then
				echo "cls zhen mei"
fi
```

#### case 语句

```shell
case $变量名 in 
  "值1"）
		如果变量的值等于值1，则执行程序1
		;; 

  "值2"）
	  如果变量的值等于值2，则执行程序2
	   ;; 
	   
	   …省略其他分支… 
  *）

		如果变量的值都不是以上的值，则执行此程序 
	  ;; 
esac
```

注意事项：

1. case行尾必须为单词“in”，每一个模式匹配必须以右括号“）”结束。
2. 双分号“**;;**”表示命令序列结束，相当于java中的break。
3. 最后的“==*）==”表示默认模式，相当于java中的default。

```shell
#!/bin/bash

case $1 in
"1")
		 echo "banzhang"
;;

"2")
			echo "cls"
;;

*)
			echo "renyao"
;;
esac
```

#### for 循环

1. 基本for循环

```shell
for (( 初始值;循环控制条件;变量变化 )) 
do 
  			程序 
done
```

```shell
\#!/bin/bash
s=0
for((i=0;i<=100;i++))
do
			s=$[$s+$i]
done
echo $s
```

2. foreach循环

```shell
for 变量 in 值1 值2 值3…
do 
			 程序 
done
```

```shell
#!/bin/bash
for i in $*
do 
			 echo "ban zhang love $i "
done
```

**比较`$*`和`$@`区别**

（a）$*和$@都表示传递给函数或脚本的所有参数，不被双引号“”包含时，都以`$1 $2 …$n`的形式输出所有参数。

（b）当它们被双引号“”包含时，`"$*"`会将所有的参数作为一个整体，以`$1, $2 ,…$n`的形式输出所有参数；`"$@"`会将各个参数分开，以“$1” “$2”…”$n”的形式输出所有参数。

```shell
\#!/bin/bash
for i in "$*"
\#$*中的所有参数看成是一个整体，所以这个for循环只会循环一次
do
			echo "ban zhang love $i"
done

for j in "$@"
\#$@中的每个参数都看成是独立的，所以“$@”中有几个参数，就会循环几次
do
			echo "ban zhang love $j" 
done
```









[atguigu@hadoop101 datas]$ chmod 777 for.sh

[atguigu@hadoop101 datas]$ bash for.sh cls xz bd

ban zhang love cls xz bd

ban zhang love cls

ban zhang love xz

ban zhang love bd

####while 循环

```shell
while [ 条件判断式 ] 
do 
			程序
done
```

```shell
#!/bin/bash
s=0
i=1
while [ $i -le 100 ]
do
			 s=$[$s+$i]
       i=$[$i+1]
done
echo $s
```

### 6. read读取控制台输入

```
read(选项)(参数)
```

> 选项：
>
> - -p：指定读取值时的提示符
> - -t：指定读取值时等待的时间（秒
>
> 参数：
>
> - 变量：指定读取值的变量名

```shell
#!/bin/bash

read -t 7 -p "Enter your name in 7 seconds " NAME
echo $NAME
```



### 7. 函数

#### 系统函数

1．==basename==基本语法

```shell
basename [string / pathname] [suffix]  ：basename命令会删掉所有的前缀包括最后一个（‘/’）字符，然后将字符串显示出来
```

> suffix为后缀，如果suffix被指定了，basename会将pathname或string中的suffix去掉。

```shell
$ basename /home/atguigu/banzhang.txt 
banzhang.txt

$ basename /home/atguigu/banzhang.txt .txt
banzhang
```



2. ==dirname==基本语法

```shell
dirname 文件绝对路径 ：从给定的包含绝对路径的文件名中去除文件名（非目录的部分），然后返回剩下的路径（目录的部分）
```

> ```shell
> $ dirname /home/atguigu/banzhang.txt 
> /home/atguigu
> ```

####自定义函数

1．基本语法

```shell
[ function ] funname[()]
{
			Action;
      [return int;]

}

funname
```



2．经验技巧

​	（1）必须在调用函数地方之前，先声明函数，==shell脚本是逐行运行==。不会像其它语言一样先编译。

​	（2）函数返回值，==只能通过$?系统变量获得==，可以显示加：return返回，如果不加，将以最后一条命令运行结果，作为返回值。return后跟数值 n(0-255)。==返回值代表是否成功==

3．案例实操

​	（1）计算两个输入参数的和

```shell
#!/bin/bash
function sum()
{
     s=0
     s=$[ $1 + $2 ]
     echo "$s"
}

read -p "Please input the number1: " n1;
read -p "Please input the number2: " n2;
sum $n1 $n2;
```

###8. Shell工具（重点）

#### 1. cut

cut的工作就是“剪”，具体的说就是在文件中负责==剪切数据==用的。cut 命令从文件的每一行剪切字节、字符和字段并将这些字节、字符和字段输出。

1. 基本用法

```shell
cut [选项参数] filename
```

> 说明：默认分隔符是制表符

2.选项参数说明

> | 选项参数 | 功能                         |
> | -------- | ---------------------------- |
> | -f       | 列号，提取第几列             |
> | -d       | 分隔符，按照指定分隔符分割列 |
> | -c       | 指定具体的字符               |



3.案例实操

```shell
数据：
dong shen
guan zhen
wo  wo
lai  lai
le  le

# 切割cut.txt第一列
$ cut -d " " -f 1 cut.txt 

#切割cut.txt第二、三列
[atguigu@hadoop101 datas]$ cut -d " " -f 2,3 cut.txt 

#在cut.txt文件中切割出guan
$ cat cut.txt | grep "guan" | cut -d " " -f 1
```

```shell
$ echo $PATH
/usr/lib64/qt-3.3/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/home/atguigu/bin
#选取系统PATH变量值，第2个“：”开始后的所有路径：
$ echo $PATH | cut -d : -f 2-

#切割ifconfig 后打印的IP地址
$ ifconfig eth0 | grep "inet addr" | cut -d : -f 2 | cut -d" " -f1
192.168.1.102
```

#### 2. sed

sed是一种==流编辑器==，它一次处理一行内容。处理时，把==当前处理的行==存储在临时缓冲区中，称为“模式空间”，接着用sed命令处理缓冲区中的内容，处理完成后，把缓冲区的内容送往屏幕。接着处理下一行，这样不断重复，直到文件末尾。文件内容并没有改变，除非你使用重定向存储输出。

1. 基本用法

```shell
sed [选项参数] ‘command’  filename
```

2. 选项参数说明

1. 

> | 选项参数 | 功能                         |
> | -------- | ---------------------------- |
> | -f       | 列号，提取第几列             |
> | -d       | 分隔符，按照指定分隔符分割列 |
> | -c       | 指定具体的字符               |

3. 命令功能描述

1. 

> | 命令 | 功能                                      |
> | ---- | ----------------------------------------- |
> | a    | ==新增==，a的后面可以接字串，在下一行出现 |
> | d    | ==删除==                                  |
> | s    | ==查找并替换==                            |



##### 正则匹配

```
\   转义
^   一行的开头
    ^R------表示以R开头的行
$   匹配一行的结束
    R$表示以R结尾的行

*   表示上一个子式匹配0次或多次，贪心匹配
    Zo*-----
            Z
            Zo
            Zooo
    .   匹配一个任意的字符
    .*匹配任意字符串
    []  表示匹配某个范围内的字符
    [a-z]------匹配一个a-z之间的字符
    [a-z]*-----匹配任意字母字符串
```

4. 案例实操

```shell
数据：
dong shen
guan zhen
wo  wo
lai  lai
le  le
```

```shell
#将“mei nv”这个单词插入到sed.txt第二行下，打印。
$ sed '2a mei nv' sed.txt 
```

>  注意：==文件并没有改变==

```shell
#删除sed.txt文件所有包含wo的行
$ sed '/wo/d' sed.txt
```

>  注意：‘==g’表示global==，全部替换

```shell
#将sed.txt文件中wo替换为ni
$ sed 's/wo/ni/g' sed.txt 
```

####3. awk

一个强大的文本分析工具，把文件逐行的读入，以空格为默认分隔符将==每行切片，切开的部分再进行分析处理==。

1. 基本用法

```shell
awk [选项参数] 'pattern1{action1}  pattern2{action2}...' filename

pattern：表示AWK在数据中查找的内容，就是匹配模式

action：在找到匹配内容时所执行的一系列命令
```

1. 注意：

2. - 只有==匹配了pattern的行才会执行action==
   - 正则表达式用//包起来

3. 

2. 选项参数说明

> | 选项参数 | 功能                 |
> | -------- | -------------------- |
> | -F       | 指定输入文件折分隔符 |
> | -v       | 赋值一个用户定义变量 |



3. 案例实操

1. ==这里的 \$ n 表示第几列==

```shell
#数据准备
$ sudo cp /etc/passwd ./

#搜索passwd文件以root关键字开头的所有行，并输出该行的第7列。
[atguigu@hadoop102 datas]$ awk -F : '/^root/{print $7}' passwd
/bin/bash

#搜索passwd文件以root关键字开头的所有行，并输出该行的第1列和第7列，中间以“，”号分割。
$ awk -F : '/^root/{print $1","$7}' passwd 
root,/bin/bash
```

```shell
#只显示/etc/passwd的第一列和第七列，以逗号分割，且在所有行前面添加列名user，shell ，在最后一行添加"dahaige，/bin/zuishuai"。
$ awk -F : 'BEGIN{print "user, shell"} {print $1","$7} END{print "dahaige,/bin/zuishuai"}' passwd
```

> 注意：==BEGIN== 在所有数据读取行之前执行；==END==在所有数据执行之后执行

```shell
#将passwd文件中的用户id增加数值1并输出
$ awk -v i=1 -F: '{print $3+i}' passwd
```

4. awk的内置变量

1. 

> | 选项参数 | 说明                                   |
> | -------- | -------------------------------------- |
> | FILENAME | 文件名                                 |
> | NR       | 已读的记录数(行)                       |
> | NF       | 浏览记录的域的个数（切割后，列的个数） |



5. 案例实操

```shell
#统计passwd文件名，每行的行号，每行的列数
$ awk -F: '{print "filename:"  FILENAME ", linenumber:" NR  ",columns:" NF}' passwd 

#切割IP
$ ifconfig eth0 | grep "inet addr" | awk -F: '{print $2}' | awk -F " " '{print $1}' 

#查询sed.txt中空行所在的行号
$ awk '/^$/{print NR}' sed.txt 
```



#### 4. sort

sort命令是在Linux里非常有用，它将文件进行排序，并将排序结果标准输出。

1. 基本语法

   ```
   sort(选项)(参数)
   ```

   

> | 选项 | 功能                     |
> | ---- | ------------------------ |
> | -n   | 依照数值的大小排序       |
> | -r   | 以相反的顺序来排序       |
> | -t   | 设置排序时所用的分隔字符 |
> | -k   | 指定需要排序的列         |

>  **参数**：指定待排序的文件列表



```shell
$ cat passwd | grep ^a | sort -t : -k 3 -n
```



# 企业真实面试题

## Shell

####京东

1. 使用Linux命令查询file1中空行所在的行号

```shell
$ awk /^$/{print NR} file1.txt
```

2. 有文件chengji.txt内容如下:

张三 40

李四 50

王五 60

使用Linux命令计算第二列的和并输出

```shell
cat chengji.txt | awk -F " " '{sum+=$2} END{print sum}'
#or
awk -F " " '{sum+=$2} END{print sum}' chengji.txt
```



####搜狐&和讯网

1. Shell脚本里如何检查一个文件是否存在？如果不存在该如何处理？

```shell
#!/bin/bash
if [ -f file.txt ]; then
   echo "文件存在!"
else
   echo "文件不存在!"
fi
```



#### 新浪

1. 用shell写一个脚本，对文本中无序的一列数字排序,并求和

```shell
$cat test.txt
9
8
7
6
5
4
3
2
10
1
$sort -n test.txt | awk '{a+=$0;print $0}END{print "SUM="a}'
```



####金和网络

1.请用shell脚本写出查找当前文件夹（/home）下所有的文本文件内容中包含有字符”shen”的文件名称

```shell
$ awk 
$ grep -r "shen" /home |cut -d ":" -f 1
# -r表示递归操作 ，grep -r "shen" /home表示对/home目录进行递归操作，找出所有包含"shen"的路径
```