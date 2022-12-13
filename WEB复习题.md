### 第一章

1. 什么是 URL, 什么是 URI，他们由哪几部分组成？URL 与 URI 有什么关系？  
   <font color=" #ff0000 ">URL</font> 是 uniform resource locator，统一资源定位器，指向 Internet 上位于某个位置的某个资源。  
   <font color=" #ff0000 ">URI</font> 是 uniform resource identifier，统一资源标识符，是以特定语法标识一个资源的字符串。  
   <font color=" #ff0000 ">URL 由四部分组成</font>： <font color=" #00b0f0 ">协议名称</font><font color=" #00b0f0 ">、所有主机的 DNS 名、可选的端口号和资源的名称</font>。  
   <font color=" #ff0000 ">URI 由模式和模式特有的部分组成</font>，他们之间用冒号隔开。  
   一般格式如下：_schema: schema - specific - part  
   <font color=" #ff0000 ">关系</font>：URI 是 URL 与 URN 的超集。  

1. HTML 常用标签的使用（表单、文本框、确认按钮等），尤其是 form 标签，包含哪些属性？
   
   1. <font color=" #ff0000 ">method</font> 属性规定用于发送 form-data 的 HTTP 方法。实际上就是请求的方式。  
   2. <font color=" #ff0000 ">name</font> 属性表单的名称。  
   3. <font color=" #ff0000 ">action</font> 属性指定表单请求的路径。  
   4. <font color=" #ff0000 ">target</font> 属性指定 action 的 Url 在哪里打开。  

3. 在服务器端动态生成 Web 页面有哪些技术？它与客户端动态 Web 文档技术有什么区别？
   
   Servlet 和 JSP 分别属于哪种技术？  
   <font color=" #ff0000 ">CGI 技术</font>，服务器扩展技术，在 HTML 页面中嵌入脚本技术  
   <font color=" #ff0000 ">Servlet </font>属于服务器扩展技术；  
   <font color=" #ff0000 ">JSP</font> 属于在 HTML 页面中嵌入脚本技术  

4. 什么是 Servlet？什么是 JSP？他们的主要作用是什么？  
   <font color=" #ff0000 ">Servlet</font> 称为<span style="background: #d3f8b6 ">小服务程序或服务连接器</span>，用 Java 编写的服务器端程序，主要功能在于交互式地浏览和修改数据，生成动态 Web 内容。  
   <font color="#ff0000">JSP</font> 全称 Java Server Pages，<span style="background:#d3f8b6">是一种动态网页开发技术</span>，是一种 Java servlet，主要用于实现 Java web 应用程序的用户界面部分。JSP 通过网页表单获取用户输入数据、访问数据库及其他数据源，然后动态地创建网页。

5. 所有 Web 应用程序的根目录是？WEB-INF 目录包含哪些内容？  
   是 <span style="background: #d3f8b6 ">WEB-INF 目录</span>。包括：  
   1、<font color=" #ff0000 ">web. xml</font> 是部署描述文件  
   2、<font color=" #ff0000 ">classes</font> 用来放置应用程序用到的自定义类 (. class)，必须包括包 (package) 结构。   
   3、<font color=" #ff0000 ">lib</font> 用来放置应用程序用到的 JAR 文件。  


#### 作业题

1 . **简述请求转发和响应重定向的区别**？  
   使用请求转发，在客户的浏览器地址栏中不会显示转发后的资源地址。使用响应重定向，在浏览器的地址栏中可以看到地址的变化。使用请求转发可以共享请求作用域中的数据，使用响应重定向可以共享会话作用域中的数据。  
   
