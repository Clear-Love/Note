考试题型：填空、选择、简答、综合、编程

# 第1章

1. 什么是URL, 什么是 URI，他们由哪几部分组成？URL与URI有什么关系？

解：

URL是uniform resource locator，统一资源定位器，指向Internet上位于某个位置的某个资源。

URI是uniform resource identifier，统一资源标识符，是以特定语法标识一个资源的字符串。

URL由四部分组成： 协议名称、所有主机的DNS名、可选的端口号和资源的名称。

URI由模式和模式特有的部分组成，他们之间用冒号隔开。

一般格式如下：schema:schema - specific - part

关系：URI是URL与URN的超集。

2. HTML常用标签的使用（表单、文本框、确认按钮等），尤其是form标签，包含哪些属性？

解：

①method属性

规定用于发送 form-data 的 HTTP 方法。实际上就是请求的方式。

②name属性

表单的名称。

③action属性

指定表单请求的路径 。

④target属性

指定action的Url在哪里打开。

3. 在服务器端动态生成Web页面有哪些技术？它与客户端动态Web文档技术有什么区别？Servlet和JSP分别属于哪种技术？

解：

CGI技术，服务器扩展技术，在HTML页面中嵌入脚本技术

Servlet属于服务器扩展技术；JSP属于在HTML页面中嵌入脚本技术

4. 什么是Servlet？什么是JSP？他们的主要作用是什么？

解：

Servlet称为小服务程序或服务连接器，用Java编写的服务器端程序，主要功能在于交互式地浏览和修改数据，生成动态Web内容。

JSP全称Java Server Pages，是一种动态网页开发技术，是一种Java servlet，主要用于实现Java web应用程序的用户界面部分。JSP通过网页表单获取用户输入数据、访问数据库及其他数据源，然后动态地创建网页。

5. 所有Web应用程序的根目录是？WEB-INF目录包含哪些内容？

解：

      是WEB-INF目录。包括：

      1、web.xml 是部署描述文件

2、classes 用来放置应用程序用到的自定义类(.class)，必须包括包(package)结构。

3、lib 用来放置应用程序用到的JAR文件。

# 第2章

1. 什么是Servlet的生命周期？Servlet的生命周期包括哪几个阶段？

解：

Servlet作为一种在容器中运行的组件，有一个从创建到销毁的过程被称为Servlet的生命周期。

包括四个阶段：加载和实例化、初始化、提供服务、销毁

2. 常用的HTTP请求方法有哪两种？各自的特点是什么？在Httpservlet中处理这些请求对应什么方法？

解：

GET方法和POST方法；

GET方法用来检索资源，GET对应doGet()方法;

POST方法用来向服务器发送需要处理的数据，POST对应doPost()方法;

3. 有一个URL,http://www.myserver.com/hello？userName=John，问号后面的内容称为什么？有什么含义？

解：

      查询串。

4. 如何检索请求参数？

解：

可以使用ServletRequest接口中定义的方法

（1）public String getParameter(String name):返回由name指定的请求参数值，如果指定的参数不存在，则返回null值。若指定的参数存在，用户没有提供值，则返回空字符串（使用该方法必须保证指定参数值只有一个）

（2）Public String[] getParameterValues(String name):返回指定参数name所包含的所有值，返回值是一个String数组，如果指定的参数不存在，则返回null值，该方法适用于参数有多个值

（3）Public Enumeration getParameter(String name):返回一个Enumeration对象，它包含请求中所有的请求参数名，元素是String类型的。如果没有请求参数，则返回一个空的Enumeration对象

（4）Public Ma getParameterMaps():返回一个包含所有请求参数的Map对象，该对象以参数名作为键、以参数值作为值。键的类型为String，值的类型为String数组。

5. 如何实现请求转发？

解：

需要通过请求对象的getRequestDispatcher()得到RequestDispatcher对象，该对象称为请求转发器对象，格式为RequestDispatcher getRequestDispatcher（String path），然后通过RequestDispatcher接口中的forward方法（public void forward(ServletRequest request, ServletResponse response)）实现转发

6. 如何使用请求对象存储数据？

解：

ServletRequest接口中的方法

（1）public void setAttribute(String name,Object obj):将指定名称name的对象obj作为属性值存储到请求对象中

