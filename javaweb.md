# JavaWeb

## 注意事项：

**要用tomcat8不能用10，要不然很多地方会报错，要引入tomcat文件里的servlet的jar包，继承HttpServlet要选javax**



## 一、简介

页面由三部分组成！分别由内容(结构)、表现、行为

1、内容一般用html技术实现

2、表现和布局一般用css实现







## 二、HTML

### 1、简介

通过标签来控制页面<>

### 2、创建

创建一个工程，然后模块，然后html文件.

### 3、主体结构

```html
<!DOCTYPE html>        
<html lang="en">     <!-- 页面的开始 -->
<head>               <!-- 头信息>
    <meta charset="UTF-8">    <!-- utf-8编码集 -->
    <title>Title</title>      <!-- 页面标题-->
</head>
<body>                      <!-- body是主体内容 -->
                       
</body>
</html>
```

<!--这是html的注释  -->

bgcolor是背景颜色

onclick是单机事件

alert()是警告框

比如<body onclick="alert('你好')"></body>   body标签是整个页面显示的内容

<button onclick="alert('nihao')"></button>按钮,在页面点击会出现你好



### 4、书写规则

双标签<p></p>        单标签,(换行)<br/>  水平线<hr/>

标签不能嵌套，比如<div><span>Nihao</div></span>     这是明显错误的       

标签要及时关闭</xxx>

标签里的属性值要加引号，比如：<font color="bule"></font>

注释不能嵌套



### 5、font标签

(修改文本的相关属性)里面可以选择color(字体颜色)、face(字体样式，比如宋体什么的)、size(字体大小)



### 6、align

对其属性,比如align="left"  向左边对齐



### **7、a标签**(生成链接)

```html
<!--生成链接-->
<a href="https://leetcode.cn/submissions/detail/330185528/">百度</a><br/>
<a href="https://leetcode.cn/submissions/detail/330185528/" target="_self">百度_self</a><br/>
<a href="https://leetcode.cn/submissions/detail/330185528/" target="_blank">百度_black</a> <br/>
```

   a标签可以生成链接，target="_black"可以打开新窗口实现链接



### 8、排序标签ul

```html
<ul type="name">
    <li>梅西</li>
    <li>C罗</li>
    <li>内马尔</li>
    <li>小罗</li>
</ul>
```

可以对内容进行排序



### 9、img标签

```html
<img src="./image_2022-04-28_18-58-36.png" width="200" height="100"/><br>
```

在页面上展示图片,src是路径

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20220704221113.jpg)



### 10、table(表格标签)

```html
 <!--表格-->
<table border="1" width="300" height="300" >
    <tr>
        <th>1.1</th>
        <th>1.2</th>
        <th>1.3</th>
    </tr>
    <tr>
        <th>2.1</th>
        <th>2.2</th>
        <th>2.3</th>
    </tr>
    <tr>
        <th>3.1</th>
        <th>3.2</th>
        <th>3.3</th>
    </tr>
</table>
```

tr表示行

th是表头标签，已经修饰好的

border设置边框粗细

width表格宽度

height表格高度

align是设置表格相对于页面的对齐方式

cellspacing设置单元格间距

td是单元格标签

th=<td align="center"><b></b></td>

<b>是加粗标签



### 11、iframe标签

```html
 <iframe src="web11.1.html" width="500" height="500" name="abc"></iframe>
<br/>
<ul>
    <li><a href="列表.html" target="abc">列表</a></li>
    <li><a href="web11.1.html" target="abc">web11</a></li>
</ul>
```

可以在页面单独开一个款，款的内容取决于src

同时配合a标签,通过name和target联系，使得a标签在框框内跳转



### **12、form表单标签**

普通版：

```html
<form>
    用户名称:<input type="text" value="年后"><br>
    用户密码:<input type="password" maxlength="10"><br>
    确认密码:<input type="password" maxlength="10"><br>
    性别：<input type="radio" name="sex" checked="checked">男  <input type="radio" name="sex">女<br>
    兴趣爱好<input type="checkbox">java
    兴趣爱好<input type="checkbox">c++
    兴趣爱好<input type="checkbox">python<br>
    国籍:<select>
        <option>请选择国籍</option>
        <option>美国</option>
        <option>中国</option>
        <option>日本</option>
       </select><br>
     自我评价:<textarea rows="10" cols="20"></textarea><br>
     <input type="reset"><br>
     <input type="submit"><br>
     <input type="button" value="abc"><br>
     <input type="hidden" value="11">
    <input type="file">
</form>
```

用input type="xxxx"

input :

type="text"  文件输入框，value为默认显示内容

type="password" 密码输入框，value同上

type=radio 单选框 name属性可以对其分组 ，checked="checked"表示默认选中

type=reset是重置按钮，value修改按钮上的信息

type=submit是提交按钮，value同上

type=button是按钮

type=file文件上传按钮

type=hidden是隐藏域

select是下拉标签

option是下拉框的选项

textara多行输入文本框(rows显示几行高度，cols每行可以显示几个字符宽度)

   

### **13、表单提交**

```html
<form action="http://localhost:8000" method="get">
    <!-- action是提交的服务器地址,method是提交的方式 -->
    <input type="hidden" name="action" value="login">
    <h1 align="center">用户注册</h1>
    <!--  h是标题标签,align是让标题居中,table是表格标签是让整体对称然后居中-->
    <table align="center">
         <tr>
             <td>用户名</td>
             <td><input type="text" value="默认值"></td>
         </tr>
        <tr>
            <td>用户密码</td>
            <td><input type="password" maxlength="20"></td>
        </tr>
        <tr>
            <td>确认密码</td>
            <td><input type="password" maxlength="20"></td>
        </tr>
        <tr>
            <td>性别</td>
            <td><input type="radio" name="sex" checked="checked" value="boy">男<input type="radio" name="sex" value="=girl">女</td>
        </tr>
        <tr>
            <td>兴趣爱好:</td>
        </tr>
        <tr>
            <td>
                <input name="hobby" type="checkbox" value="java">java
                <input  name="hobby" type="checkbox" value="cpp">c++
                <input  name="hobby" type="checkbox" value="python">python
            </td>
        </tr>
        <tr>
            <td>国籍</td>
            <td>
                <select name="country">
                    <option>请选择国籍</option>
                    <option>美国</option>
                    <option>中国</option>
                    <option>日本</option>
                </select>
            </td>
        </tr>
        <tr>
            <td>
                <input type="submit" value="提交">
            </td>
        </tr>
    </table>
</form>
```

表单提交没有发给服务器：

1、表单没有name属性

2、单选复选(option)要加value属性

3、表单项不在form标签中



### 14、其他标签

div默认独占一行

span长度是封装数据的长度

p 默认会在锻段落上方或者下方空出一行







## 三、CSS

### 1、和html结合方式一

```html
<div style="text-align:center;border:1px solid red;width:100px; height:100px;background:blue">标签1</div>
```

给每一个标签设置边框等内容

### 2、结合方式二

style标签

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
      div{
         text-align:center;
         border:1px solid red;
         width:100px;
         height:100px;
         background:blue
      }
    </style>
</head>
<body>
      <div> 标签1</div>
      <div>标签2</div>
</body>
</html>
```

在最上面定义style type="xxx"

### 3、方式三

css文件导入

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <link rel="stylesheet" type="text/css" href="css1.css" >
</head>
<body>
    <div>标签1</div>
    <div>标签2</div>
     <span>标签3</span>
</body>
</html>
```

用link标签通过rel，type，以及路径href来导入css文件



### 4、id选择器

通过标签的id来识别css

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
       #id100{
           color: blue;
           font-size: 20px;
           border: 1px yellow solid;
       }
       #id101{
           color: red;
           font-size: 40px;
           border: 5px black dotted;
       }
    </style>
</head>
<body>
     <div id="id100">标签1</div>
     <span id="id101">标签2</span>
</body>
</html>
```



### 5、class选择器

和id选择器一样，通过class名来实现css代码

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
         .class1001{
             color: blue;
         }
    </style>
</head>
<body>
    <div class="class1001">标签1</div>
</body>
</html>
```





### 6、组合选择器

见手机代码



### 7、常见样式

```
color:red;                 字体颜色
border: yellow 1px solid;
width: 300px;
height: 200px;
background-color:         aquamarine;背景颜色
font-size:40px;          字体大小
margin-left: auto;        居中
margin-right: auto;
text-align: center;       文本居中
```







## 四、JavaScript

### 1、alert()

alert()是一个警告框，可以弹出东西来



### 2、在htlm里面写js要用标签script

```js
<script type="text/javascript">
    var i;
    i=12;
    //alert(typeof (i));
    var arr=[1,2,3,4,5]
    arr[20]='ssss'
    alert(arr)
</script>
```





### 3、引入js代码

```js
<script type="text/javascript" src="js1.js"></script>
```





### 4、JS变量简介

数值类型：number(js没有Int这些)

字符串类型：string

对象类型：object

布尔类型：boolean

函数类型：function(函数可以赋给一个对象)



特殊值：

undefined(没有赋初始值)

null

NAN(非数值类型)



### 5、定义变量

var  a或者var a=xxxx

typedef(a)返回类型



### 6、比较运算符

==表面比较

===全部比较

比如12=="12"  true

12==="12"false



