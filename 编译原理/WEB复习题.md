1. **简述请求转发和响应重定向的区别**？
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
1. 假设 myObj 是一个对象的引用，m1 () 是该对象上一个合法的方法。下面的 JSP 结构哪个是合法的？ <font color=" #ff0000 "><%=myObj. m1 ()%></font>


1. 什么时 MVC 设计模式？简述实现 MVC 涉及模式的一般步骤。
   MVC 组件分为模型（Model）、视图（View）和控制器（Controller），每种组件完成各自的任务。所有请求的目标都是 Servlet，它充当应用程序的控制器，Servlet 分析请求并将响应所需要的数据收集到 JavaBeans 对象，该对象作为应用程序的模型，最后 Servlet 控制器将请求转发到 JSP 页面。这些页面使用存储在 JavaBeans 中的数据产生响应，该对象作为应用程序的视图。该模型的最大优点是将业务逻辑和数据访问从表示层分离出来。JSP 页面不需要处理任何复杂的逻辑。节省开发的时间和费用，易于维护。
   实现 MVC 模式的一般步骤：
   （1）使用 Servlet 处理请求；
   （3）填写 JavaBeans 对象数据；
   （4）将结果存储在作用域对象中；
   （5）将请求转发到 JSP 页面；
   （6）最后在 JSP
   
```
```
