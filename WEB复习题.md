### 第一章

1 . **简述请求转发和响应重定向的区别**？
   使用请求转发，在客户的浏览器地址栏中不会显示转发后的资源地址。使用响应重定向，在浏览器的地址栏中可以看到地址的变化。使用请求转发可以共享请求作用域中的数据，使用响应重定向可以共享会话作用域中的数据。
   
2. 
   ```java
   login.jsp为登录页面:

＜%@ page contentType="text/html; charset=UTF-8"pageEncoding="UTF-8"%＞

＜html＞

＜head＞

＜title＞登录页面＜/title＞

＜/head＞

＜body＞

＜form action="login.do" method="post"＞   

＜table＞   

＜tr＞＜td＞用户名：＜/td＞       ＜td＞＜input type=（1）"__________" name="username"/＞＜/td＞   ＜/tr＞   

＜tr＞＜td＞密  码：＜/td＞        ＜td＞＜input type=（2）"__________" name="password"/＞＜/td＞   ＜/tr＞   

＜tr＞＜td＞＜input type=（3）"__________" value="登录"/＞＜/td＞       ＜td＞＜input type="reset" value="取消"/＞＜/td＞   ＜/tr＞   

＜/table＞

＜/form＞

＜/body＞

＜/html＞

 在登录页面点击登录按钮，资源跳转到LoginServlet.java，如果用户名和口令均为admin，认为登录成功，跳转到欢迎页面:
@WebServlet(name="LoginServlet",urlPatterns=(4){"/__________"})
public class LoginServlet extends （5）__________
{public void （6）__________(HttpServletRequest request, HttpServletResponse response)throws ServletException, IOException 
{String username = request.（7）__________("username");     
 String password = request.（8）__________("password");      
// 用户名和口令均为admin，认为登录成功      
if(username.equals("admin")＆＆password.equals("admin"))
{          request.setAttribute("username", username);  
RequestDispatcher rd =（9）request. __________  ("/welcome.jsp");        
 rd.（10）__________(request, response);    

  }  

 }

}


```
 1. text
 2. password
 3. submit
 4. login. do
 5. doPost
 6. HttpServlet
 7. getParameter
 8. getParameter
 9. getRequestDispatcher
 10. forward
     
### 第二章
1. 有一个 URL 为 http://www.myserver.com/hello?userName=John ，问号 (?) 后面的内容称为<font color=" #ff0000 ">请求参数</font>
2. 要使向服务器发送的数据不在浏览器的地址栏中显示，应该使用 <font color=" #ff0000 ">Post</font> 方法 
3. `<jsp:include>` 标签可以在请求时把另一个 JSP 页面的结果包含到当前页面中
4. JSP 生命周期方法  <font color="#ff0000">jspInit () 和 jspDestroy () 都可以被覆盖</font>
5. JSP 代码输出结果是 :  <font color="#ff0000">x与y的和是：9</font>
```java
<% int x=3; %＞  
<%! int x=5; %＞  
<%! int y=6; %＞  
x与y的和是：＜%=x+y %＞
```
1. 假设 myObj 是一个对象的引用，m1 () 是该对象上一个合法的方法。下面的 JSP 结构哪个是合法的？ `<%=myObj. m1 ()%>`


### 第三章
1. 什么时 MVC 设计模式？简述实现 MVC 涉及模式的一般步骤。
   MVC 组件分为模型（Model）、视图（View）和控制器（Controller），每种组件完成各自的任务。所有请求的目标都是 Servlet，它充当应用程序的控制器，Servlet 分析请求并将响应所需要的数据收集到 JavaBeans 对象，该对象作为应用程序的模型，最后 Servlet 控制器将请求转发到 JSP 页面。这些页面使用存储在 JavaBeans 中的数据产生响应，该对象作为应用程序的视图。该模型的最大优点是将业务逻辑和数据访问从表示层分离出来。JSP 页面不需要处理任何复杂的逻辑。节省开发的时间和费用，易于维护。
   实现 MVC 模式的一般步骤：
   （1）使用 Servlet 处理请求；
   （3）填写 JavaBeans 对象数据；
   （4）将结果存储在作用域对象中；
   （5）将请求转发到 JSP 页面；
   （6）最后在 JSP