### **7、逻辑运算符**

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220704231006.png)

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220704230936.png)



### 8、函数

定义方式：1、function 函数名(){   具体内容  }  **参数不要写类型，返回值没有类型**

​                 2、var 函数名=function(参数){}

js 不能有函数重载，如果两个函数重名了，第二个会覆盖第一个



### 9、定义属性

var a={

属性：值，

属性：值 

}

### 10、js内存结构

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220705135436.png" style="zoom:50%;" />



### 11、JS中的事件(重点）

onload 加载完成事件 window.onload(function())

分为动态和静态

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        function onloadFun(){
            alert("静态注册")
        }
       window.onload=function (){
            alert("动态")
       }
    </script>
</head>
      <!-- 静态注册unlond事件-->
<body onload="onloadFun()">

</body>
</html>
```




onblur失去焦点事件(验证输入内容是否安全)

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //静态注册失去焦点事件
        function onblurFun(){
            //控制台对象,向浏览器的控制器打印输出
            //log是打印的方法
           console.log("静态注册");
        }
        //动态
        window.onload=function (){
            var b=document.getElementById("1001");
            b.onblur=function (){
               console.log("动态")
            }
        }
    </script>
</head>
<body>
     用户名:<input type="text" onblur="onblurFun()"><br/>
     密码:<input type="text" id="1001"><br/>
</body>
</html>
```



onclick单机事件

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
     <script type="text/javascript">
         function onclickFun(){
             alert("静态注册")
         }
         window.onload=function (){
             //获取标签对象
             //document是js提供的一个对象(文档)
             //getElementById通过id属性获取标签对象
            var b= document.getElementById("1001");
             //通过标签对象，事件名=function
             b.onclick=function (){
                 alert("动态")
             }
         }
     </script>
</head>
<body>
    <button onclick="onclickFun()">按钮1</button>
     <button id="1001">按钮2</button>
</body>
</html>
```



onchange

内容改变事件(用于下拉列表和输入框内容发生改变的操作)

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //静态
       function onchangeFun(){
          alert("静态改变")
       }
       //动态
        window.onload=function (){
           var b=document.getElementById("1001");
           b.onchange=function (){
               alert("动态改变")
           }
        }
    </script>
</head>
<body>
      选择一个球星:
      <select onchange="onchangeFun()">
          <option>梅西</option>
          <option>C罗</option>
          <option>内马尔</option>
          <option>小罗</option>
      </select><br/>
       选择一个人:
      <select id="1001">
          <option>梅西</option>
          <option>C罗</option>
          <option>内马尔</option>
          <option>小罗</option>
      </select>
</body>
</html>
```



onsubmit

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //静态注册提交表单
        function onsubmitFun(){
            //要验证表单是否合法，合法才能提交
            alert("不合法");
            return false;
        }
        //动态
        window.onload=function (){
            var b=document.getElementById("1001")
            b.onsubmit=function (){
                alert("动态不合法")
                return false;
            }
        }
    </script>
</head>
<body>
    <!-- return false可以阻止表单提交-->
    <form action="http://localhost:8080" method="get" onsubmit="return onsubmitFun();">
        <input type="submit",value="静态注册">
    </form>
    <form action="http://localhost:8080" method="get" id="1001"">
        <input type="submit",value="动态注册">
    </form>
</body>
</html>
```



### 12、事件注册分类

动态和静态

静态就是 function xxx(){}

**动态：**

**1、获取标签对象**

**2、标签对象.事件名=function()**

 **window.onload=function (){**
            **var b=document.getElementById("1001")   步骤1**
            **b.onsubmit=function (){                             步骤2**
                **alert("动态不合法")**
                **return false;**
            **}**
        **}**



### 13、DOM模型

把文档中的属性，标签，文本转换为对象来管理

1、dom对象管理了所以html文档内容

2、dom对象是一种树结构文档，有层级关系

**3、可以通过dom对象访问标签对象**

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220709011146477.png" alt="image-20220709011146477" style="zoom:50%;" />



### 14、dom对象方法(重要)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220706134053.png" style="zoom: 67%;" />

几个方法都大同小异

都是通过标签的属性获取对象然后再操作

#### 方式一:通过id

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>标题</title>
    <script type="text/javascript">
        //用户点击按钮，输入内容，要验证里面的内容是否合法
         //规则是由字母，数字，下划线组成,并且长度是5到12位
        function  onclickfun(){
            //操作标签，先获取标签对象
            var name=document.getElementById("username");
            //name就是dom对象
            var b=name.value;
            //正则表达式
            var patt=/^\w{5,12}$/;
            //test方法用了测试某个字符串是否符号规则
            var usrname2=document.getElementById("us");
            //alert(usrname2.innerHTML);//表示起始标签和结束标签的内容
            if(patt.test(b)){
               usrname2.innerHTML="用户名合法"
            }else {
                usrname2.innerHTML="用户名不合法"
            }
        }
    </script>
</head>
<body>
    用户名:
    <input type="text" id="username" value="111">
    <span id="us" style="color: red">用户名不合法</span>
    <button onclick="onclickfun()">校验</button>
</body>
</html>
```



#### 方式二：通过name属性

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        //三种方法对应三个状态
         function checkall(){
             //获取一个多个标签对象集合
           var a=document.getElementsByName("hobby");
           for(var i=0;i<a.length;i++){
               a[i].checked=true;
           }
         }
         function checkno(){
             var a=document.getElementsByName("hobby");
             for(var i=0;i<a.length;i++){
                 a[i].checked=false;
             }
         }
         function check(){
             var a=document.getElementsByName("hobby");
             for(var i=0;i<a.length;i++){
                 if(a[i].checked==false)a[i].checked=true;
                 else a[i].checked=false;
             }
         }
    </script>
</head>
<body>
     兴趣爱好：
     <input type="checkbox" name="hobby" value="cpp" checked="checked">CPP
     <input type="checkbox"  name="hobby"  value="java" checked="checked">java
      <input type="checkbox"  name="hobby"  value="go" checked="checked">go
      <br>
      <button onclick="checkall()">全选</button>
      <button onclick="checkno()">全不选</button>
      <button  onclick="check()">反选</button>
</body>
</html>
```



#### 方式三：通过标签名

//获得一个集合，类似数组

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
  <script type="text/javascript">
      //通过标签名来引入
      function checkall(){
          var a=document.getElementsByTagName("input")
          for(var i=0;i<a.length;i++){
              a[i].checked=true;
          }
      }
      function checkno(){
          var a=document.getElementsByTagName("input")
          for(var i=0;i<a.length;i++){
              a[i].checked=false;
          }
      }
      function  check(){
          var a=document.getElementsByTagName("input")
          for(var i=0;i<a.length;i++){
              a[i].checked=!a[i].checked;
          }
      }
  </script>
</head>
<body>
      <input type="checkbox"  value="cpp" checked="checked">CPP
      <input type="checkbox"   value="java" checked="checked">java
      <input type="checkbox"   value="go" checked="checked">go
      <br>
      <button onclick="checkall()">全选</button>
      <button onclick="checkno()">全不选</button>
      <button onclick="check()">复选</button>
</body>
</html>
```



#### 四、创建标签对象

```html
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        window.onload=function () {
            var objdiv = document.createElement("div");
            objdiv.innerHTML = "年后";
            document.body.appendChild(objdiv);
        }
    </script>
</head>
<body>

</body>
</html>
```



#### 五、innerHTML

在标签中插入文字



### **15、结点的常用属性和方法**

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220706134529.png" style="zoom:50%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220706134541.png" style="zoom: 67%;" />



## **五、JQuery**

### 1、简介

//引入jquery文件

$(function())来完成加载

```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>

<script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
<script type="text/javascript">

   //使用$()代替window.onload
   $(function(){
      //使用选择器获取按钮对象，随后绑定单击响应函数
      $("#btnId").click(function(){
         //弹出Hello
         alert('Hello');
      });
   });

</script>


</head>
<body>

   <button id="btnId">SayHello</button>

</body>
</html>
```

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220706233247.png" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220706233307.png" style="zoom:67%;" />

jquery是dom对象的数组

可以互相转换

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220706233725.png" style="zoom:67%;" />



### 2、转换