2. login. jsp 为登录页面  
```java :

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

1. 什么是 Servlet 的生命周期？Servlet 的生命周期包括哪几个阶段？  
   <font color="#ff0000">Servlet</font> 作为一种在容器中运行的组件，有一个从创建到销毁的过程被称为 Servlet 的<font color="#ff0000">生命周期</font>。
   包括四个阶段：加载和<span style="background: #d3f8b6 ">实例化</span>、<span style="background: #d3f8b6 ">初始化</span>、<span style="background: #d3f8b6 ">提供服务</span>、<span style="background: #d3f8b6 ">销毁</span>  

2. 常用的 HTTP 请求方法有哪两种？各自的特点是什么？在 Httpservlet 中处理这些请求对应什么方法？
   <font color=" #ff0000 ">GET</font> 方法和 <font color=" #ff0000 ">POST</font> 方法；  
   <span style="background: #d3f8b6 ">GET 方法用来检索资源</span>，GET 对应 doGet () 方法;  
   <span style="background: #d3f8b6 ">POST 方法用来向服务器发送需要处理的数据</span>，POST 对应 doPost () 方法;  

3. 有一个 URL, http://www.myserver.com/hello ？userName=John，问号后面的内容称为什么？有什么含义？<font color=" #ff0000 ">查询串</font>。  

4. 如何检索请求参数？  
   可以使用 ServletRequest 接口中定义的方法
   （1）<font color=" #ff0000 ">public String getParameter (String name)</font>: 返回由 name 指定的请求参数值，如果指定的参数不存在，则返回 null 值。若指定的参数存在，用户没有提供值，则返回空字符串（使用该方法必须保证指定参数值只有一个）  
   （2）<font color=" #ff0000 ">Public String[] getParameterValues (String name)</font>: 返回指定参数 name 所包含的所有值，返回值是一个 String 数组，如果指定的参数不存在，则返回 null 值，该方法适用于参数有多个值  
   （3）<font color=" #ff0000 ">Public Enumeration getParameter (String name)</font>: 返回一个 Enumeration 对象，它包含请求中所有的请求参数名，元素是 String 类型的。如果没有请求参数，则返回一个空的 Enumeration 对象  
   （4）<font color="#ff0000">Public Ma getParameterMaps ()</font>: 返回一个包含所有请求参数的 Map 对象，该对象以参数名作为键、以参数值作为值。键的类型为 String，值的类型为 String 数组。

5. 如何实现请求转发？  
   需要通过请求对象的 getRequestDispatcher () <font color="#ff0000">得到 RequestDispatcher 对象</font>，该对象称为请求转发器对象，格式为 RequestDispatcher getRequestDispatcher（String path），然后通过 <font color="#ff0000">RequestDispatcher</font> 接口中的 <font color="#ff0000">forward</font> 方法（public void forward (ServletRequest request, ServletResponse response)）实现转发

6. 如何使用请求对象存储数据？
   ServletRequest 接口中的方法
   （1）<font color=" #ff0000 ">public void setAttribute (String name, Object obj)</font>: 将指定名称 name 的对象 obj 作为属性值存储到请求对象中  
   （2）<font color=" #ff0000 ">public Object setAttribute (String name)</font>: 返回请求对象中存储的指定名称的属性值，如果指定名称的属性不存在，返回 null，使用该方法在必要时需要作类型转换。  
   （3）<font color=" #ff0000 ">public Enumeration getAttribute name ()</font>: 返回一个 Enumeration 对象，它是请求对象中包含的所有属性名的枚举  
   （4）<font color=" #ff0000 ">Public void removeAttribute (String name)</font>: 从请求对象中删除指定名称的属性  

7. SerevletResponse 如何向客户发送文本数据（<font color=" #ff0000 ">调用 getWriter（）方法获得 Printwriter 对象</font>）  

8. 如何设置响应的内容类型?  
   <span style="background: #d3f8b6 ">使用响应对象的 setContentType ()</span>,  
   
   例：response. setContentType (“text/html; charset=UTF-8”)
   设置响应头  
   （1）<font color=" #ff0000 ">public void setHeader</font> <font color=" #ff0000 ">(String name, String value)</font>: 将指定名称的响应头设置为指定的值  
   （2）<font color=" #ff0000 ">public void setIntHeader</font><font color=" #ff0000 "> (<font color=" #ff0000 ">S</font>tring name, int value)</font>: 用给定的名称和整数值设置响应头  
   （3）<font color=" #ff0000 ">public void setDateHeader</font><font color=" #ff0000 "> (String name, long date)</font>: 用给定的名称和日期值设置响应头  
   （4）<font color=" #ff0000 ">public void addHeader</font><font color=" #ff0000 "> (String name, String value)</font>: 用给定的名称和值添加响应头  
   （5）<font color=" #ff0000 ">public void addIntHeader</font> <font color=" #ff0000 ">(String name, int value)</font>: 用给定的名称和整数值添加响应头  
   （6）<font color=" #ff0000 ">public void addDateHeader </font><font color=" #ff0000 ">(String name, long date)</font>: 用给定的名称和日期值添加响应头  
   （7）<font color=" #ff0000 ">Public boolean containsHeader</font> <font color=" #ff0000 ">(String name)</font>: 返回是否已经设置指定的响应头

9. 如何实现响应重定向？  
   响应重定向是<span style="background: #d3f8b6 ">通过响应对象的 sendRedirect () 实现</span>，格式为 public void sendRedirect (String location)  

10. RequestDispatcher 的 forward 方法转发请求和使用 sendRedirect () 方法重定向请求有何不同？  
    <font color=" #ff0000 ">forward ()</font> 方法转发请求是服务器端控制权的转向，客户端地址栏中不显示转发后的资源地址。  
    <font color=" #ff0000 ">sendRedirect ()</font> 方法是服务器向浏览器发送 302 状态码，它使浏览器连接到新的位置，浏览器地址栏可看到地址的变化。使用重定向，资源不能位于 WEB-INF 目录中。  

11. 部署描述文件的名称和作用是什么？`<servlet>` 元素包含哪些子元素？有什么含义？（尤其是 `<servlet-mapping>` 元素包含哪些子元素？  
    <font color=" #ff0000 ">Deployment Descripior DD</font>，用来初始化 Web 应用程序的组件 
    
    `<servlet>` 元素包含 `<servlet-name>` 元素, 该元素用来定义 Servlet 名称；`<servlet-class>` 元素, 该元素指定 Servlet 类的完整名称；`<init-param>` 元素, 该元素定义向 Servlet 传递的初始化参数；`<load-on-startup>` 元素，该元素指定是否在 Web 应用程序启动时载入该 Servlet。  
    
    `<servlet-mapping>` 元素包含 `< servlet- name >` 和 `< url-pattern >`

12. 请求 URL 的组成? 容器如何解析 URL?  
    请求 URL 由协议与主机名、上下文路径、Servlet 路径、路径信息、查询串组成
    （1）当容器接收到该请求 URL 后，它<span style="background: #d3f8b6 ">首先解析出 URI</span>。<span style="background: #d3f8b6 ">然后从中取出第一部分作为上下文路径</span>，这里是/helloweb，<span style="background: #d3f8b6 ">接下来在容器中查找是否有名称为 helloweb 的 Web 应用程序</span>  
    （2）如果<font color=" #ff0000 ">没有</font>名为 helloweb 的 Web 应用程序，则上下文路径为空，<span style="background: #d3f8b6 ">请求将发送到默认的 Web 应用程序</span>  
    （3）如果<font color=" #ff0000 ">有</font>名为 helloweb 的应用程序，则<span style="background: #d3f8b6 ">继续解析下一部分</span>。容器<span style="background: #d3f8b6 ">尝试将 Servlet 路径与 Servlet 映射匹配</span>，如果找到一个匹配，则完整的 URI 请求就是 Servlet 路径，在这种情况下，路径信息为 null  
    （4）<span style="background: #d3f8b6 ">容器沿着请求 URI 路径树向下</span>，每次一层目录，使用“/”作为路径分隔符，反复尝试最长的路径，看是否与一个 Servlst 匹配。<font color=" #ff0000 ">如果有一个匹配</font>，请求 URI 的匹配部分就是 Servlet 路径，剩余的部分是路径信息  
    （5）<font color=" #ff0000 ">如果不能找到匹配的资源</font>，容器将向客户发送一个 404 错误消息  

13. @WebServlet 和@WebInitParam 注解的用法。  
    <font color=" #ff0000 ">@WebServlet</font>是用来配置 servlet 的属性的，<font color=" #ff0000 ">@WebInitParam</font>是用来配置一些初始化属性的。  
    @WebServlet (  
    name = "WebInitParamExample", urlPatterns = {"/hello"}  
    , initParams = {  
    @WebInitParam (name= "Site : ", value=" http://roseindia.net" ),  
    @WebInitParam (name= "Rose", value= "India"),  
    }  
    )

14. 什么是 ServletConfig 对象？如何获得该对象？该对象定义哪些方法？（尤其是 getInitParameter（）方法）  
    在 Servlet 初始化时，容器将调用 init（ServletConfig），并为其传递一个 ServletConfig 对象，该对象称为 Servlet 配置对象
    （1）<span style="background:#d3f8b6">覆盖 Servlet 的 init（ServletConfig config），然后把容器创建的 ServletConfig 对象保存到一个成员变量中</span>，
    如：ServletConfig config = null;
    Public void init (ServletConfig config) {
        super. init (config);
        this. config = config;
    }  
    （2）<span style="background: #d3f8b6 ">在 Servlet 中直接使用 getServletConfig () 获得 ServletConfig 对象</span>，如：ServletConfig config=getServletConfig ()  
    
    <span style="background: #d3f8b6 ">ServletConfig 接口定义 4 个方式</span>：  
    （1）<font color=" #ff0000 ">public String getInitParameter（String name）</font>：返回指定名称的初始化参数值。若该参数不存在，则返回 null。初始化参数是在 Servlet 初始化时容器从 DD 文件中取出，然后把它包装到 ServletConfig 对象中  
    （2）<font color=" #ff0000 ">Public Enumeration getInitParameterNames（）</font>：返回一个包含所有初始化参数名的 Enumeration 对象，若 Servlet 没有初始化参数，则返回一个空的 Enumeration 对象  
    （3）<font color=" #ff0000 ">public String getServletName（）</font>：返回在 DD 文件中＜servlet-name＞元素指定的 Servlet 名称  
    （4）<font color=" #ff0000 ">public ServletContext getServletContext ()</font>: 返回该 Servlet 所在的上下文对象在部署描述文件中和注解中如何设置 Servlet 初始化参数。  

15. 什么是 ServletContext 对象？如何获得该对象？  
    掌握该对象定义的 getInitParameter（）方法，Servlet 上下文对象的的 RequestDispatcher 方法和 setAttribute ()，getAttribute () 方法的作用。
    
    ServletContext 对象可以<span style="background: #d3f8b6 ">通过`ServletConfig. getServletContext ()`方法</span>获得对 ServletContext 对象的引用，也可以<span style="background: #d3f8b6 ">通过`this. getServletContext ()`方法</span>获得其对象的引用  
    Web 容器在启动时会加载每个 web 应用程序·并为每个 Web 应用程序创建一个唯一的 ServletContext 对象, 该对象一般称为 <font color=" #ff0000 ">Servlet 上下文对象</font>。  
    (1) public void setAttribute (String name, Object object): 将给定名称的属性派对象绑定到上下文对象上。 
    (2) public Object getAttribute (String name): 返回绑定到上下文对象上的给定名称的属性值，如果没有该属性，则返回 null.  
    (3) public Enumeration getAttributeNames (): 返回绑定到上下文对象上的所有属性名 Enumeration 对象.  
    (4) public void removeAttribute (String name): 从上下文对象中删除指定名称的属性。  
    
16. 在 DD 文件中如何声明应用程序的初始化参数？  
    
```java
<init-param>