2. 
```java
请在横线处将程序补充完整。

queryStudent.jsp :在该页面输入学生学号，点击“确定”按钮，页面跳转到querystudent.do对应的servlet程序。学生学号要保密，不能在浏览器地址栏显示出来。

＜%@page contentType="text/html;charset=UTF-8" pageEncoding="UTF-8"%＞

＜html＞ 

＜head＞

＜title＞ 学生查询 

＜/title＞ 

＜/head＞

＜body＞

＜formaction="①querystudent.do"method="② post "＞    

学号：  ＜inputtype="text"name="studentID"size="15"＞ 

姓名：  ＜inputtype="text"name=" studentName "size="10"＞ 

＜inputtype=③" submit"    value="确定"＞

＜/form＞

＜/body＞ 

＜/body＞ 

＜/html＞

在 querystudent.do对应的servlet程序中，把queryStudent.jsp页面中填写的学生信息存放在名为student的JavaBeans对象中，并把该对象作为属性存储在请求作用域，然后请求转发到 displayStudent.jsp 。 

displayStudent.jsp ：从JavaBeans对象中收集学生信息，并在该页面中显示出来。 

＜%@pagecontentType="text/html;charset=utf-8"%＞

＜jsp:useBeanid="student"type="com.demo.Student"scope=" ④request  "/＞

＜html＞ 

＜head＞ ＜title＞ 学生信息 ＜/title＞ ＜/head＞

＜body＞

学号：＜jsp:⑤getProperty  name="student"property="stu_id"/＞ ＜br＞

姓名：＜jsp:getPropertyname="student"property="stu_name"/＞

＜/body＞

＜/html＞
```

```java
下面代码存在三处错误，请找出错误并改正。

1行＜%@PagecontentType="text/html;charset=UTF-8"%＞

2行＜html＞＜body＞

3行＜%!floatnumber=0%＞

4行＜%number=number+1;%＞

5行number的值:＜%=number;%＞次。

6行＜/body＞＜/html＞

错误1位于第（）行，改正（）

错误2位于第（）行，改正（）

错误3位于第（）行，改正（）
/**
1行  改为page小写p

3行  改为＜%!floatnumber=0;%＞，要带分号。

5行   改为＜%=number%＞，表达式要去掉分号。
**/

```

### 第四章

1. 调用哪个方法会使会话失效？<font color="#ff0000">session.invalidate()</font>
2. 下面通过哪个接口或类获取与用户相关的会话对象 <font color=" #ff0000 ">HttpServletRequest</font>
3. 给定 request 是一个 HttpServletRequest 对象，下面哪行代码会在不存在会话的情况下创建一个会话？<font color=" #ff0000 ">request. getSession ()</font>
4. HTTP 协议变成了有状态的协议服务器为用户所产生的会话 ID 是唯一的浏览器可设置是否使用 cookie 的功能 
5. 会话的超时时间设置为-1，则会话永远不会过期。
6. 给定一个会话对象 s，有两个属性分别为 myAttrl 和 myAttr2, 下面哪段代码会把这两个属性从会话中删除 
   <font color=" #ff0000 ">s.removeAttribute ("myAttrl") s.removeAttribute ("myAttr2")</font>
7. 将下面哪个代码片段插入到 doGet（）中可以正确记录用户的 GET 请求的数量？
   
```java
HttpSessionsession=request.getSession();

intcount=((Integer)session.getAttribute(“count”).intValue();

session.setAttribute(“count”,newInteger(++count));

```

8. 以下哪段代码能从请求中获取名为"ORA-UID"的 Cookie 的值？
 
```java
Cookie[] cookies=request.getCookies();  
String cName=null;  
String value=null;  
if(cookies!=null)/{  
for(int i=0;i<cookies.length;i++)/{  
cName=cookies[i].getName();  
if(cName!=null&&cName.equals("ORA_UID")){  
value=cookies[i].getValue();  
}  
}  
}
```

1. 上传文件如何从 Part 对象中检索上传文件的文件名？上传文件使用什么表单域？表单那有什么特殊要求？
   调用 part 对象的 String getHeader (String name) 方法，参数 name 上传文件使用 `<input type="file">` 的输入域用于指定上传的文件。上传文件表单的 `<form>` 标签中应该指定 enctype 属性，它的值应该为“multipart/form-data”，  `<form>` 标签的 method
   
   
   