dom->jquery   var￥a=&(dom对象）

var dom=&obj[下标]



### 3、选择器(重点）

#### 1、基本选择器

#id    .class  element(标签名)  *(所有元素)  

基本一样的，见代码

这里的点击是click和dom不一样,dom是要xxx.onclick=fuction(){}

```HTML
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <style type="text/css">
         div, span, p {
             width: 140px;
             height: 140px;
             margin: 5px;
             background: #aaa;
             border: #000 1px solid;
             float: left;
             font-size: 17px;
             font-family: Verdana;
         }
         
         div.mini {
             width: 55px;
             height: 55px;
             background-color: #aaa;
             font-size: 12px;
         }
         
         div.hide {
             display: none;
         }
      </style>
      <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">

            //1.选择 id 为 one 的元素 "background-color","#bbffaa"
             $(function () {
                $("#btn1").click(function () {
                   //css设置和获取样式
                   alert($("#one").css("background-color", "red"));
                })

                //2.选择 class 为 mini 的所有元素
                $("#btn2").click(function (){
                   $(".mini").css("background-color","yellow")
                })
                //3.选择 元素名是 div 的所有元素
                $("#btn3").click(function (){
                   $("div").css("background-color","green")
                })
                //4.选择所有的元素
                $("#btn4").click(function (){
                   $("*").css("background-color","green")
                })
                //5.选择所有的 span 元素和id为two的元素
                     $("#btn5").click(function (){
                   $("span,#two").css("background-color","red")
                })
             })
   
         
      </script>
   </head>
   <body>
<!--   <div>
      <h1>基本选择器</h1>
   </div>  -->   
      <input type="button" value="选择 id 为 one 的元素" id="btn1" />
      <input type="button" value="选择 class 为 mini 的所有元素" id="btn2" />
      <input type="button" value="选择 元素名是 div 的所有元素" id="btn3" />
      <input type="button" value="选择 所有的元素" id="btn4" />
      <input type="button" value="选择 所有的 span 元素和id为two的元素" id="btn5" />
      
      <br>
      <div class="one" id="one">
         id 为 one,class 为 one 的div
         <div class="mini">class为mini</div>
      </div>
      <div class="one" id="two" title="test">
         id为two,class为one,title为test的div
         <div class="mini" title="other">class为mini,title为other</div>
         <div class="mini" title="test">class为mini,title为test</div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini"></div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini" title="tesst">class为mini,title为tesst</div>
      </div>
      <div style="display:none;" class="none">style的display为"none"的div</div>
      <div class="hide">class为"hide"的div</div>
      <div>
         包含input的type为"hidden"的div<input type="hidden" size="8">
      </div>
      <span class="one" id="span">^^span元素^^</span>
   </body>
</html>
```



#### 2、层级选择器

ancestor descendant 后代选择器

parent>chid 子元素选择器

prev+next(相邻元素)

prev~siblings  之后的兄弟选择器

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <style type="text/css">
         div, span, p {
             width: 140px;
             height: 140px;
             margin: 5px;
             background: #aaa;
             border: #000 1px solid;
             float: left;
             font-size: 17px;
             font-family: Verdana;
         }
         
         div.mini {
             width: 55px;
             height: 55px;
             background-color: #aaa;
             font-size: 12px;
         }
         
         div.hide {
             display: none;
         }        
      </style>
      <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">
         $(document).ready(function(){
            //1.选择 body 内的所有 div 元素 
            $("#btn1").click(function(){
               $("body div").css("background", "#bbffaa");
            });

            //2.在 body 内, 选择div子元素  
            $("#btn2").click(function(){
               $("body>div").css("background", "#bbffaa");
            });

            //3.选择 id 为 one 的下一个 div 元素 
            $("#btn3").click(function(){
               $("#one+div").css("background", "#bbffaa");
            });

            //4.选择 id 为 two 的元素后面的所有 div 兄弟元素
            $("#btn4").click(function(){
               $("#two~div").css("background", "#bbffaa");
            });
         });
      </script>
   </head>
   <body> 
   
<!--   <div>
      <h1>层级选择器:根据元素的层级关系选择元素</h1>
      ancestor descendant  ：
      parent > child           ：
      prev + next          ：
      prev ~ siblings       ：
   </div>  -->
      <input type="button" value="选择 body 内的所有 div 元素" id="btn1" />
      <input type="button" value="在 body 内, 选择div子元素" id="btn2" />
      <input type="button" value="选择 id 为 one 的下一个 div 元素" id="btn3" />
      <input type="button" value="选择 id 为 two 的元素后面的所有 div 兄弟元素" id="btn4" />
      <br><br>
      <div class="one" id="one">
         id 为 one,class 为 one 的div
         <div class="mini">class为mini</div>
      </div>
      <div class="one" id="two" title="test">
         id为two,class为one,title为test的div
         <div class="mini" title="other">class为mini,title为other</div>
         <div class="mini" title="test">class为mini,title为test</div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini"></div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini" title="tesst">class为mini,title为tesst</div>
      </div>
      <div style="display:none;" class="none">style的display为"none"的div</div>
      <div class="hide">class为"hide"的div</div>
      <div>
         包含input的type为"hidden"的div<input type="hidden" size="8">
      </div>
      <span id="span">^^span元素^^</span>
   </body>
</html>
```



#### **3、基本过滤器**(重要且难记)

**:first获取第一个** 

**:last 最后一个**

**:not(selecor)去除与给定选择器匹配的元素**

**:even     匹配索引值为偶数元素，从0开始    ：odd**

**：eq(index)     匹配一个给定索引值的元素**

**:gt(index)  所有索引大于index元素**

**:it(index)小于index**

**:header   匹配如：h1,h2,h3之类的标题元素**

**:animated   匹配正在执行的动画元素**

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <style type="text/css">
         div, span, p {
             width: 140px;
             height: 140px;
             margin: 5px;
             background: #aaa;
             border: #000 1px solid;
             float: left;
             font-size: 17px;
             font-family: Verdana;
         }
         
         div.mini {
             width: 55px;
             height: 55px;
             background-color: #aaa;
             font-size: 12px;
         }
         
         div.hide {
             display: none;
         }        
      </style>
      <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">
         $(document).ready(function(){
            function anmateIt(){
               $("#mover").slideToggle("slow", anmateIt);
            }
            anmateIt();
         });
         
         $(document).ready(function(){
            //1.选择第一个 div 元素  
            $("#btn1").click(function(){
               $("div:first").css("background", "#bbffaa");
            });

            //2.选择最后一个 div 元素
            $("#btn2").click(function(){
               $("div:last").css("background", "#bbffaa");
            });

            //3.选择class不为 one 的所有 div 元素
            $("#btn3").click(function(){
               $("div:not(.one)").css("background", "#bbffaa");
            });

            //4.选择索引值为偶数的 div 元素
            $("#btn4").click(function(){
               $("div:even").css("background", "#bbffaa");
            });

            //5.选择索引值为奇数的 div 元素
            $("#btn5").click(function(){
               $("div:odd").css("background", "#bbffaa");
            });

            //6.选择索引值为大于 3 的 div 元素
            $("#btn6").click(function(){
               $("div:gt(3)").css("background", "#bbffaa");
            });

            //7.选择索引值为等于 3 的 div 元素
            $("#btn7").click(function(){
               $("div:eq(3)").css("background", "#bbffaa");
            });

            //8.选择索引值为小于 3 的 div 元素
            $("#btn8").click(function(){
               $("div:lt(3)").css("background", "#bbffaa");
            });

            //9.选择所有的标题元素
            $("#btn9").click(function(){
               $(":header").css("background", "#bbffaa");
            });

            //10.选择当前正在执行动画的所有元素
            $("#btn10").click(function(){
               $(":animated").css("background", "#bbffaa");
            });
            //选择没有执行动画最后一个div
            $("#btn11").click(function (){
               $("div:not(:animated):last").css("background", "#bbffaa");
            })
         });
      </script>
   </head>
   <body>    
<!--   <div>
   :first           
   :last        
   :not(selector)     
   :even        
   :odd         
   :eq(index)     
   :gt(index)        
   :lt(index)        
   :header       
   :animated     
   </div> -->
      <input type="button" value="选择第一个 div 元素" id="btn1" />
      <input type="button" value="选择最后一个 div 元素" id="btn2" />
      <input type="button" value="选择class不为 one 的所有 div 元素" id="btn3" />
      <input type="button" value="选择索引值为偶数的 div 元素" id="btn4" />
      <input type="button" value="选择索引值为奇数的 div 元素" id="btn5" />
      <input type="button" value="选择索引值为大于 3 的 div 元素" id="btn6" />
      <input type="button" value="选择索引值为等于 3 的 div 元素" id="btn7" />
      <input type="button" value="选择索引值为小于 3 的 div 元素" id="btn8" />
      <input type="button" value="选择所有的标题元素" id="btn9" />
      <input type="button" value="选择当前正在执行动画的所有元素" id="btn10" />    
      <input type="button" value="选择没有执行动画的最后一个div" id="btn11" />
      
      <h3>基本选择器.</h3>
      <br><br>
      <div class="one" id="one">
         id 为 one,class 为 one 的div
         <div class="mini">class为mini</div>
      </div>
      <div class="one" id="two" title="test">
         id为two,class为one,title为test的div
         <div class="mini" title="other">class为mini,title为other</div>
         <div class="mini" title="test">class为mini,title为test</div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini"></div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini" title="tesst">class为mini,title为tesst</div>
      </div>
      <div style="display:none;" class="none">style的display为"none"的div</div>
      <div class="hide">class为"hide"的div</div>
      <div>
         包含input的type为"hidden"的div<input type="hidden" size="8">
      </div>
      <div id="mover">正在执行动画的div元素.</div>
   </body>
</html>
```



#### 4、内容过滤器

：contains(text)包含的内容

：empty匹配所有不包含子元素或者文本的空元素

:parent 匹配含有子元素或者文本的元素

:has(selector)匹配含有选择器所匹配的元素的元素

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <style type="text/css">
         div, span, p {
             width: 140px;
             height: 140px;
             margin: 5px;
             background: #aaa;
             border: #000 1px solid;
             float: left;
             font-size: 17px;
             font-family: Verdana;
         }
         
         div.mini {
             width: 55px;
             height: 55px;
             background-color: #aaa;
             font-size: 12px;
         }
         
         div.hide {
             display: none;
         }        
      </style>
      <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">
         $(document).ready(function(){
            function anmateIt(){
               $("#mover").slideToggle("slow", anmateIt);
            }
   
            anmateIt();             
         });
         
         /** 
         :contains(text)   
         :empty             
         :has(selector)     
         :parent          
         */
         $(document).ready(function(){
            //1.选择 含有文本 'di' 的 div 元素
            $("#btn1").click(function(){
               $("div:contains('di')").css("background", "#bbffaa");
            });

            //2.选择不包含子元素(或者文本元素) 的 div 空元素
            $("#btn2").click(function(){
               $("div:empty").css("background", "#bbffaa");
            });

            //3.选择含有 class 为 mini 元素的 div 元素
            $("#btn3").click(function(){
               $("div:has(.mini)").css("background", "#bbffaa");
            });

            //4.选择含有子元素(或者文本元素)的div元素
            $("#btn4").click(function(){
               $("div:parent").css("background", "#bbffaa");
            });
         });
      </script>
   </head>
   <body>    
      <input type="button" value="选择 含有文本 'di' 的 div 元素" id="btn1" />
      <input type="button" value="选择不包含子元素(或者文本元素) 的 div 空元素" id="btn2" />
      <input type="button" value="选择含有 class 为 mini 元素的 div 元素" id="btn3" />
      <input type="button" value="选择含有子元素(或者文本元素)的div元素" id="btn4" />
      
      <br><br>
      <div class="one" id="one">
         id 为 one,class 为 one 的div
         <div class="mini">class为mini</div>
      </div>
      <div class="one" id="two" title="test">
         id为two,class为one,title为test的div
         <div class="mini" title="other">class为mini,title为other</div>
         <div class="mini" title="test">class为mini,title为test</div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini"></div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini" title="tesst">class为mini,title为tesst</div>
      </div>
      <div style="display:none;" class="none">style的display为"none"的div</div>
      <div class="hide">class为"hide"的div</div>
      <div>
         包含input的type为"hidden"的div<input type="hidden" size="8">
      </div>
      <div id="mover">正在执行动画的div元素.</div>
   </body>
</html>
```



#### 5、属性过滤器

[attribute]匹配包含给定属性的元素

[attribute=value] 匹配给定属性是某个值的元素

[attribute!=value]不含有或者不等于

[a$=value]匹配给定的属性是以某些值结尾的元素

[a*=value]包含某些值的元素

[][]//[][]...复核过滤器

```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Untitled Document</title>
<style type="text/css">
div,span,p {
   width: 140px;
   height: 140px;
   margin: 5px;
   background: #aaa;
   border: #000 1px solid;
   float: left;
   font-size: 17px;
   font-family: Verdana;
}

div.mini {
   width: 55px;
   height: 55px;
   background-color: #aaa;
   font-size: 12px;
}

div.hide {
   display: none;
}
</style>
<script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
<script type="text/javascript">
   /**
[attribute]          
[attribute=value]     
[attribute!=value]         
[attribute^=value]        
[attribute$=value]        
[attribute*=value]        
[attrSel1][attrSel2][attrSelN]  
   
   
   */
   $(function() {
      //1.选取含有 属性title 的div元素
      $("#btn1").click(function() {
         $("div[title]").css("background", "#bbffaa");
      });
      //2.选取 属性title值等于'test'的div元素
      $("#btn2").click(function() {
         $("div[title='test']").css("background", "#bbffaa");
      });
      //3.选取 属性title值不等于'test'的div元素(*没有属性title的也将被选中)
      $("#btn3").click(function() {
         $("div[title!='test']").css("background", "#bbffaa");
      });
      //4.选取 属性title值 以'te'开始 的div元素
      $("#btn4").click(function() {
         $("div[title^='te']").css("background", "#bbffaa");
      });
      //5.选取 属性title值 以'est'结束 的div元素
      $("#btn5").click(function() {
         $("div[title$='est']").css("background", "#bbffaa");
      });
      //6.选取 属性title值 含有'es'的div元素
      $("#btn6").click(function() {
         $("div[title*='es']").css("background", "#bbffaa");
      });
      
      //7.首先选取有属性id的div元素，然后在结果中 选取属性title值 含有'es'的 div 元素
      $("#btn7").click(function() {
         $("div[id][title*='es']").css("background", "#bbffaa");
      });
      //8.选取 含有 title 属性值, 且title 属性值不等于 test 的 div 元素
      $("#btn8").click(function() {
         $("div[title][title!='test']").css("background", "#bbffaa");
      });
   });
</script>
</head>
<body>
   <input type="button" value="选取含有 属性title 的div元素." id="btn1" />
   <input type="button" value="选取 属性title值等于'test'的div元素." id="btn2" />
   <input type="button"
      value="选取 属性title值不等于'test'的div元素(没有属性title的也将被选中)." id="btn3" />
   <input type="button" value="选取 属性title值 以'te'开始 的div元素." id="btn4" />
   <input type="button" value="选取 属性title值 以'est'结束 的div元素." id="btn5" />
   <input type="button" value="选取 属性title值 含有'es'的div元素." id="btn6" />
   <input type="button"
      value="组合属性选择器,首先选取有属性id的div元素，然后在结果中 选取属性title值 含有'es'的 div 元素."
      id="btn7" />
   <input type="button"
      value="选取 含有 title 属性值, 且title 属性值不等于 test 的 div 元素." id="btn8" />

   <br>
   <br>
   <div class="one" id="one">
      id 为 one,class 为 one 的div
      <div class="mini">class为mini</div>
   </div>
   <div class="one" id="two" title="test">
      id为two,class为one,title为test的div
      <div class="mini" title="other">class为mini,title为other</div>
      <div class="mini" title="test">class为mini,title为test</div>
   </div>
   <div class="one">
      <div class="mini">class为mini</div>
      <div class="mini">class为mini</div>
      <div class="mini">class为mini</div>
      <div class="mini"></div>
   </div>
   <div class="one">
      <div class="mini">class为mini</div>
      <div class="mini">class为mini</div>
      <div class="mini">class为mini</div>
      <div class="mini" title="tesst">class为mini,title为tesst</div>
   </div>
   <div style="display: none;" class="none">style的display为"none"的div</div>
   <div class="hide">class为"hide"的div</div>
   <div>
      包含input的type为"hidden"的div<input type="hidden" value="123456789"
         size="8">
   </div>
   <div id="mover">正在执行动画的div元素.</div>
</body>
</html>
```



#### 6、表单过滤器

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220709113751823.png" alt="image-20220709113751823" style="zoom:50%;" />

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">
         $(function(){
            
            
      /**
      :input        
      :text     
      :password  
      :radio        
      :checkbox  
      :submit    
      :image        
      :reset        
      :button    
      :file     
      :hidden    
      
      表单对象的属性
      :enabled      
      :disabled     
      :checked      
      :selected     
      */
               
               
            //1.对表单内 可用input 赋值操作
            $("#btn1").click(function(){
               //val方法可以操作表单项的value
               $(":text:enabled").val("加油")
            });
            //2.对表单内 不可用input 赋值操作
            $("#btn2").click(function(){
               $(":text:disabled").val("修改成功");
            });
            //3.获取多选框选中的个数  使用size()方法获取选取到的元素集合的元素个数
            $("#btn3").click(function(){
               alert($(":checkbox:checked").length)
            });
            //4.获取多选框，每个选中的value值
            $("#btn4").click(function(){
               var chekboxies=$(":checkbox:checked")
               //for(var i=0;i<chekboxies.length;i++){
                  //alert(chekboxies[i].value)
               //}
               chekboxies.each(function (){
                  alert(this.value)
               })
            });
            //5.获取下拉框选中的内容  
            $("#btn5").click(function(){
               //获取选中的option对象
               var a=$("select option:selected")
               a.each(function (){
                  alert(this.value)
               })
            });
         }) 
      </script>
   </head>
   <body>
      <h3>表单对象属性过滤选择器</h3>
       <button id="btn1">对表单内 可用input 赋值操作.</button>
       <button id="btn2">对表单内 不可用input 赋值操作.</button><br /><br />
       <button id="btn3">获取多选框选中的个数.</button>
       <button id="btn4">获取多选框选中的内容.</button><br /><br />
         <button id="btn5">获取下拉框选中的内容.</button><br /><br />
       
      <form id="form1" action="#">         
         可用元素: <input name="add" value="可用文本框1"/><br>
         不可用元素: <input name="email" disabled="disabled" value="不可用文本框"/><br>
         可用元素: <input name="che" value="可用文本框2"/><br>
         不可用元素: <input name="name" disabled="disabled" value="不可用文本框"/><br>
         <br>
         
         多选框: <br>
         <input type="checkbox" name="newsletter" checked="checked" value="test1" />test1
         <input type="checkbox" name="newsletter" value="test2" />test2
         <input type="checkbox" name="newsletter" value="test3" />test3
         <input type="checkbox" name="newsletter" checked="checked" value="test4" />test4
         <input type="checkbox" name="newsletter" value="test5" />test5
         
         <br><br>
         下拉列表1: <br>
         <select name="test" multiple="multiple" style="height: 100px" id="sele1">
            <option>浙江</option>
            <option selected="selected">辽宁</option>
            <option>北京</option>
            <option selected="selected">天津</option>
            <option>广州</option>
            <option>湖北</option>
         </select>
         
         <br><br>
         下拉列表2: <br>
         <select name="test2">
            <option>浙江</option>
            <option>辽宁</option>
            <option selected="selected">北京</option>
            <option>天津</option>
            <option>广州</option>
            <option>湖北</option>
         </select>
      </form>       
   </body>
</html>
```



#### 7、juery元素筛选

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220709114346919.png" alt="image-20220709114346919" style="zoom:50%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220709114407703.png" alt="image-20220709114407703" style="zoom:50%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220709114421696.png" alt="image-20220709114421696" style="zoom:50%;" />

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>DOM查询</title>
      <style type="text/css">
         div, span, p {
             width: 140px;
             height: 140px;
             margin: 5px;
             background: #aaa;
             border: #000 1px solid;
             float: left;
             font-size: 17px;
             font-family: Verdana;
         }
         
         div.mini {
             width: 55px;
             height: 55px;
             background-color: #aaa;
             font-size: 12px;
         }
         
         div.hide {
             display: none;
         }        
      </style>
      <script type="text/javascript" src="../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">
         $(document).ready(function(){
            function anmateIt(){
               $("#mover").slideToggle("slow", anmateIt);
            }
            anmateIt();
            
   /**
               
   过滤
   eq(index|-index)         
   first()                
   last()                    
   hasClass(class)          
   filter(expr|obj|ele|fn)    
   is(expr|obj|ele|fn)1.6*    
   has(expr|ele)           
   not(expr|ele|fn)         
   slice(start,[end])           
   
   查找
   children([expr])         
   closest(expr,[con]|obj|ele)1.6*   
   find(expr|obj|ele)              
   next([expr])               
   nextall([expr])             
   nextUntil([exp|ele][,fil])1.6*     
   parent([expr])                 
   parents([expr])             
   parentsUntil([exp|ele][,fil])1.6*  
   prev([expr])               
   prevall([expr])             
   prevUntil([exp|ele][,fil])1.6*     
   siblings([expr])            
   
   串联
   add(expr|ele|html|obj[,con])   
                     
   
   */
            
            //(1)eq()  选择索引值为等于 3 的 div 元素
            $("#btn1").click(function(){
               $("div").eq(3).css("background-color","#bfa");
            });
            //(2)first()选择第一个 div 元素
             $("#btn2").click(function(){
                //first()   选取第一个元素
               $("div").first().css("background-color","#bfa");
            });
            //(3)last()选择最后一个 div 元素
            $("#btn3").click(function(){
               //last()  选取最后一个元素
               $("div").last().css("background-color","#bfa");
            });
            //(4)filter()在div中选择索引为偶数的
            $("#btn4").click(function(){
               //filter()  过滤   传入的是选择器字符串
               $("div").filter(":even").css("background-color","#bfa");
            });
             //(5)is()判断#one是否为:empty或:parent
            //is用来检测jq对象是否符合指定的选择器
            $("#btn5").click(function(){
                   alert($("#one").is(":empty"))
            });
            
            //(6)has()选择div中包含.mini的
            $("#btn6").click(function(){
               //has(selector)  选择器字符串    是否包含selector
               $("div").has(".mini").css("background-color","#bfa");
            });
            //(7)not()选择div中class不为one的
            $("#btn7").click(function(){
               //not(selector)  选择不是selector的元素
               $("div").not(".one").css("background-color","#bfa");
            });
            //(8)children()在body中选择所有class为one的div子元素
            $("#btn8").click(function(){
               //children()  选出所有的子元素
               $("body").children("div.one").css("background-color","#bfa");
            });
            
            
            //(9)find()在body中选择所有class为mini的div元素
            $("#btn9").click(function(){
               //find()  选出所有的后代元素
               $("body").find("div.mini").css("background-color","#bfa");
            });
            //(10)next() #one的下一个div
            $("#btn10").click(function(){
               //next()  选择下一个兄弟元素
               $("#one").next("div").css("background-color","#bfa");
            });
            //(11)nextAll() #one后面所有的span元素
            $("#btn11").click(function(){
               //nextAll()   选出后面所有的元素
               $("#one").nextAll("span").css("background-color","#bfa");
            });
            //(12)nextUntil() #one和span之间的元素
            $("#btn12").click(function(){
               //
               $("#one").nextUntil("span").css("background-color","#bfa")
            });
            //(13)parent() .mini的父元素
            $("#btn13").click(function(){
               $(".mini").parent().css("background-color","#bfa");
            });
            //(14)prev() #two的上一个div
            $("#btn14").click(function(){
               //prev()  
               $("#two").prev("div").css("background-color","#bfa")
            });
            //(15)prevAll() span前面所有的div
            $("#btn15").click(function(){
               //prevAll()   选出前面所有的元素
               $("span").prevAll("div").css("background-color","#bfa")
            });
            //(16)prevUntil() span向前直到#one的元素
            $("#btn16").click(function(){
               //prevUntil(exp)   找到之前所有的兄弟元素直到找到exp停止
               $("span").prevUntil("#one").css("background-color","#bfa")
            });
            //(17)siblings() #two的所有兄弟元素
            $("#btn17").click(function(){
               //siblings()    找到所有的兄弟元素，包括前面的和后面的
               $("#two").siblings().css("background-color","#bfa")
            });
            
            
            //(18)add()选择所有的 span 元素和id为two的元素
            $("#btn18").click(function(){
   
               //   $("span,#two,.mini,#one")
               $("span").add("#two").css("background-color","#bfa");
               
            });
            


         });
         
         
      </script>
   </head>
   <body>    
      <input type="button" value="eq()选择索引值为等于 3 的 div 元素" id="btn1" />
      <input type="button" value="first()选择第一个 div 元素" id="btn2" />
      <input type="button" value="last()选择最后一个 div 元素" id="btn3" />
      <input type="button" value="filter()在div中选择索引为偶数的" id="btn4" />
      <input type="button" value="is()判断#one是否为:empty或:parent" id="btn5" />
      <input type="button" value="has()选择div中包含.mini的" id="btn6" />
      <input type="button" value="not()选择div中class不为one的" id="btn7" />
      <input type="button" value="children()在body中选择所有class为one的div子元素" id="btn8" />
      <input type="button" value="find()在body中选择所有class为mini的div后代元素" id="btn9" />
      <input type="button" value="next()#one的下一个div" id="btn10" />
      <input type="button" value="nextAll()#one后面所有的span元素" id="btn11" />
      <input type="button" value="nextUntil()#one和span之间的元素" id="btn12" />
      <input type="button" value="parent().mini的父元素" id="btn13" />
      <input type="button" value="prev()#two的上一个div" id="btn14" />
      <input type="button" value="prevAll()span前面所有的div" id="btn15" />
      <input type="button" value="prevUntil()span向前直到#one的元素" id="btn16" />
      <input type="button" value="siblings()#two的所有兄弟元素" id="btn17" />
      <input type="button" value="add()选择所有的 span 元素和id为two的元素" id="btn18" />

      
      <h3>基本选择器.</h3>
      <br /><br />
      文本框<input type="text" name="account" disabled="disabled" />
      <br><br>
      <div class="one" id="one">
         id 为 one,class 为 one 的div
         <div class="mini">class为mini</div>
      </div>
      <div class="one" id="two" title="test">
         id为two,class为one,title为test的div
         <div class="mini" title="other"><b>class为mini,title为other</b></div>
         <div class="mini" title="test">class为mini,title为test</div>
      </div>
      
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini"></div>
      </div>
      <div class="one">
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini">class为mini</div>
         <div class="mini" title="tesst">class为mini,title为tesst</div>
      </div>
      <div style="display:none;" class="none">style的display为"none"的div</div>
      <div class="hide">class为"hide"的div</div>
      <span id="span1">^^span元素 111^^</span>
      <div>
         包含input的type为"hidden"的div<input type="hidden" size="8">
      </div>
      <span id="span2">^^span元素 222^^</span>
      <div id="mover">正在执行动画的div元素.</div>
   </body>
</html>
```



#### 8、属性操作

html()获取起始标签和结束标签中的内容(和dom中的innerHTML一样)

text()设置和获取起始标签和结束标签中的文本内容

val()设置和获取表单的value

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <script type="text/javascript" src="../../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">
         $(function(){
            
            $("input[type=button]:eq(0)").click(function(){
               //$("#single :option:eq(2)").attr("selected", "selected");
               $("#single").val(["s3"]);
            });
            
            $("input[type=button]:eq(1)").click(function(){
               $("#multiple").val(["x2", "x4"]);
            });
            
            $("input[type=button]:eq(2)").click(function(){
               $(":checkbox").val(["check2", "check4"]);
            });
            
            $("input[type=button]:eq(3)").click(function(){
               $(":radio").val(["radio2"]);
            });
            
            $("input[type=button]:eq(4)").click(function(){
               $("#single")
                  .add("#multiple")
                  .add(":checkbox:checked")
                  .add(":radio:checked")
                  .each(function(){
                     alert($(this).val());
                  });
            });
         });
      </script>
   </head>
   <body>
      
      <input type="button" value="使单选下拉框的'选择3号'被选中"/>
      <input type="button" value="使多选下拉框选中的'选择2号'和'选择4号'被选中"/><br>
      <input type="button" value="使多选框的'多选2'和'多选4'被选中"/>
      <input type="button" value="使单选框的'单选2'被选中"/><br>
      <input type="button" value="打印已经被选中的值"><br>
 
      <br/>
      
      <select id="single" name="singlecheck">
        <option value="s1">选择1号</option>
        <option value="s2">选择2号</option>
        <option value="s3">选择3号</option>
      </select>
      
      <select id="multiple" multiple="multiple" name="multiplecheck" style="height:120px;">
        <option selected="selected" value="x1">选择1号</option>
        <option value="x2">选择2号</option>
        <option value="x3">选择3号</option>
        <option value="x4">选择4号</option>
        <option selected="selected" value="x5">选择5号</option>
      </select>
      
      <br/><br/>

      <input type="checkbox" name="c" value="check1"/> 多选1
      <input type="checkbox" name="c" value="check2"/> 多选2
      <input type="checkbox" name="c" value="check3"/> 多选3
      <input type="checkbox" name="c" value="check4"/> 多选4
      
      <br/>
      
      <input type="radio" name="r" value="radio1"/> 单选1
      <input type="radio" name="r"  value="radio2"/> 单选2
      <input type="radio" name="r"  value="radio3"/> 单选3

   </body>
</html>
```

**attr()设置和获取属性**

**proup也一样**

**练习：**

```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
<script type="text/javascript" src="../../script/jquery-1.7.2.js"></script>
<script type="text/javascript">
   
   $(function(){
      
      var $items = $(":checkbox[name=items]");
      var items = $("[name='items']");
      //全选按钮
      $("#checkedAllBtn").click(function(){
         items.attr("checked",true);
         $("#checkedAllBox").attr("checked",true);
      });
      //全不选按钮
      $("#checkedNoBtn").click(function(){
         items.attr("checked",false);
         $("#checkedAllBox").attr("checked",false);
      });
      
      //反选按钮
      $("#checkedRevBtn").click(function(){
         items.each(function(){
            this.checked = !this.checked;
         });
         var flag = $("[name='items']:checked").length==4;
         $("#checkedAllBox").attr("checked",flag);
      });
      
      //提交按钮
      $("#sendBtn").click(function(){
         $(":checkbox[name='items']:checked").each(function(){
            alert(this.value);
         });
      });
      
      //全选/全不选复选框
      $("#checkedAllBox").click(function(){
         items.attr("checked",this.checked);
      });
      
      //全选/全不选复选框与items状态同步
      $("[name='items']").click(function(){
         var flag = $("[name='items']:checked").length==4;
         $("#checkedAllBox").attr("checked",flag);
      });
   });
   
</script>
</head>
<body>

   <form method="post" action="">
   
      你爱好的运动是？<input type="checkbox" id="checkedAllBox" />全选/全不选 
      
      <br />
      <input type="checkbox" name="items" value="足球" />足球
      <input type="checkbox" name="items" value="篮球" />篮球
      <input type="checkbox" name="items" value="羽毛球" />羽毛球
      <input type="checkbox" name="items" value="乒乓球" />乒乓球
      <br />
      <input type="button" id="checkedAllBtn" value="全　选" />
      <input type="button" id="checkedNoBtn" value="全不选" />
      <input type="button" id="checkedRevBtn" value="反　选" />
      <input type="button" id="sendBtn" value="提　交" />
   </form>

</body>
</html>
```



#### 9、其他操作

插入

appendTo()    a.appendTo(b)  a插入到b元素末尾

a.prependTo(b)   a插入到B所有元素前面



外部插入

insertAfter()    a x b   得到ba

a.insertBefore(b)       ab



替换

a.replaceWith(b)    用b换a

a.replaceAll(b)    用a替换所有b



删除

a.remove()  删除a标签

a.empty()清空a标签中的所有信息



```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
   <style type="text/css">
      select {
         width: 100px;
         height: 140px;
      }
      
      div {
         width: 130px;
         float: left;
         text-align: center;
      }
   </style>
   <script type="text/javascript" src="script/jquery-1.7.2.js"></script>
   <script type="text/javascript">
      $(function (){
         $("button:eq(0)").click(function (){
            //select标签第一个，后面的后代且选中,加到有边的select
            $("select:eq(0) option:selected").appendTo($("select:eq(1)"));
         })
         $("button:eq(1)").click(function (){
            //select标签第一个，后面的后代且选中,加到有边的select
            $("select:eq(0) option").appendTo($("select:eq(1)"));
         })

         $("button:eq(2)").click(function (){
            //select标签第一个，后面的后代且选中,加到有边的select
            $("select:eq(1) option:selected").appendTo($("select:eq(0)"));
         })
         $("button:eq(3)").click(function (){
            //select标签第一个，后面的后代且选中,加到有边的select
            $("select:eq(1) option").appendTo($("select:eq(0)"));
         })
      })
   
   </script>
</head>
<body>

   <div id="left">
      <select multiple="multiple" name="sel01">
         <option value="opt01">选项1</option>
         <option value="opt02">选项2</option>
         <option value="opt03">选项3</option>
         <option value="opt04">选项4</option>
         <option value="opt05">选项5</option>
         <option value="opt06">选项6</option>
         <option value="opt07">选项7</option>
         <option value="opt08">选项8</option>
      </select>
      
      <button>选中添加到右边</button>
      <button>全部添加到右边</button>
   </div>
   <div id="rigth">
      <select multiple="multiple" name="sel02">
      </select>
      <button>选中删除到左边</button>
      <button>全部删除到左边</button>
   </div>

</body>
</html>
```

添加删除记录

具体见代码



### 4、css样式

addClass()  添加样式

removeClass()  删除样式

toggleClass()  有就删除，没有就添加

offset()   获取和设置元素坐标

```html
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>品牌展示练习</title>
<style type="text/css">
* {
   margin: 0;
   padding: 0;
}

body {
   font-size: 12px;
   text-align: center;
}

a {
   color: #04D;
   text-decoration: none;
}

a:hover {
   color: #F50;
   text-decoration: underline;
}

.SubCategoryBox {
   width: 600px;
   margin: 0 auto;
   text-align: center;
   margin-top: 40px;
}

.SubCategoryBox ul {
   list-style: none;
}

.SubCategoryBox ul li {
   display: block;
   float: left;
   width: 200px;
   line-height: 20px;
}

.showmore , .showless{
   clear: both;
   text-align: center;
   padding-top: 10px;
}

.showmore a , .showless a{
   display: block;
   width: 120px;
   margin: 0 auto;
   line-height: 24px;
   border: 1px solid #AAA;
}

.showmore a span {
   padding-left: 15px;
   background: url(img/down.gif) no-repeat 0 0;
}

.showless a span {
   padding-left: 15px;
   background: url(img/up.gif) no-repeat 0 0;
}

.promoted a {
   color: #F50;
}
</style>
<script type="text/javascript" src="script/jquery-1.7.2.js"></script>
<script type="text/javascript">
   $(function() {
      $("li:gt(5):not(:last)").hide();
     //给按钮绑定单机
     $("div div a").click(function (){
        //让隐藏标签切换或者展示标签隐藏
        $("li:gt(5):not(:last)").toggle();
        //判断是否隐藏
       if( $("li:gt(5):not(:last)").is(":hidden")){
          $("div div a span").text("显示全部品牌")
          //改角标
          //先去掉原来
          $("div div").removeClass()
          $("div div").addClass("showmore")
       }else{
          $("div div a span").text("显示精品品牌")
          $("div div").removeClass()
          $("div div").addClass("showless")
          //加高亮
          $("li:contains('明基')").addClass("promoted")
       }

        return false;
     })
   });
</script>
</head>
<body>
   <div class="SubCategoryBox">
      <ul>
         <li><a href="#">佳能</a><i>(30440) </i></li>
         <li><a href="#">索尼</a><i>(27220) </i></li>
         <li><a href="#">三星</a><i>(20808) </i></li>
         <li><a href="#">尼康</a><i>(17821) </i></li>
         <li><a href="#">松下</a><i>(12289) </i></li>
         <li><a href="#">卡西欧</a><i>(8242) </i></li>
         <li><a href="#">富士</a><i>(14894) </i></li>
         <li><a href="#">柯达</a><i>(9520) </i></li>
         <li><a href="#">宾得</a><i>(2195) </i></li>
         <li><a href="#">理光</a><i>(4114) </i></li>
         <li><a href="#">奥林巴斯</a><i>(12205) </i></li>
         <li><a href="#">明基</a><i>(1466) </i></li>
         <li><a href="#">爱国者</a><i>(3091) </i></li>
         <li><a href="#">其它品牌相机</a><i>(7275) </i></li>
      </ul>
      <div class="showmore">
         <a href="more.html"><span>显示全部品牌</span></a>
      </div>
   </div>
</body>
    </htm>
```



### 5、Jquery动画

#### 基本动画

show()   隐藏元素显示

hide()  将可见元素隐藏

toggle()  可见就隐藏，不可见就显示

都可以添加参数

第一个参数是市场，毫秒为单位，第二个是回调函数



#### 淡入淡出动画

fadeln()  淡入  fadeOut()

fadeTO()   在指定时间修改透明度

fadeToggle()   切换淡入淡出



```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <link href="css/style.css" type="text/css" rel="stylesheet" />
      <script type="text/javascript" src="script/jquery-1.7.2.js"></script>
   
<script type="text/javascript">
   /*     
      基本
      show([speed,[easing],[fn]]) 
      hide([speed,[easing],[fn]]) 
      toggle([speed],[easing],[fn]) 
      滑动
      slideDown([spe],[eas],[fn]) 
      slideUp([speed,[easing],[fn]]) 
      slideToggle([speed],[easing],[fn]) 
      淡入淡出
      fadeIn([speed],[eas],[fn]) 
      fadeOut([speed],[eas],[fn]) 
      fadeTo([[spe],opa,[eas],[fn]]) 
      fadeToggle([speed,[eas],[fn]])
      */
      $(function(){
         //显示   show()
         $("#btn1").click(function(){
            $("#div1").show(1000);
         });       
         //隐藏  hide()
         $("#btn2").click(function(){
            $("#div1").hide(1000);
         });    
         //切换   toggle()
         $("#btn3").click(function(){
            $("#div1").toggle(1000);
         });    
         
         
         //淡入   fadeIn()
         $("#btn4").click(function(){
            $("#div1").fadeIn(500);
         });    
         //淡出  fadeOut()
         $("#btn5").click(function(){
            $("#div1").fadeOut(500);
         });    
         
         //淡化到  fadeTo()
         $("#btn6").click(function(){
            $("#div1").fadeTo("slow",Math.random());
         });    
         //淡化切换  fadeToggle()
         $("#btn7").click(function(){
            $("#div1").fadeToggle("slow","linear");
         });    
      })
</script>
   
   </head>
   <body>
      <table style="float: left;">
         <tr>
            <td><button id="btn1">显示show()</button></td>
         </tr>
         <tr>
            <td><button id="btn2">隐藏hide()</button></td>
         </tr>
         <tr>
            <td><button id="btn3">显示/隐藏切换 toggle()</button></td>
         </tr>
         <tr>
            <td><button id="btn4">淡入fadeIn()</button></td>
         </tr>
         <tr>
            <td><button id="btn5">淡出fadeOut()</button></td>
         </tr>
         <tr>
            <td><button id="btn6">淡化到fadeTo()</button></td>
         </tr>
         <tr>
            <td><button id="btn7">淡化切换fadeToggle()</button></td>
         </tr>
      </table>
      
      <div id="div1" style="float:left;border: 1px solid;background-color: blue;width: 300px;height: 200px;">
         jquery动画定义了很多种动画效果，可以很方便的使用这些动画效果
      </div>
   </body>

</html>
```



### 6、事件操作

$(function(){})和window.onload=function(){}区别

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220709122530619.png" alt="image-20220709122530619" style="zoom:50%;" />



### 7、其他事件

click()  mouseover()鼠标移入  mouseout()

blind() 给元素一次绑定多个事件

one() 和上面一样，但是只会响应一次

live() 绑定选择器匹配的所有元素的事件，哪怕这个元素是后面动态创建出来的

 urblind()解绑

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <link href="css/style.css" type="text/css" rel="stylesheet" />
      <script type="text/javascript" src="../../script/jquery-1.7.2.js"></script>
      <script type="text/javascript">
      
         $(function(){
            $("h5").click(function (){
               alert("h5")
            })
            //鼠标移入
            $("h5").mousemove(function (){
               alert("移入")
            })
            //移出
            $("h5").mouseout(function (){
               alert("移出")
            })
         });
      
      </script>
   </head>
   <body>
      <div id="panel">
         <h5 class="head">什么是jQuery?</h5>
         <div class="content">
            jQuery是继Prototype之后又一个优秀的JavaScript库，它是一个由 John Resig 创建于2006年1月的开源项目。jQuery凭借简洁的语法和跨平台的兼容性，极大地简化了JavaScript开发人员遍历HTML文档、操作DOM、处理事件、执行动画和开发Ajax。它独特而又优雅的代码风格改变了JavaScript程序员的设计思路和编写程序的方式。
         </div>
      </div>
   </body>

</html>
```

### 8、事件冒泡

父子监听同一个事件，当触发子元素事件，父元素的事件也一起触发

return false可以阻止冒泡

```html
<html>
   <head>
      <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
      <title>Untitled Document</title>
      <style type="text/css">
         *{
            margin: 0;
            padding: 0;
         }
         body{
            font-size: 13px;
            line-height: 130%;
            padding: 60px;
         }
         #content{
            width: 220px;
            border: 1px solid #0050D0;
            background: #96E555;
         }
         span{
            width: 200px;
            margin: 10px;
            background: #666666;
            cursor: pointer;
            color: white;
            display: block;
         }
         p{
            width: 200px;
            background: #888;
            color: white;
            height: 16px;
         }
      </style>
      <script type="text/javascript" src="jquery-1.7.2.js"></script>
      <script type="text/javascript">
         $(function(){
            
            //冒泡就是事件的向上传导，子元素的事件被触发，父元素的响应事件也会触发
            //解决冒泡问题：return false;
            
            //给span绑定一个单击响应函数
            $("span").click(function(){
               alert("我是span的单击响应函数");
               return false;
            });
            
            //给id为content的div绑定一个单击响应函数
            $("#content").click(function(){
               alert("我是div的单击响应函数");
               return false;
            });
            
            //给body绑定一个单击响应函数
            $("body").click(function(){
               //alert("我是body的单击响应函数");
            });
            
            //取消默认行为
            /* $("a").click(function(){
               return false;
            }) */
            
         })
      </script>
   </head>
   <body>
      <div id="content">
         外层div元素
         <span>内层span元素</span>
         外层div元素
      </div>
      
      <div id="msg"></div>   
      
      <br><br>
      <a href="http://www.hao123.com" onclick="return false;">WWW.HAO123.COM</a> 
   </body>