（2）public Object setAttribute(String name):返回请求对象中存储的指定名称的属性值，如果指定名称的属性不存在，返回null，使用该方法在必要时需要作类型转换。

（3）public Enumeration getAttribute name():返回一个Enumeration对象，它是请求对象中包含的所有属性名的枚举

（4）Public void removeAttribute(String name):从请求对象中删除指定名称的属性

7. SerevletResponse如何向客户发送文本数据（调用getWriter（）方法获得Printwriter对象）

解：

8. 如何设置响应的内容类型?

解：

使用响应对象的setContentType(),

例：response.setContentType(“text/html;charset=UTF-8”)

设置响应头

（1）public void setHeader(String name,String value):将指定名称的响应头设置为指定的值

（2）public void setIntHeader(String name,int value):用给定的名称和整数值设置响应头

（3）public void setDateHeader(String name,long date):用给定的名称和日期值设置响应头

（4）public void addHeader(String name,String value):用给定的名称和值添加响应头

（5）public void addIntHeader(String name,int value):用给定的名称和整数值添加响应头

（6）public void addDateHeader(String name,long date):用给定的名称和日期值添加响应头

（7）Public boolean containsHeader(String name):返回是否已经设置指定的响应头

9. 如何实现响应重定向？

解：

响应重定向是通过响应对象的sendRedirect()实现，格式为public void sendRedirect(String location)

10. RequestDispatcher的forward方法转发请求和使用sendRedirect()方法重定向请求有何不同？

解：

forward()方法转发请求是服务器端控制权的转向，客户端地址栏中不显示转发后的资源地址。

sendRedirect()方法是服务器向浏览器发送302状态码，它使浏览器连接到新的位置，浏览器地址栏可看到地址的变化。使用重定向，资源不能位于WEB-INF目录中。

11. 部署描述文件的名称和作用是什么？`<servlet>`元素包含哪些子元素？有什么含义？（尤其是`<servlet-mapping>`元素包含哪些子元素？

解：

Deployment Descripior DD，用来初始化Web应用程序的组件

`<servlet>`元素包含`<servlet-name>`元素,该元素用来定义Servlet名称；`<servlet-class>`元素,该元素指定Servlet类的完整名称；`<init-param>`元素,该元素定义向Servlet传递的初始化参数；`<load-on-startup>`元素，该元素指定是否在Web应用程序启动时载入该Servlet。

`<servlet-mapping>`元素包含`< servlet- name >`和`< url-pattern >`

12. 请求URL的组成?容器如何解析URL?

解：

请求URL由协议与主机名、上下文路径、Servlet路径、路径信息、查询串组成

（1）当容器接收到该请求URL后，它首先解析出URI。然后从中取出第一部分作为上下文路径，这里是/helloweb，接下来在容器中查找是否有名称为helloweb的Web应用程序

（2）如果没有名为helloweb的Web应用程序，则上下文路径为空，请求将发送到默认的Web应用程序

（3）如果有名为helloweb的应用程序，则继续解析下一部分。容器尝试将Servlet路径与Servlet映射匹配，如果找到一个匹配，则完整的URI请求就是Servlet路径，在这种情况下，路径信息为null

（4）容器沿着请求URI路径树向下，每次一层目录，使用“/”作为路径分隔符，反复尝试最长的路径，看是否与一个Servlst匹配。如果有一个匹配，请求URI的匹配部分就是Servlet路径，剩余的部分是路径信息

（5）如果不能找到匹配的资源，容器将向客户发送一个404错误消息

13. @WebServlet和@WebInitParam注解的用法。

14. 什么是ServletConfig对象？如何获得该对象？该对象定义哪些方法？（尤其是getInitParameter（）方法）

解：

在Servlet初始化时，容器将调用init（ServletConfig），并为其传递一个ServletConfig对象，该对象称为Servlet配置对象

（1）覆盖Servlet的init（ServletConfig config），然后把容器创建的ServletConfig对象保存到一个成员变量中，如：ServletConfig config = null;

Public void init(ServletConfig config) {

      super.init(config);

this.config = config;

}

（2）在Servlet中直接使用getServletConfig()获得ServletConfig对象，如：ServletConfig config=getServletConfig()

ServletConfig接口定义4个方式：

（1）public String getInitParameter（String name）：返回指定名称的初始化参数值。若该参数不存在，则返回null。初始化参数是在Servlet初始化时容器从DD文件中取出，然后把它包装到ServletConfig对象中

