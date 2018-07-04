# J2EE开发实训

//一个本科咸鱼的课余生活

myclips 使用  将网页的有关信息放入webroot  将引入包比如jdbc驱动放入lib  xml可以作为一个小型数据库（好处在于跨语言），另外主要作为配置信息

1.java笔试i++(++i）//自增自减

2.finall 需要出现在数据库连接这种即使操作未完成也需要关闭

3.单例模式懒汉或饿汉式
      单例模式：应用该模式的类，一个类只有一个实例。
      懒汉式：在你需要的时候才去创建这个对象
	public class Study{
		private static Study student;	
		private Study(){};//外界不能创建对象，所以将构造方法私有
		public static Study getstudent(){
			if(student == null){
				student = new Study();
			}
			return student;
		}
	}

      饿汉式：不管需不需要，一开始就创建对象
	public class Study{
		private static final Study student = new Study();
		private Study(){};
		public static Study getstudent(){
			return student;
		}
	} 

4.冒泡排序

	void bubble_sort(int a[],int len){
		int t;
		for( int i = 0; i < len - 1; ++i)
			for(int j = 0; j<len-1-i;++j)
				if(a[i] < a[j]){
					t = a[i];
					a[i] = a[j];
					a[j] = t;}
	}

5.css（调整显示样式）
	a.有多条声明时，用“；”隔开
	b.样式的三种写法
		α. <p style="font-size:32;font-family:宋体">你好</p>（不建议）
		β.在<head></head>里面，<title></title>后面
		   #p02（"#"为id选择器）{color:red;width:30px;height:50px;}
		γ.外部引入css  <link href="*.css" type="text/css" rel="stylesheet">//rel 表示的是是否从外部引入
 	c.选择器
		* 通配符选择器  表示所有
		body 元素选择器  表示选择所有的body标签，统一样式
		.list  类选择器  引用了此类名（class="list"）的标签，统一样式
		#li id选择器   (id="li") 
		.list li 后代选择器  在引用了list这个类的标签下面的li标签的样式被选择
                                .list>li  子元素选择器
		.list+li  紧邻兄弟选择器
		.list-li   不紧邻兄弟选择器
		h1,h2,h3 分组选择器
		[background]  属性选择器  当前页面所有包含backgrond属性的标签
	d.缩进  p{text-indent:5em;}
	e.链接的样式 
		a:link 未被访问的
	f.边框  border
	g.盒子模型 从外到内依次为 margin（外边距） border（边框）padding（内边距） element（内容）
	h.相对位置：相对父元素进行定位
	   绝对定位：整个网页布局的定位

6.JavaScript
	需要用<script></script>标签去声明这是脚本
	a.三种写法
	      α.<input type="button" onClick="alert('hello world')" value="say")
	      β.<script type="text/javascript"> function say(){alert('hello world');} </script>
	         <input type="button" onClick="say()" value="say")
	      γ.<input type = "button" id="btn03" value="say">
	        window.onload=function(){//不等页面加载完才进行解析
	         var btn03=document.getElementById("btn03");//由于页面是自上往下进行的，所以需要将函数用window.onload包括起来
	          btn03.onClick = function(){alert('hello world');}}
	b.很多的事件  eg:onclick onblur onfocus onchange	

7.jQuery(兼容多浏览器、轻量级的JavaScript库)
	从外部引入 <script type="text/javascript" src="jquery-1.7.2.js></script>//引入之后需要再开一个<script>标签写函数
	a.window.onload 用$符号代替即window.onload=function(){}  =  $(function(){})
	b.document.getElementById("btn01").onclick=function(){} = $("#btn01").click(function(){})
	$是jQuery的核心函数
	c.$("选择器")  直接根据选择器查找元素  
	d.$("html字符串") 根据html关键字查找元素
	e.$("DOM对象")
	g. 动态绑定事件用live ，用以给新添加的元素也能实现函数功能 eg:$(".del").live(function=(){})

8. <table></table> 标签  <thead> 表示表头 <tr> 行  <tbody> 表内容 <td> 列

9.Tomcat  （针对java的web服务器，解析servlet、jsp）将自己的项目放入webapps 然后通过localhost:8080/（自己的项目）.html访问

10.Severlet  ？？？
	a.创建一个类来实现Serverlet接口
	b.生命周期
		init()初始化方法
		service() 处理请求方法
		destroy() 销毁方法

		容器
	c.ServletContext  获取web初始化参数
	d.转发和重定向 转发执行了一次请求，重定向执行了两次请求 转发地址栏显示的是最初访问的目录
	   重定向是最终页面的目录  
	e.@WebServlet("/user") 在servelet类中 注释这个类是要用来干嘛、并指明外部访问路径
	   要让网页与WebServlet连接起来，需要在表单注明方法和访问方法<form action="login" method="post"></form>
	   表示网页将使用login这个类，并使用post的方法
	f.get:系统默认的提交方式为get   在地址栏直接输入是get   get会将参数直接表示在地址栏中 参数小于1kb
	  post:
11.JSP 
	a.<% String unname="zhangsan";%> java代码 <%=unname%>  展示java内容  <%! public int add(int a,int b){return a+b;}%>  <%=add(2+3)%>声明java
	   <%--注释信息 --%>
	b.九大隐式对象
		request（客户端请求)、response(服务器响应)、out、session、application、pageContext、page、config、exception
	c.四个作用域
		pageContext 当前页面  request 当前请求(包含转发)  session 当前会话(一个浏览器与服务器) application 整个应用
	d.JSP指令
		<%@page ... %> 定义网页属性  <%@include ...%> 包含文件  <%@taglib ... %> 引入标签库的定义
	e.session与cookie会话跟踪
		