</html>
```



### 9、js事件对象

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220709123414229.png" alt="image-20220709123414229" style="zoom:50%;" />

```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
<style type="text/css">

   #areaDiv {
      border: 1px solid black;
      width: 300px;
      height: 50px;
      margin-bottom: 10px;
   }
   
   #showMsg {
      border: 1px solid black;
      width: 300px;
      height: 20px;
   }

</style>
<script type="text/javascript" src="jquery-1.7.2.js"></script>
<script type="text/javascript">
     //获取事件对象
   //1.原生javascript获取 事件对象
   window.onload=function (){
      var a=document.getElementById("areaDiv");
      a.onclick=function (event){
         alert("你好")
      }
   }
   $(function (){
      $("#areaDiv").click(function (event){
         alert("年后呀")
      })

      //绑定多个事件
      $("#showMsg").bind("mouseover mouseout",function (event){
         if(event.type=="mouseover")alert("移入")
         else alert("鼠标移出")
      })
   })
   //2.JQuery代码获取 事件对象
   //3.使用bind同时对多个事件绑定同一个函数。怎么获取当前操作是什么事件。


</script>
</head>
<body>

   <div id="areaDiv"></div>
   <div id="showMsg">1</div>

</body>
</html>
```



10、图片跟随

```html
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
<style type="text/css">
   body {
      text-align: center;
   }
   #small {
      margin-top: 150px;
   }
   #showBig {
      position: absolute;
      display: none;
   }