（2）Public Enumeration getInitParameterNames（）：返回一个包含所有初始化参数名的 Enumeration对象，若Servlet没有初始化参数，则返回一个空的Enumeration对象

（3）public String getServletName（）：返回在DD文件中＜servlet-name＞元素指定的Servlet名称

（4）public ServletContext getServletContext():返回该Servlet所在的上下文对象在部署描述文件中和注解中如何设置Servlet初始化参数。

15. 什么是 ServletContext对象？如何获得该对象？掌握该对象定义的getInitParameter（）方法，Servlet上下文对象的的RequestDispatcher方法和setAttribute ()，getAttribute ()方法的作用。

解：

Web容器在启动时会加载每个web应用程序·并为每个Web应用程序创建一个唯一的ServletContext对象,该对象一般称为Servlet上下文对象。

16. 在 DD 文件中如何声明应用程序的初始化参数？

解：

<init-param>

<param-name>name</param-name>

<param-value>value</param-value>

</init-param>

17. 使用ServletContext对象存储数据，与使用请求对象存储数据有什么区别？

解：

(1)public void setAttribute(String name,Object object):将给定名称的属性派对象绑

定到上下文对象上。

(2)public Object getAttribute(String name):返回绑定到上下文对象上的给定名称的属

性值，如果没有该属性，则返回null.

(3)public Enumeration getAttributeNames():返回绑定到上下文对象上的所有属性名

) Enumeration 对象.

(4) public void removeAttribute(String name):从上下文对象中删除指定名称的属性。

18. Servlet上下文初始化参数和Servlet初始化参数有什么区别？

解：

1. Servlet 上下文初始化参数与 Servlet 初始化参数类似，区别是 Servlet 上下文初始化参数对整个 web 应用而 Servlet 初始化参数只对应一个 servlet

2. Servlet 上下文初始化参数在 servlet 中直接调用 getServletContext (). getInitParameter ()

3. Servlet 初始化参数定义在 web. xml 中的一个 servlet 元素中，通过 ServletConfig 接口的 getInitParameter (java. lang. String name) 方法。

# 第3章

1. 在JSP页面包含哪些元素？哪三种是JSP脚本元素？如何使用他们？

解：

脚本元素：声明、小脚本和表达式。

JSP声明：<%! Int count = 0; %>

JSP小脚本：<% count++; %>

JSP表达式：<% = count;%>

2. 在JSP页面包含哪些指令（page指令、include指令和taglib指令）？在JSP页面包含哪些动作，如何使用？

解：

（下面几种动作必须掌握:

jsp:include

jsp:forward

jsp:useBean查找或创建一个JavaBeans对象。

jsp:setProperty设置JavaBeans对象的属性值。

jsp:getProperty返回JavaBeans对象的属性值。）

3. 简述JSP页面生命周期？

解：

(1) 页面转换：对页面解析并创建一个包含对应Servlet的Java源文件

(2) 页面编译：对Java源文件编译

(3) 加载类：将编译后的类加载到容器中

(4) 创建实例：创建一个Servlet实例

(5) 调用jspInit()：调用其他方法之前调用该方法初始化

(6) 调用_jspService()：对每个请求调用一次该方法

(7) 调用jspDestroy()：当Servlet容器决定停止Servlet服务时调用该方法

4. JSP生命周期方法有哪些？各起什么作用？

解：

jspInit()：初始化Servlet实例。

_jspService()：每次请求调用一次，实现交互行为。

jspDestroy()：清理jspInit()获得的资源。

5. 如何将JSP页面中的元素转换成Servlet代码（转换规则是什么？）？JSP声明中定义的变量和小脚本中定义的变量有何不同？

解：

(1) 所有的JSP声明都转换成页面实现类的成员，它们被原样复制。

(2) 所有的JSP小脚本都转换成页面实现类的_jspService()的一部分，它们也被原样复制。

小脚本中声明的标量转换成_jspService()的局部变量，语句转换成_jspService()中的语句。

(3) 所有的JSP表达式都转化成_jspService()的一部分，表达式的值使用out.print()语句输出。

(4) 有些指令在转换阶段产生Java代码，例如，page指令的import属性转换成页面实现类的import语句。