<param-name>name</param-name>

<param-value>value</param-value>

</init-param>
```

17. 使用 ServletContext 对象存储数据，与使用请求对象存储数据有什么区别？  
    由于一个 WEB 应用中的所有 Servlet 共享同一个 ServletContext 对象，因此 Servlet 对象之间可以通过 ServletContext 对象来实现通讯。ServletContext 对象通常也被称之为 context 域对象  
    
18. Servlet 上下文初始化参数和 Servlet 初始化参数有什么区别？  
    1. Servlet 上下文初始化参数与 Servlet 初始化参数类似，区别是 <span style="background:#d3f8b6">Servlet 上下文初始化参数对整个 web 应用而 Servlet 初始化参数只对应一个 servlet</span>
    2. Servlet 上下文初始化参数在 servlet 中直接调用 getServletContext (). getInitParameter ()  
    3. Servlet 初始化参数定义在 web. xml 中的一个 servlet 元素中，通过 ServletConfig 接口的 getInitParameter (java. lang. String name) 方法。
       
#### 作业题

1. 有一个 URL 为 http://www.myserver.com/hello?userName=John ，问号 (?) 后面的内容称为<font color=" #ff0000 ">请求参数</font>  
2. 要使向服务器发送的数据不在浏览器的地址栏中显示，应该使用 <font color=" #ff0000 ">Post</font> 方法   
3. `<jsp:include>` 标签可以在请求时把另一个 JSP 页面的结果包含到当前页面中  
4. JSP 生命周期方法  <font color=" #ff0000 ">jspInit () 和 jspDestroy () 都可以被覆盖</font>  
5. JSP 代码输出结果是 :  <font color=" #ff0000 ">x 与 y 的和是：9</font>  
```java
<% int x=3; %＞  
<%! int x=5; %＞  
<%! int y=6; %＞  
x与y的和是：＜%=x+y %＞
```
1. 假设 myObj 是一个对象的引用，m1 () 是该对象上一个合法的方法。下面的 JSP 结构哪个是合法的？ `<%=myObj. m1 ()%>` 


### 第三章

1. 在 JSP 页面包含哪些元素？哪三种是 JSP 脚本元素？如何使用他们？ 
   脚本元素：声明、小脚本和表达式。  
   <font color=" #ff0000 ">JSP 声明</font>：<%! Int count = 0; %>  
   <font color=" #ff0000 ">JSP 小脚本</font>：<% count++; %>  
   <font color=" #ff0000 ">JSP 表达式</font>：<% = count;%>  

2. 在 JSP 页面包含哪些指令（<span style="background: #d3f8b6 ">page 指令、include 指令和 taglib 指令</span>）？在 JSP 页面包含哪些动作，如何使用？  
   （下面几种动作必须掌握:  
   <font color=" #ff0000 ">jsp: include</font> 在页面被请求的时候引入一个文件  
   <font color=" #ff0000 ">jsp: forward </font>把请求转到一个新的页面。  
  <font color=" #ff0000 "> jsp: useBean</font> 查找或创建一个 JavaBeans 对象。  
   <font color=" #ff0000 ">jsp: setProperty </font>设置 JavaBeans 对象的属性值。  
   <font color=" #ff0000 ">jsp: getProperty</font> 返回 JavaBeans 对象的属性值。）  

3. 简述 JSP 页面生命周期？  
   (1) <font color=" #ff0000 ">页面转换</font>：对页面解析并创建一个包含对应 Servlet 的 Java 源文件  
   (2) <font color=" #ff0000 ">页面编译</font>：对 Java 源文件编译  
   (3) <font color=" #ff0000 ">加载类</font>：将编译后的类加载到容器中  
   (4) <font color=" #ff0000 ">创建实例</font>：创建一个 Servlet 实例   
   (5) <font color=" #ff0000 ">调用 jspInit ()</font>：调用其他方法之前调用该方法初始化  
   (6) <font color=" #ff0000 ">调用_jspService ()</font>：对每个请求调用一次该方法  
   (7) <font color=" #ff0000 ">调用 jspDestroy ()</font>：当 Servlet 容器决定停止 Servlet 服务时调用该方法  

4. JSP 生命周期方法有哪些？各起什么作用？  
   <font color=" #ff0000 ">_jspInit ()</font>：初始化 Servlet 实例。  
   <font color=" #ff0000 ">jspService ()</font>：每次请求调用一次，实现交互行为。  
   <font color=" #ff0000 ">jspDestroy ()</font>：清理 jspInit () 获得的资源。  

5. 如何将 JSP 页面中的元素转换成 Servlet 代码（转换规则是什么？）？JSP 声明中定义的变量和小脚本中定义的变量有何不同？  
   (1) 所有的 <font color=" #ff0000 ">JSP 声明</font>都转换成页面实现类的成员，它们被原样复制。  
   
   (2) 所有的 <font color=" #ff0000 ">JSP 小脚本</font>都转换成页面实现类的_jspService () 的一部分，它们也被原样复制。小脚本中声明的标量转换成_jspService () 的局部变量，语句转换成_jspService () 中的语句。  
   
   (3) 所有的 <font color=" #ff0000 ">JSP 表达式</font>都转化成_jspService () 的一部分，表达式的值使用 out. print () 语句输出。  

   (4) 有些<font color=" #ff0000 ">指令</font>在转换阶段产生 Java 代码，例如，page 指令的 import 属性转换成页面实现类的 import 语句。  

   (5) 所有的 <font color=" #ff0000 ">JSP 动作</font>都通过调用针对厂商的类来替换。  

   (6) 所有<font color=" #ff0000 ">表达式语言 EL </font>通过计算后使用 out. write () 语句输出。  

   (7) 所有<font color=" #ff0000 ">模板文本</font>都成为_jspService () 的一部分，模板内容是由 out. write () 语句输出。  

   (8) 所有<font color=" #ff0000 "> JSP 注释</font>都被忽略。  

6. 什么是请求时属性表达式？  
   在<span style="background:#d3f8b6">请求时计算 JSP 表达式的值，传递给动作</span>，这个表达式被称为请求时属性表达式。
   例如：  
   <%! String pageURL = “copyright. jsp”%>  
   <jsp: include page = “<% = pageURL%>”/>  

7. JSP 隐含变量有哪些？各代表什么含义？  
   
|request|**HttpServletRequest**类的实例，引用页面的当前请求对象。|
| - | - |
|response|**HttpServletResponse**类的实例，用来向客户发送一个响应。|
|out|**PrintWriter**类的实例，引用页面输出流，用于把结果输出至网页上。|
|session|**HttpSession**类的实例，引用用户对话。|
|application|**ServletContext**类的实例，引用Web应用程序上下文。|
|config|**ServletConfig**类的实例，引用Servlet的配置对象|
|pageContext|<p>**PageContext**类的实例，引用页面上下文，</p><p>提供对JSP页面所有对象以及命名空间的访问</p>|
|page|引用页面的Servlet实例|
|exception|**Exception**类的对象，代表发生错误的JSP页面中对应的异常对象|

8. page 指令的常用属性（<span style="background: #d3f8b6 ">import, contentType, pageEncoding, session, errorPage, isErrorPage</span>）  

9. 什么是静态包含？如何用 include 指令实现？什么是动态包含？如何用 jsp：include 动作实现？他们之间有什么区别？  
   <font color=" #ff0000 ">静态包含</font>是在 JSP <span style="background: #d3f8b6 ">页面转换阶段将另一个文件的内容包含在当前 JSP 页面中</span>。  
   < %@ include file = “relativeURL”% >  
   
   <font color=" #ff0000 ">动态包含</font>是在<span style="background: #d3f8b6 ">请求时将另一个页面的输出包含到主页面的输出中</span>。  
   <jsp: include page=”relativeURL” flush=”true|false”>  
   
   <font color=" #ff0000 ">区别</font>：  
   1. 静态导入是将导入页面的代码完全融入，两个页面融合成一个整体 Servlet；而动态 include 是在 Servlet 中使用 include 方法来引入被导入语页面的内容。  
   2. 静态导入时页面的编译指令会起作用；而动态导入时被导入页面的编译指令则失去作用，只是插入被导入页面的 body 内容  
   3. 最直观的区别就是动态包含可以增加额外的参数  

10. 在 JSP 页面实现请求转发的三种方法？  
   <font color=" #ff0000 "> 1）</font>:
    <%
          RequestDispatcher view = 
          request. getRequestDispatcher ("other. jsp");
          view. forward (request, response);
    %>
    <font color=" #ff0000 ">2）</font>:
    <%
          pageContext. forward ("other. jsp");
    %>
    <font color=" #ff0000 ">3）</font>:
    <jsp: forward page="other. jsp"   
    />  

**11. JSP 的作用域对象有哪些？它们的作用域范围是什么？如何在这些对象上设置和获得属性？ **

|**作用域名**|**对应的对象**|**存在性和可访问性**|
| - | - | - |
|**应用作用域**|**application**|**整个Web应用程序有效**|
|**会话作用域**|**session**|**一个用户对话范围内有效**|
|**请求作用域**|**request**|**在用户的请求和转发的请求内有效**|
|**页面作用域**|**pageContext**|**只在当前的页面内有效**|

<font color="#ff0000">应用作用域</font>：
设置属性：ServletContext context = getServletContext();
        Context. setAttribute (“foo”, one);
获得属性：<% = application. getAttribute (“foo”); %>

<font color="#ff0000">会话作用域</font>：HttpSession session = request.getSession(true);
设置属性：session.setAttribute(“name”,value);
获得属性：session. getAttribute (“name”);

<font color="#ff0000">请求作用域</font>：
设置属性：request.setAttribute(“name”,value);
获得属性：request. getAttribute (“name”)

<font color="#ff0000">页面作用域</font>：
设置属性：<% pageContext.setAttribute(“name”,value);%
获得属性：<% pageContext.getAttribute(“name”);%>


12. 什么是 JavaBeans？要遵循的规范是什么？  
    JavaBeans 是 Java 平台的组件技术，在 JavaWeb 开发中常用 JavaBeans 来存放数据、封装业务逻辑等，从而很好地实现业务逻辑和表示逻辑的分离，是系统具有更好的健壮性和灵活性。
    <font color="#ff0000">规范</font>：
    （1）JavaBeans 应该是 public 类，并且具有无参数的 public 构造方法，通过定义不带参数的构造方法或使用默认的构造方法均可满足这个要求。
    （2）JavaBeans 类的成员变量一般称为属性。对应每个属性访问权限一般定义为 private。
    （3）每个属性通常定义两个 public 方法，一个是访问方法（getter），另一个是修改方法（setter）使用它们访问和修改 JavaBeans 的属性值。

13. 在 JSP 中如何使用 JavaBeans？（<jsp:useBean> <jsp:setProperty>  <jsp:getProperty>），这些动作包含哪些属性，代表什么含义？
    
    <jsp:<font color="#ff0000">useBean</font>>动作用来在 JSP 页面中查找或创建一个 bean 实例。
    属性：  
    <span style="background: #d3f8b6 ">id 属性</span>用来唯一标识一个 bean 实例，该属性是必须的。  
    <span style="background: #d3f8b6 ">scope 属性</span>指定 bean 实例的作用域。  
    <span style="background: #d3f8b6 ">class 属性</span>指定创建 bean 实例的 Java 类。  
    <span style="background:#d3f8b6">Type 属性</span>指定由 id 属性声明的变量的类型，由于该变量是在请求时只想实际的 bean 实例，其类型必须与 bean 类的类型相同或者是其超类，或者是一个 bean 类实现的接口。
    
    <jsp:<font color=" #ff0000 ">setProperty</font>>动作用来给 bean 实例的属性赋值。
    属性：
    <span style="background: #d3f8b6 ">name 属性</span>用来标识一个 bean 实例，该实例必须是前面使用<jsp:useBean>动作声明的，并且 name 属性值必须与<jsp:useBean>动作中指定的一个 id 属性相同。  <span style="background: #d3f8b6 ">property 属性</span>指定要设置值的 bean 实例的属性，容器将根据指定的 bean 的属性调用适当的 setXxx ()，因此该属性也是必须的。  
    <span style="background: #d3f8b6 ">value 属性</span>为 bean 的属性指定新值，该属性值可以接受请求时属性表达式。  
    <span style="background: #d3f8b6 ">param 属性</span>指定请求参数名，如果请求中包含指定的参数，那么使用该参数值来设置 bean 的属性值。
    **Value 和 param 都可选并且不能同时使用**。  
    
    <jsp:<font color=" #ff0000 ">getProperty</font>>动作检索并向输出流中打印 bean 的属性值。  
    属性：  
    <span style="background: #d3f8b6 ">name 属性</span>指定 bean 实例名，<span style="background: #d3f8b6 ">property 属性</span>指定要输出的属性名。  

14. MVC 设计模型中控制器是什么？模型是什么？视图是什么？MVC 设计模型的优点？  
    
    <span style="background: #d3f8b6 ">Servlet 实现控制器功能</span>，它从请求中读取请求信息、创建 JavaBeans 对象、执行业务逻辑、访问数据库等，最后将请求转发到视图组件。  
    <span style="background: #d3f8b6 ">JavaBeans 实现模型功能</span>，用于存放数据。  
    <span style="background: #d3f8b6 ">JSP 页面实现视图功能</span>。  
    最大优点是<font color=" #ff0000 ">将业务逻辑和数据访问从表示层中分离出来</font>。<font color=" #ff0000 ">提高系统的灵活性和复用性</font>。<font color=" #ff0000 ">提高开发效率</font>。  

15. 实现 <font color=" #ff0000 ">MVC 模式的一般步骤</font>是什么？  
    （1）定义 JavaBeans 表示数据  
    （2）使用 Servlet 处理请求  
    （3）填写 JavaBeans 对象数据  
    （4）结果的存储  
    （5）转发请求到 JSP 页面  
    （6）从 JavaBeans 对象中提取数据  

1. 什么是 MVC 设计模式？简述实现 MVC 涉及模式的一般步骤。  
   MVC 组件分为<font color=" #ff0000 ">模型（Model）</font>、<font color=" #ff0000 ">视图（View）</font>和<font color=" #ff0000 ">控制器（Controller</font><font color=" #ff0000 ">）</font>，每种组件完成各自的任务。所有请求的目标都是 Servlet，它充当应用程序的控制器，Servlet 分析请求并将响应所需要的数据收集到 JavaBeans 对象，该对象作为应用程序的模型，最后 Servlet 控制器将请求转发到 JSP 页面。这些页面使用存储在 JavaBeans 中的数据产生响应，该对象作为应用程序的视图。该模型的最大优点是将业务逻辑和数据访问从表示层分离出来。JSP 页面不需要处理任何复杂的逻辑。节省开发的时间和费用，易于维护。 
   实现 MVC 模式的一般步骤： 
    （1）定义 JavaBeans 表示数据  
    （2）使用 Servlet 处理请求  
    （3）填写 JavaBeans 对象数据  
    （4）结果的存储  
    （5）转发请求到 JSP 页面  
    （6）从 JavaBeans 对象中提取数据  
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

1. 什么是会话？  
   会话是<span style="background: #d3f8b6 ">一个客户与服务器之间的不间断的请求响应序列</span>  

2. 如何创建 HttpSession 对象？掌握 HttpSession 对象定义的 getSession（）方法和 setAttribute ()，getAttribute () 方法。  
   <font color="#ff0000">创建 HttpSession 对象</font>需要使用 HttpServletRequest 接口提供的 getSession（）
   
   该方法有两种格式：  
   (1) <font color=" #ff0000 ">public Httpsession getsession (boolean create)</font> 返回或创建与当前请求关联的会话对象。如果没有与当前请求关联的会话对象，当参数为 true 时创建一个新的会话对象，当参数就为 false 时返回 null.  
   (2) <font color="#ff0000">public Httpsession getsession ()</font> 该方法与调用 getsession (true) 等价。

3. 关闭浏览器是否就结束了会话？为何浏览器关闭后再发请求，服务器不再识别用户？  
   让 Session 结束生命周期，有以下两种办法： 
      
   一个是 <font color=" #ff0000 ">Session. invalidate () </font>方法，不过这个方法在实际的开发中，并不推荐，可能在强制注销用户的时候会使用；  
   一个是<font color=" #ff0000 ">当前用户和服务器的交互时间超过默认时间</font>后，Session 会失效  
   
   当<span style="background: #d3f8b6 ">把浏览器关闭时，浏览器并没有向服务器发送任何请求来关闭 Session</span>，自然 Session 也不会被销毁之前的 Session 一直都在服务器端，而当我们关闭浏览器时，此时的 Cookie 是存在于浏览器的进程中的，当浏览器关闭时，Cookie 也就不存在了。  


4. 如何让会话失效（2 个方法）? invalidate () 和在 DD 文件中设置会话超时时间。
   **可以在 DD 文件中设置会话超时时间。  
	<  session-config >  
	< session-timeout > 10 </session-timeout >  
	< /session-config >  

5. 什么是 Cookie？如何构造 Cookie 对象？如何向客户端发送 Cookie ？如何从客户端读取 Cookie？  
   <font color=" #ff0000 ">Cookie 是</font>客户访问 Web 服务器时，服务器在客户硬盘上存放的信息。  
   调用 Cookie 类的构造方法可以<font color=" #ff0000 ">创建 Cookie 对象</font>     
   Cookie userCookie=new Cookie (“username”,”hacker”)；  
   <span style="background: #d3f8b6 ">发送 Cookie 对象</span>需要调用响应对象的 addCookie（）将 Cookie 添加到 Set-Cookie 响应头：  
   Response. addCookie (userCookie);  
   <font color=" #ff0000 ">读取 Cookie</font>：  
   1. <span style="background: #d3f8b6 ">调用请求对象的 getCookie 方法</span>，该方法返回一个 Cookie 对象的数组，如果请求中不含 Cookie，返回 null 值。  Cookie[]cookie=request. getCookie ();
   2. <span style="background: #d3f8b6 ">对 Cookie 数组循环</span>：有了 Cookie 对象数组后，就可以通过循环访问它的每个元素，然后调用每个 Cookie 的 getName (), 直到找到一个与希望的名称相同的对象为止。找到所需要的 Cookie 对象后，一般要调用它的 getValue ()，并根据得到的值做进一步处理

6. 上传文件页面表单域有什么特殊要求？如何上传文件？如何从 Part 对象中检索上传文件的文件名？  

   客户端需要使用 form 表单，method 设为 post，enctype 默认为 application/x- www-form-urlencoded ，这里改为 multipart/form-data，把 input 标签的 type 属性设为 file。  

   用户选择文件提交表单后，服务器端就可以通过 JSP 的内置对象 request（实际上是 HttpServletRequest 的实例）的输入流获取用户表单内容。需要注意的是此输入流不仅包含了用户上传的文件，还包含了表单的其他字段信息，我们可以把此输入流存为临时文件，然后从临时文件中提取用户真正上传的文件。  

7. 文件下载需要完成哪些操作？如何下载文件？  
   <span style="background: #d3f8b6 ">在服务器端把文件转换成输出流，写入到 response</span>，以 response 把文件带到浏览器，由浏览器来提示用户是否愿意保存文件到本地  


#### 作业题

1. 调用哪个方法会使会话失效？<font color=" #ff0000 ">session. invalidate ()</font>
   
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

1. 什么是 JDBC？JDBC 的基本功能是什么？ 

   <font color=" #ff0000 ">JDBC</font>： Java 程序发访问数据库的标准，由一组 Java 语言编写的类和接口组成，这些类和接口称为 JDBC API，它为 Java 程序提供一种通用的数据访问接口。  

   <font color="#ff0000">基本功能包括</font>：建立与数据库的连接、发送 SQL 语句、处理数据库操作结果。

2. 语句对象有哪两种？有什么区别？（Statement 对象，PreparedStatement 对象），语句对象常用的方法有哪些？

   <font color="#ff0000">Statemetent 对象</font>执行的是静态 SQL 语句, 而 <font color="#ff0000">PreparedStatement 对象</font>执行的是预编译 SQL 语句

3. 结果集是什么？如何获得结果集？结果集常用方法有哪些？  

   <font color=" #ff0000 ">结果集</font>：表示 SELECT 语句查询得到的记录结合。  

   <font color=" #ff0000 ">可滚动的结果集</font>指在结果集对象上可以前后移动指针访问结果集中的记录。  

   <font color=" #ff0000 ">可更新的结果集</font>指直接通过结果集对象更新数据库表中数据。   

4. 传统的数据库建立连接的步骤？该方法的缺点（建立连接比较耗费时间，导致增大请求的响应时间）  
 
   传统数据库连接的一般步骤是：  
   <font color=" #ff0000 ">1</font> 加载 JDBC 驱动程序  
   <font color=" #ff0000 ">2</font> 建立连接对象  
   <font color=" #ff0000 ">3</font> 创建语句对象  
   <font color=" #ff0000 ">4</font> 执行 SQL 语句得到结果集对象，调用 ResultSet 的有关方法就可以完成对数据库的操作  
   <font color=" #ff0000 ">5</font> 关闭建立的各种对象  

   <font color=" #ff0000 ">缺点</font>是每次访问数据库都要建立连接对象，请求结束需关闭连接对象。这将耗费大量的时间，可能导致增大请求的响应时间。  

5. 使用数据源连接数据库的优点? 通过数据源对象如何获得连接对象？    

   <span style="background: #d3f8b6 ">使用数据源对象连接数据库，应用程序在启动时只需创建少量的连接对象即可</span>。这样就不需要为每个 HTTP 请求都创建一个连接对象，这会大大降低请求的响应时间。  

   采用 Java 命名与目录接口 （Java Naming and Directory Interface，JNDI）技术来获得 DataSource 对象的引用。<font color="#ff0000">首先</font>为要创建的对象指定一个唯一的名字，<font color="#ff0000">然后</font>由对象工厂创建对象，并将该对象与唯一的名字绑定，外部程序可以通过名字来获得某个对象的访问。

6. 什么是 DAO? 使用它有什么优点? 如何设计和使用 DAO 类？  

   <font color=" #ff0000 ">DAO (Data Access Object)</font> 数据访问对象是一个面向对象的数据库接口，它显露了 Microsoft Jet 数据库引擎（由 Microsoft Access 所使用），并允许 Visual Basic 开发者通过 ODBC 像直接连接到其他数据库一样，直接连接到 Access 表。  
   
   <font color=" #ff0000 ">优点</font>：使用 DAO 技术可以使我们方便的访问 Microsoft Jet 引擎数据库  
   
   
#### 作业题

1. 隔离了数据访问代码和业务逻辑代码

2. 隔离了不同数据库实现

一个典型的 Dao 模式有一下几部分组成：

1. dao 接口：把对数据库的所有操作定义成抽象方法，可以实现多种实现

2. Dao 实现类：针对不同数据库给出 Dao 接口定义方法的具体实现

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

1. 如何调用表达式语言？
   ：<font color=" #ff0000 ">${expression}</font>

2. 使用 EL 表达式如何访问作用域变量？
   ：<font color="#ff0000">${userName}</font>

3. 用 EL 表达式如何访问 JavaBeans 和集合对象？
   ：<font color=" #ff0000 ">${name. class}</font>

4. EL 的隐含变量的使用？
   例如访问 Accept 请求头，可使用 <font color="#ff0000">header 隐含变量</font>
   `${header.Accept}` 或$ `{header[“Accept”]}`

5. 在 EL 中都可以访问哪些类型的数据？ 
   某个 <font color="#ff0000">web 域中的对象</font>，访问 <font color="#ff0000">javabean 的属性</font>、访问 <font color="#ff0000">list</font>, <font color="#ff0000">map 集合</font>、访问<font color="#ff0000">数组</font>


1. EL 表达式语言可用于在网页上生成动态的内容并代替 JSP 元素，EL 表达式语言的语法是 <font color=" #ff0000 ">${ELexpression}</font>
   
2. 在 JavaWeb 应用程序中，EL 表达式可用于访问（）中存储的数据 <font color=" #ff0000 ">JavaBeans</font>
   
3. 下面哪个变量不能用在 EL 表达式中？<font color=" #ff0000 ">contextScope</font>
   
4. 表达式${(10 le 10)＆＆! (24+ 1 lt 24)?”Yes”:”No”}的结果是 <font color=" #ff0000 ">YES</font>
   `算术运算符 + 、 - 、 * 、 / （或 div ）和 % （或 mod ）`
   
   `关系运算符 == （或 eq ）、 != （或 ne ）、 < （或 lt ）、 > （或 gt ）、 <= （或 le ）和 >= （或 ge ）`
   
   `逻辑运算符 && （或` `and` `）、 || （或` `or` `）和 ! （或 not ）`
   
   `验证运算符` `empty`
5. EL 显示请求的 URI，下面哪个是正确的 <font color=" #ff0000 ">${pageContext. request. requestURI}</font>
   
6. EL 表达式${user. loginName}的执行效果等同于以下哪个选项：? (user 是一个 JavaBean 对象，loginName 是它其中的一个属性。） <font color=" #ff0000 ">＜%=user. getLoginName ()%＞</font>
   
7. 一个 Web 站点将管理员的 E-mail 地址存储在一个名为 master-email 的 ServletContext 参数中，如何使用 EL 得到这个值<font color=" #ff0000 ">${initParam. master-email}</font>
   ServletContext 用于存放全局变量
   
8. 给定一个 HTML 表单，其中使用了有一个名为 hobbies 的复选框，如下所示：  
   兴趣：＜input type=”checkbox” name=”hobbies” value=”reading”＞  
   文学＜input type=”checkbox” name=”hobbies” value=”sport”＞  
   体育＜input type=”checkbox” name=”hobbies” value=”computer”＞电脑＜br＞  下面哪些表达式能够计算并得到 hobbies 参数的第一个值?
   ：<font color=" #ff0000 ">${ paramValues . hobbies[0]}</font>
   

- 写出使用 EL 表达式访问应用作用域上存储的属性名为 count 的变量所对应的值的语句：
  ${<font color=" #ff0000 ">applicationScope</font>. count}   
  
- 阅读下列程序片段，写成访问该页面的输出结果。 

```java
＜%@page import="java.util.ArrayList"＞  

＜% ArrayListcity=newArrayList(); city.add("Beijing");  

city.add("Shanghai");  

city.add("Guangzhou"); 

 request.setAttribute("myLocation",city);  %＞
```

我最喜欢的城市是:${myLocation[2]}.     输出结果：<font color=" #ff0000 ">Guangzhou</font>

   