</style>
<script type="text/javascript" src="script/jquery-1.7.2.js"></script>
<script type="text/javascript">
   $(function(){
      $("#small").bind("mouseover mouseout mousemove",function (event){
         if(event.type=="mouseover"){
            $("#showBig").show();
         }else if(event.type=="mouseout") {
            $("#showBig").hide();
         }else{
            $("#showBig").offset({
               left:event.pageX+10,
               top:event.pageY+10
            })
         }
      })
   });
</script>
</head>
<body>

   <img id="small" src="img/small.jpg" />
   
   <div id="showBig">
      <img src="img/big.jpg">
   </div>

</body>
</html>
```



## 六、XML

​	<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709153105.png" alt="微信截图_20220709153105" style="zoom:67%;" />										

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709153957.png" alt="微信截图_20220709153957" style="zoom:50%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709154332.png" alt="微信截图_20220709154332" style="zoom: 67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709155109.png" alt="微信截图_20220709155109" style="zoom:67%;" />



## **七、Tomcat阶段(重要)**

### 1、介绍

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709171606.png" alt="微信截图_20220709171606" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709173224.png" alt="微信截图_20220709173224" style="zoom:67%;" />

![微信截图_20220709183758](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709183758.png)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709195025.png" alt="微信截图_20220709195025" style="zoom:67%;" />



### 2、创建web程序

1、创建普通的java模块

2、在java模块添加框架，web应用程序

3、在web下的web-inf下创建两个包，一个叫classes，另一个叫lib,lib里面放各种jar包，记住，tomcat不要下载10，要不然很麻烦，然后导入servlet api的jar包，具体看操作。然后是在项目结构里面模块下的路径，把两个路径改成classes,然后依赖下的+号点jar目录选lib。

这样子创建好了

![微信截图_20220709203253](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220709203253.png)

### 3、启动

实现tomcat配置，最好把名字改成包名

创建java类要继承Httpservlet类，实现post,和get方法

然后在web.xml下配置路径

这个才是对的

```
public class test implements javax.servlet.Servlet {
```

![微信截图_20220710160239](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710160239.png)

常见错误

![微信截图_20220710160748](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710160748.png)

![微信截图_20220710162017](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710162017.png)



### 4、简介

![微信截图_20220710162017](C:\Users\waili\Desktop\usual\微信截图\javaweb\微信截图_20220710162017.png)

### 5、生命周期

![微信截图_20220710162541](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710162541.png)

### 6、ServletConfig

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710181313.png" alt="微信截图_20220710181313" style="zoom: 200%;" />





### 7、ServletContext

![微信截图_20220710182233](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710182233.png)



<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710231205.png" alt="微信截图_20220710231205" style="zoom:67%;" />

作用

![微信截图_20220710234941](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220710234941.png)

![微信截图_20220711000033](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711000033.png)





### 8、http

get

![微信截图_20220711010158](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711010158.png)

post

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711010604.png" alt="微信截图_20220711010604" style="zoom: 50%;" />



请求头

![微信截图_20220711010744](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711010744.png)

**get和post使用**

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711010832.png" alt="微信截图_20220711010832" style="zoom: 67%;" />

常见状态

![微信截图_20220711142504](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711142504.png)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711143527.png" alt="微信截图_20220711143527" style="zoom:50%;" />

### **9、HttpServletRequest**

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711143837.png" alt="微信截图_20220711143837" style="zoom: 67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711144836.png" alt="微信截图_20220711144836" style="zoom:67%;" />

常见方法展示

![微信截图_20220711151928](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711151928.png)



![微信截图_20220711160448](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711160448.png)

#### **解决乱码**

![微信截图_20220711160623](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711160623.png)



### **10、请求转发**

大概意思

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711191309.png" alt="微信截图_20220711191309" style="zoom: 50%;" />

![微信截图_20220711193843](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711193843.png)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711193910.png" alt="微信截图_20220711193910" style="zoom:67%;" />

![微信截图_20220711193956](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711193956.png)

![微信截图_20220711194006](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711194006.png)







### 11、路径

![微信截图_20220711231901](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711231901.png)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711232350.png" alt="微信截图_20220711232350" style="zoom:67%;" />





### **12、HttpsevletResponse**

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711232839.png" alt="微信截图_20220711232839" style="zoom:67%;" />



### **13、输入输出**

![微信截图_20220711233302](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711233302.png)

用法如下：

![微信截图_20220711234647](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711234647.png)

设置字符集防止乱码

![微信截图_20220711235809](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711235809.png)

简写：

![微信截图_20220711235918](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220711235918.png)



### 14、重定向(重点)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220712164730.png" alt="微信截图_20220712164730" style="zoom:67%;" />

特点：

![微信截图_20220712171253](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220712171253.png)

方式

![微信截图_20220712172555](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220712172555.png)



## 八、三层框架

### 1、简介



![微信截图_20220712174831](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220712174831.png)



### 2、具体分层

![微信截图_20220712193953](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220712193953.png)

![微信截图_20220725053108](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220725053108.png)

### 3、utils(工具类)

封装数据库

```java
public class JDBCutlis {
    private static DruidDataSource dataSource;
    static {
        Properties properties=new Properties();
        //读取文件的内容
       InputStream inputStream= JDBCutlis.class.getClassLoader().getResourceAsStream("jdbc.properties");
        try {
            //从流中加载数据
            properties.load(inputStream);
            dataSource= (DruidDataSource) DruidDataSourceFactory.createDataSource(properties);

        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
    //获取数据库连接处中的链接
    public static Connection getConnection(){
        //如果返回null说明获取链接失败
      Connection connection=null;
        try {
            connection=dataSource.getConnection();

        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
        return connection;
    }

     //关闭链接
    public static  void close(Connection connection){
        try {
            if(connection!=null)
            connection.close();
        } catch (SQLException e) {
            throw new RuntimeException(e);
        }
    }

    public static void main(String[] args) {
        System.out.println(getConnection());
    }

}
```

其他见代码bookitem



## 九、jsp

### 1、含义

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220713213413.png" alt="微信截图_20220713213413" style="zoom:67%;" />

### 2、头部命令

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714161142.png" alt="微信截图_20220714161142" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714161617.png" alt="微信截图_20220714161617" style="zoom:67%;" />

### 3、声明和使用

![微信截图_20220714164236](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714164236.png)



### 4、脚本

#### 1、声明脚本

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714164316.png" alt="微信截图_20220714164316" style="zoom:67%;" />

#### 2、表达式脚本



<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714165941.png" alt="微信截图_20220714165941" style="zoom:67%;" />

#### 3、代码脚本

![微信截图_20220714211317](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714211317.png)

![微信截图_20220714210027](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714210027.png)

#### 4、注释

![微信截图_20220714211514](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714211514.png)

### **5、内置对象(重点)**

![微信截图_20220714212213](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714212213.png)

### **6、四大域对象**

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714213539.png" alt="微信截图_20220714213539" style="zoom:67%;" />

注意事项

![微信截图_20220714220101](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714220101.png)



### 7、静态包含

代码复用

![微信截图_20220714221223](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714221223.png)



### 8、动态包含

![微信截图_20220714222107](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714222107.png)



### **9、jsp标签转发**(重要)

![微信截图_20220714222721](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714222721.png)



### **11、请求转发**

![微信截图_20220714225134](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714225134.png)

![微信截图_20220714231047](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714231047.png)

![微信截图_20220714231058](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220714231058.png)



### **12、监听器**

#### **1、含义**

![微信截图_20220715132636](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715132636.png)



#### 2、配置

![微信截图_20220715132957](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715132957.png)



#### 3、实现类

![微信截图_20220715133129](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715133129.png)







### 13、el表达式( 比较简洁)

#### 1、含义

![微信截图_20220715133457](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715133457.png)



#### 2、搜索规则

![微信截图_20220715133716](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715133716.png)



#### 3、实现和练习

![微信截图_20220715134404](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715134404.png)

![微信截图_20220715134701](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715134701.png)



#### 4、运算符号

![微信截图_20220715134726](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715134726.png)

![微信截图_20220715134839](C:\Users\waili\Desktop\usual\微信截图\javaweb\微信截图_20220715134839.png)

![微信截图_20220715134904](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715134904.png)

![微信截图_20220715134955](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715134955.png)

![微信截图_20220715135200](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715135200.png)

![微信截图_20220715152046](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715152046.png)

#### **5、el表达式的隐含对象**

![微信截图_20220715152506](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715152506.png)



#### 6、获取四个域中属性



![微信截图_20220715170646](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715170646.png)

用法：

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715170700.png" alt="微信截图_20220715170700" style="zoom:50%;" />

#### 7、标签库

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715222425.png" alt="微信截图_20220715222425" style="zoom:67%;" />

步骤

记得要用tomcat8.要不然会报错

#### 8、保存数据set

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715223235.png" alt="微信截图_20220715223235" style="zoom:67%;" />

![微信截图_20220715224649](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220715224649.png)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716001904.png" alt="微信截图_20220716001904" style="zoom:67%;" />



#### 9、遍历 for each

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716003356.png" alt="微信截图_20220716003356" style="zoom:67%;" />



#### 10、文件上传

![微信截图_20220716165912](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716165912.png)

![微信截图_20220716170526](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716170526.png)

常用文件api

![微信截图_20220716175232](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716175232.png)

![微信截图_20220716175326](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716175326.png)

具体代码：

![微信截图_20220716230716](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716230716.png)



#### 11、文件下载

![微信截图_20220716231351](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716231351.png)

![微信截图_20220716233735](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716233735.png)

代码：

![微信截图_20220716234052](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220716234052.png)





#### 12、静态包含

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220717153027.png" alt="微信截图_20220717153027" style="zoom:67%;" />

![微信截图_20220717153058](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220717153058.png)



#### **13、通过反射来调用方法(优化)**

![微信截图_20220717163853](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220717163853.png)

action是方法名

代码如下：

![微信截图_20220717164549](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220717164549.png)

![微信截图_20220718011354](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220718011354.png)

![微信截图_20220718011413](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220718011413.png)

![微信截图_20220729092727](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220729092727.png)



#### 14、MVC

![微信截图_20220718014048](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220718014048.png)



## 十、cookie

### 1、含义

简单来说是保存用户信息

![微信截图_20220720032828](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720032828.png)

### 2、创建

![微信截图_20220720032642](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720032642.png)

![微信截图_20220720032807](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720032807.png)

记得每次创建要add







### 3、操作

![微信截图_20220720141928](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720141928.png)

![微信截图_20220720141935](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720141935.png)



修改

![微信截图_20220720142949](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720142949.png)

### 4、生命周期

![微信截图_20220720144826](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720144826.png)

### 5、路径设置

![微信截图_20220720145527](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720145527.png)



## 十一、session

### 1、含义

![微信截图_20220720171012](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720171012.png)

### 2、操作

![微信截图_20220721205749](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721205749.png)

3、生命周期

![微信截图_20220721211049](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721211049.png)



### 3、设置时长

![微信截图_20220721211844](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721211844.png)



### 4、用户的登录和注销

用户的信息保存到session域中

mvc也是判断用户有没有登录成功就是用session来判断

退出登录就是销毁session

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819011207.png)

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819011216.png)