(5) 所有的JSP动作都通过调用针对厂商的类来替换。

(6) 所有表达式语言EL通过计算后使用out.write()语句输出。

(7) 所有模板文本都成为_jspService()的一部分，模板内容是由out.write()语句输出。

(8) 所有JSP注释都被忽略。

6. 什么是请求时属性表达式？

解：

在请求时计算JSP表达式的值，传递给动作，这个表达式被称为请求时属性表达式。

例如：<%! String pageURL = “copyright.jsp”%>

        <jsp:include page = “<% = pageURL%>”/>

7. JSP隐含变量有哪些？各代表什么含义？

解：

request

HttpServletRequest类的实例，引用页面的当前请求对象。

response

HttpServletResponse类的实例，用来向客户发送一个响应。

out

PrintWriter类的实例，引用页面输出流，用于把结果输出至网页上。

session

HttpSession类的实例，引用用户对话。

application

ServletContext类的实例，引用Web应用程序上下文。

config

ServletConfig类的实例，引用Servlet的配置对象

pageContext

PageContext类的实例，引用页面上下文，

提供对JSP页面所有对象以及命名空间的访问

page

引用页面的Servlet实例

exception

Exception类的对象，代表发生错误的JSP页面中对应的异常对象

8. page指令的常用属性（import, contentType, pageEncoding, session, errorPage, isErrorPage）

9. 什么是静态包含？如何用include指令实现？什么是动态包含？如何用jsp：include动作实现？他们之间有什么区别？

解：

静态包含是在JSP页面转换阶段将另一个文件的内容包含在当前JSP页面中。

<%@ include file = “relativeURL”%>

动态包含是在请求时将另一个页面的输出包含到主页面的输出中。

<jsp:include page=”relativeURL” flush=”true|false”>

区别：

1.静态导入是将导入页面的代码完全融入，两个页面融合成一个整体Servlet；而动态include是在Servlet中使用include方法来引入被导入语页面的内容。

2.静态导入时页面的编译指令会起作用；而动态导入时被导入页面的编译指令则失去作用，只是插入被导入页面的body内容

3.最直观的区别就是动态包含可以增加额外的参数

10. 在JSP页面实现请求转发的三种方法？

解：

1）<%

      RequestDispatcher view = request.getRequestDispatcher("other.jsp");

      view.forward(request, response);

%>

2）<%

          pageContext.forward("other.jsp");

%>

3）`<jsp:forward page="other.jsp" />`

11. JSP的作用域对象有哪些？它们的作用域范围是什么？如何在这些对象上设置和获得属性？

解：

作用域名

对应的对象

存在性和可访问性

应用作用域

application

整个Web应用程序有效

会话作用域

session

一个用户对话范围内有效

请求作用域

request

在用户的请求和转发的请求内有效

页面作用域

pageContext

只在当前的页面内有效

应用作用域：

设置属性：ServletContext context = getServletContext();

              Context.setAttribute(“foo”,one);

获得属性：<% = application.getAttribute(“foo”); %>

会话作用域：

HttpSession session = request.getSession(true);

设置属性：session.setAttribute(“name”,value);

获得属性：session.getAttribute(“name”);

请求作用域：

设置属性：request.setAttribute(“name”,value);

获得属性：request.getAttribute(“name”);

页面作用域：

设置属性：<% pageContext.setAttribute(“name”,value);%>

获得属性：<% pageContext.getAttribute(“name”);%>

12. 什么是JavaBeans？要遵循的规范是什么？

解：

JavaBeans是Java平台的组件技术，在JavaWeb开发中常用JavaBeans来存放数据、封装业务逻辑等，从而很好地实现业务逻辑和表示逻辑的分离，是系统具有更好的健壮性和灵活性。

规范：

（1）JavaBeans应该是public类，并且具有无参数的public构造方法，通过定义不带参数的构造方法或使用默认的构造方法均可满足这个要求。

（2）JavaBeans类的成员变量一般称为属性。对应每个属性访问权限一般定义为private。

（3）每个属性通常定义两个public方法，一个是访问方法（getter），另一个是修改方法（setter）使用它们访问和修改JavaBeans的属性值。

13. 在JSP中如何使用JavaBeans？（<jsp:useBean> <jsp:setProperty> <jsp:getProperty>），这些动作包含哪些属性，代表什么含义？