### 第五章

1. Statement 接口的 exeteQuery (String sql) 方法用来执行 SQL 的 <font color=" #ff0000 ">查询</font> 语句
2. PreparedStatement 对象通常用来执行动态 SQL 语句，此时需要在 SQL 语句中通过
   <font color=" #ff0000 ">问号</font> 指定参数
3. 使用 Class 类的 forName () 加载驱动程序需要捕获什么异常？
    ：<font color=" #ff0000 ">ClassNotFoundException</font>
4. Web 应用程序需要访问数据库，数据库驱动程序应该安装在哪个目录？WEB-INF\lib
5. 对于新产生的结果集对象，调用 ResultSet 的（）方法，使游标指向第一行 <font color=" #ff0000 ">next ()</font>
   
- 试说明使用数据源对象连接数据库的优点是什么？通过数据源对象如何获得连接对象？
  
    这种方法是事先建立若干连接对象，将它们存放在数据库连接池中供应用程序共享。应用程序需要连接数据库，就从连接池中取出一个连接对象，使用完后将其放回。使用这种技术，<font color="#ff0000">应用程序在启动时只需创建少量的连接对象即可，不需要每次都建立连接对象，提高数据库访问效率。</font>
    需要采用 Java 命名与目录接口（JNDI）技术来获得 DataSource 对象的引用。使用 javax. naming. Context 接口的 lookup () 查找 JNDI 数据源，得到了 DataSource 对象的引用后，就可以通过它的 getConnection () 获得数据库连接对象 Connection。
    
- 为本章的 CustomerDao. java 程序增加两个方法实现删除和修改客户信息，这两个方法的格式为：  
  `public boolean deleteCustomer (String custName)`  
  `public boolean updateCustomer(CustomerBean customer)`
  
```java
// 按姓名删除客户记录  
public boolean deleteCustomer(String custName){  
Connection conn = null;  
PreparedStatement pstmt = null;  
ResultSet rst = null;  
CustomerBean customer =null;  
try{  
conn = dataSource.getConnection();  
pstmt = conn.prepareStatement(DELETE_SQL);  
pstmt.setString(1,custName);  
int n = pstmt.executeUpdate();  
if(n ==1){  
return true;  
}else{  
return false;  
}  
}catch(SQLException se){  
return false;  
}finally{  
try{  
pstmt.close();  
conn.close();  
}catch(SQLException se){}  
}  
}  
// 修改客户记录  
public boolean updateCustomer(CustomerBean customer){  
Connection conn = null;  
PreparedStatement pstmt = null;  
try{  
conn = dataSource.getConnection();  
pstmt = conn.prepareStatement(UPDATE_SQL);  
pstmt.setString(1,customer.getEmail());  
pstmt.setString(2,customer.getPhone());  
pstmt.setString(3,customer.getCustName());  
int n = pstmt.executeUpdate();  
if(n ==1){  
return true;  
}else{  
return false;  
}  
}catch(SQLException se){  
return false;  
}finally{  
try{  
pstmt.close();  
conn.close();  
}catch(SQLException se){}  
}  
}
```


### 第六章

1. EL 表达式语言可用于在网页上生成动态的内容并代替 JSP 元素，EL 表达式语言的语法是 <font color=" #ff0000 ">${ELexpression}</font>
2. 在 JavaWeb 应用程序中，EL 表达式可用于访问（）中存储的数据 <font color=" #ff0000 ">JavaBeans</font>
3. 下面哪个变量不能用在 EL 表达式中？<font color=" #ff0000 ">contextScope</font>
4. 表达式${(10 le 10)＆＆! (24+ 1 lt 24)?”Yes”:”No”}的结果是 <font color=" #ff0000 ">YES</font>
   `算术运算符 + 、 - 、 * 、 / （或 div ）和 % （或 mod ）`
   
   `关系运算符 == （或 eq ）、 != （或 ne ）、 < （或 lt ）、 > （或 gt ）、 <= （或 le ）和 >= （或 ge ）`
   
   `逻辑运算符 && （或` `and` `）、 || （或` `or` `）和 ! （或 not ）`
   
   `验证运算符` `empty`
5. 
   