解：

<jsp:useBean>动作用来在JSP页面中查找或创建一个bean实例。

属性：

id属性用来唯一标识一个bean实例，该属性是必须的。

scope属性指定bean实例的作用域。

class属性指定创建bean实例的Java类。

Type属性指定由id属性声明的变量的类型，由于该变量是在请求时只想实际的bean实例，其类型必须与bean类的类型相同或者是其超类，或者是一个bean类实现的接口。

<jsp:setProperty>动作用来给bean实例的属性赋值。

属性：

name属性用来标识一个bean实例，该实例必须是前面使用<jsp:useBean>动作声明的，并且name属性值必须与<jsp:useBean>动作中指定的一个id属性相同。

property属性指定要设置值的bean实例的属性，容器将根据指定的bean的属性调用适当的setXxx()，因此该属性也是必须的。

value属性为bean的属性指定新值，该属性值可以接受请求时属性表达式。

param属性指定请求参数名，如果请求中包含指定的参数，那么使用该参数值来设置bean的属性值。

Value和param都可选并且不能同时使用。

<jsp:getProperty>动作检索并向输出流中打印bean的属性值。

属性：

name属性指定bean实例名，property属性指定要输出的属性名。

14. MVC设计模型中控制器是什么？模型是什么？视图是什么？MVC设计模型的优点？

解：

Servlet实现控制器功能，它从请求中读取请求信息、创建JavaBeans对象、执行业务逻辑、访问数据库等，最后将请求转发到视图组件。

JavaBeans实现模型功能，用于存放数据。

JSP页面实现视图功能。

最大优点是将业务逻辑和数据访问从表示层中分离出来。提高系统的灵活性和复用性。提高开发效率。

15. 实现MVC模式的一般步骤是什么？

解：

（1）定义JavaBeans表示数据

（2）使用Servlet处理请求

（3）填写JavaBeans对象数据

（4）结果的存储

（5）转发请求到JSP页面

（6）从JavaBeans对象中提取数据

# 第4章

1. 什么是会话？

解：

会话是一个客户与服务器之间的不间断的请求响应序列

2. 如何创建HttpSession对象？掌握HttpSession对象定义的getSession（）方法和setAttribute()，getAttribute()方法。

解：

创建HttpSession对象需要使用HttpServletRequest接口提供的getSession（）该方法有两种格式：

(1)public Httpsession getsession(boolean create)返回或创建与当前请求关联的会话对象。如果没有与当前请求关联的会话对象，当参数为true时创建一个新的会话对象，当参数就为false时返回null.

(2) public Httpsession getsession()该方法与调用getsession(true)等价。

3. 关闭浏览器是否就结束了会话？为何浏览器关闭后再发请求，服务器不再识别用户？

解：

让Session结束生命周期，有以下两种办法：

一个是Session.invalidate()方法，不过这个方法在实际的开发中，并不推荐，可能在强制注销用户的时候会使用；

一个是当前用户和服务器的交互时间超过默认时间后，Session会失效

当把浏览器关闭时，浏览器并没有向服务器发送

任何请求来关闭Session，自然Session也不会被销毁

之前的Session一直都在服务器端，而当我们关闭浏览器时，此时的Cookie是存在

于浏览器的进程中的，当浏览器关闭时，Cookie也就不存在了。

4. 如何让会话失效（2个方法）? invalidate()和在DD文件中设置会话超时时间。

解：

可以在DD文件中设置会话超时时间。

<  session-config >

< session-timeout > 10 </session-timeout >

< /session-config >

5. 什么是Cookie？如何构造Cookie对象？如何向客户端发送Cookie ？如何从客户端读取Cookie？

解：

Cookie是客户访问Web服务器时，服务器在客户硬盘上存放的信息。

调用Cookie类的构造方法可以创建Cookie对象  

Cookie userCookie=new Cookie(“username”,”hacker”);

发送Cookie对象需要调用响应对象的addCookie（）将Cookie添加到Set-Cookie响应头：

Response.addCookie(userCookie);

读取Cookie：

①调用请求对象的getCookie方法，该方法返回一个Cookie对象的数组，如果请求中不含Cookie，返回null值。  Cookie[]cookie=request.getCookie();

②对Cookie数组循环：有了Cookie对象数组后，就可以通过循环访问它的每个元素，然后调用每个Cookie的getName(),直到找到一个与希望的名称相同的对象为止。找到所需要的Cookie对象后，一般要调用它的getValue()，并根据得到的值做进一步处理

6. 上传文件页面表单域有什么特殊要求？如何上传文件？如何从Part对象中检索上传文件的文件名？

解：客户端需要使用form表单，method设为post，enctype默认为application/x-www-form-urlencoded，这里改为multipart/form-data，把input标签的type属性设为file。

用户选择文件提交表单后，服务器端就可以通过JSP的内置对象request（实际上是HttpServletRequest的实例）的输入流获取用户表单内容。需要注意的是此输入流不仅包含了用户上传的文件，还包含了表单的其他字段信息，我们可以把此输入流存为临时文件，然后从临时文件中提取用户真正上传的文件。

7. 文件下载需要完成哪些操作？如何下载文件？

解：在服务器端把文件转换成输出流，写入到response，以response把文件带到浏览器，由浏览器来提示用户是否愿意保存文件到本地

# 第5章

1. 什么是JDBC？JDBC的基本功能是什么？

解：

JDBC是Java程序发访问数据库的标准，由一组Java语言编写的类和接口组成，这些类和接口称为JDBC API，它为Java程序提供一种通用的数据访问接口。

基本功能包括：建立与数据库的连接、发送SQL语句、处理数据库操作结果。

2. 语句对象有哪两种？有什么区别？（Statement对象，PreparedStatement对象），语句对象常用的方法有哪些？

解：

Statemetent对象执行的是静态SQL语句,而PreparedStatement对象执行的是预编译SQL语句

3. 结果集是什么？如何获得结果集？结果集常用方法有哪些？

解：

表示SELECT语句查询得到的记录结合。

可滚动的结果集指在结果集对象上可以前后移动指针访问结果集中的记录。

可更新的结果集指直接通过结果集对象更新数据库表中数据。

4. 传统的数据库建立连接的步骤？该方法的缺点（建立连接比较耗费时间，导致增大请求的响应时间）

解：

传统数据库连接的一般步骤是：

１加载JDBC驱动程序

２建立连接对象

３创建语句对象

４执行SQL语句得到结果集对象，调用ResultSet的有关方法就可以完成对数据库的操作

5关闭建立的各种对象

缺点是每次访问数据库都要建立连接对象，请求结束需关闭连接对象。这将耗费大量的时间，可能导致增大请求的响应时间。

5. 使用数据源连接数据库的优点? 通过数据源对象如何获得连接对象？

解：

使用数据源对象连接数据库，应用程序在启动时只需创建少量的连接对象即可。这样就不需要为每个HTTP请求都创建一个连接对象，这会大大降低请求的响应时间。

采用Java命名与目录接口 （Java Naming and Directory Interface，JNDI）技术来获得DataSource对象的引用。首先为要创建的对象指定一个唯一的名字，然后由对象工厂创建对象，并将该对象与唯一的名字绑定，外部程序可以通过名字来获得某个对象的访问。

6. 什么是DAO?使用它有什么优点?如何设计和使用DAO类？

解：

DAO(Data Access Object) 数据访问对象是一个面向对象的数据库接口，它显露了 Microsoft Jet 数据库引擎（由 Microsoft Access 所使用），并允许 Visual Basic 开发者通过 ODBC 像直接连接到其他数据库一样，直接连接到 Access 表。

优点：使用DAO技术可以使我们方便的访问Microsoft Jet引擎数据库

1.隔离了数据访问代码和业务逻辑代码

2.隔离了不同数据库实现

一个典型的Dao模式有一下几部分组成：

1.dao接口：把对数据库的所有操作定义成抽象方法，可以实现多种实现

2.Dao实现类：针对不同数据库给出Dao接口定义方法的具体实现

# 第6章

1. 如何调用表达式语言？

解：

${expression}

2. 使用EL表达式如何访问作用域变量？

解：

${userName}

3. 用EL表达式如何访问JavaBeans和集合对象？

解：

${name.class}

4. EL的隐含变量的使用？

解：

例如访问Accept请求头，可使用header隐含变量

${header.Accept}或${header[“Accept”]}

5. 在EL中都可以访问哪些类型的数据？

解：

某个web域中的对象，访问javabean的属性、访问list,map集合、访问数组