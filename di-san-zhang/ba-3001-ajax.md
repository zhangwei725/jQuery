# jQuery Ajax

## 一、概要

​	jQuery在异步提交方面封装的很好，直接用AJAX非常麻烦，jQuery大大简化了我们的操作，不用考虑浏览器的兼容性.

## 二、核心方法

### 1、ajax()

#### 1.1、说明

> 发送并处理AJAX请求。这是jQuery底层的AJAX实现，包含处理AJAX请求所需的一切功能。
>
> jQuery的底层AJAX实现。jQuery.get()、 jQuery.post()、load()、 jQuery.getJSON()、 jQuery.getScript()等函数都是该函数的简化形式

#### 1.2、语法格式

1. 格式一

   jQuery.ajax( [ settings ] ] )

2. 格式二

   jQuery.ajax( url [, settings ] ] )

#### 1.3、参数

| 参数       | 描述                                       |
| -------- | ---------------------------------------- |
| url      | String类型URL请求字符串。                        |
| settings | 可选/Object类型一个Object对象，其中的每个属性用来指定发送请求所需的额外参数设置。 |

#### 1.4、参数说明

| 参数名             | 类型            | 描述                                       |
| --------------- | ------------- | ---------------------------------------- |
| **url**         | String        | (默认: 当前页地址) 发送请求的地址。                     |
| **type**        | String        | (默认: "GET") 请求方式 ("POST" 或 "GET")， 默认为 "GET"。注意：其它 HTTP 请求方法，如 PUT 和 DELETE 也可以使用，但仅部分浏览器支持。 |
| **timeout**     | Number        | 设置请求超时时间（毫秒）。此设置将覆盖全局设置。                 |
| **async**       | Boolean       | (默认: true) 默认设置下，所有请求均为异步请求。如果需要发送同步请求，请将此选项设置为 false。注意，同步请求将锁住浏览器，用户其它操作必须等待请求完成才可以执行。 |
| **beforeSend**  | Function      | 发送请求前可修改 XMLHttpRequest 对象的函数，如添加自定义 HTTP 头。XMLHttpRequest 对象是唯一的参数。function (XMLHttpRequest) {  this; // the options for this ajax request} |
| **cache**       | Boolean       | (默认: true) jQuery 1.2 新功能，设置为 false 将不会从浏览器缓存中加载请求信息。 |
| **complete**    | Function      | 请求完成后回调函数 (请求成功或失败时均调用)。参数： XMLHttpRequest 对象，成功信息字符串。function (XMLHttpRequest, textStatus) {  this; } |
| **contentType** | String        | (默认: "application/x-www-form-urlencoded") 发送信息至服务器时内容编码类型。默认值适合大多数应用场合。 |
| **data**        | Object,String | 发 送到服务器的数据。将自动转换为请求字符串格式。GET 请求中将附加在 URL 后。查看 processData 选项说明以禁止此自动转换。必须为 Key/Value 格式。如果为数组，jQuery 将自动为不同值对应同一个名称。如 {foo:["bar1", "bar2"]} 转换为 '&foo=bar1&foo=bar2'。 |
| **dataType**    | String        | 预期服务器返回的数据类型。如果不指定，jQuery 将自动根据 HTTP 包 MIME 信息返回 responseXML 或 responseText，并作为回调函数参数传递，可用值:"xml": 返回 XML 文档，可用 jQuery 处理。"html": 返回纯文本 HTML 信息；包含 script 元素。"script": 返回纯文本 JavaScript 代码。不会自动缓存结果。"json": 返回 JSON 数据 。"jsonp": JSONP 格式。使用 JSONP形式调用函数时，如 "url?callback=?" jQuery 将自动替换 ? 为正确的函数名，以执行回调函数。 |
| **error**       | Function      | (默认: 自动判断 (xml 或 html)) 请求失败时将调用此方法。这个方法有三个参数：XMLHttpRequest 对象，错误信息，（可能）捕获的错误对象。function (XMLHttpRequest, textStatus, errorThrown) {  // 通常情况下textStatus和errorThown只有其中一个有值   this; |
| **global**      | Boolean       | (默认: true) 是否触发全局 AJAX 事件。设置为 false 将不会触发全局 AJAX 事件，如 ajaxStart 或 ajaxStop 。可用于控制不同的Ajax事件 |
| **processData** | Boolean       | (默认: true) 默认情况下，发送的数据将被转换为对象(技术上讲并非字符串) 以配合默认内容类型 "application/x-www-form-urlencoded"。如果要发送 DOM 树信息或其它不希望转换的信息，请设置为 false。 |
| **success**     | Function      | 请求成功后回调函数。这个方法有两个参数：服务器返回数据，返回状态function (data, textStatus) { } |

#### 1.5、示例代码

1. get请求

   ```
      // 将url单独提取出来作为第一个参数(jQuery 1.5+才支持)
      $.ajax("/login?name=haha&pwd=123, {
           dataType: "json" , // 返回JSON格式的数据
           success: function( data, textStatus, jqXHR ){
              // jQuery已帮我们将该JSON字符串转换为对应的JS对象，可以直接使用
              alert( data.name ); // CodePlayer
          }   
      });

      $.ajax( {
          // 注意这里有个参数callback=?
           url: "name=hehe&age=21&callback=?",
           async: false // 同步请求，发送请求后浏览器将被锁定，只有等到该请求完成(无论成功或失败)后，用户才能操作，js代码才会继续执行
          , dataType: "jsonp" // 返回JSON格式的数据
          , success: function( data, textStatus, jqXHR ){
              alert( data.state );
          }   
      });
      $.ajax( {
          // 加载指定的js文件到当前文档中
            url: "http://code.jquery.com/jquery-1.8.3.min.js", 
          dataType: "script"
      });
   ```

2. post请求

   ```
     $.ajax({
                   url: "/account/login",
                   type: "post",
                   data: "name=zw&age=18",
                   success: function (data, textStatus, jqXHR) {
                       // data 是返回的数据
                       // textStatus 可能为"success"、"notmodified"等
                       // jqXHR 是经过jQuery封装的XMLHttpRequest对象
                       alert("返回的数据" + data);
                   }
               });
    
               $.ajax({
                   url: "/shop?page=1&id=3",
                   type: "post",
                   //等价于"uid=1&name=zw&age=18"
                   data: {uid: 1, name: "zw", age: 18},
                   // 请求成功时执行
                   success: function (data, textStatus, jqXHR) {
                       alert("返回的数据" + data);
                   },
                   // 请求失败时执行
                   error: function (jqXHR, textStatus, errorMsg) {
                       // jqXHR 是经过jQuery封装的XMLHttpRequest对象
                       // textStatus 可能为： null、"timeout"、"error"、"abort"或"parsererror"
                       // errorMsg 可能为： "Not Found"、"Internal Server Error"等
                       alert("请求失败：" + errorMsg);
                   }
               });
   ```

### 2、get()

#### 2.1、说明

> 通过HTTP GET形式的AJAX请求获取远程数据

#### 2.2、语法格式

1. 格式一

   ```javascript
   jQuery.get( url [, data ] [, success ] [, type ] )
   //等价于
   $.ajax({
    url: url,
    type: "GET",
    data: data,
    success: success,
    dataType: dataType
   });
   ```

#### 2.3、参数

| 参数      | 描述                                       |
| ------- | ---------------------------------------- |
| url     | String类型指定请求的目标URL。                      |
| data    | 可选/String/Object类型发送请求传递的数据。             |
| success | 可选/Function类型请求成功时执行的回调函数。它有3个参数：一是请求返回的数据，二是请求状态文本(例如"success"、 "notmodified")，三是当前jqXHR对象(在jQuery 1.4及之前版本中，该参数为原生的XMLHttpRequest对象)。 |
| type    | 可选/String类型指定请求返回的数据类型，可以为xml、 html、 script、 json、 jsonp、text。如果省略该参数，jQuery将会根据请求进行智能猜测，猜测范围为：xml、 json、 script 或html。 |

#### 2.4、示例代码

1. 对数据不处理

   ```
    $(function () {
               // 等价于shop?id=1的数据，但不作任何处理
               $.get("/shop?id=1");
               // 等价于shop?id=1&orderId=1
               $.get("/shop?id=1", "orderId=1");
               // 等价于 /shop?id=1&orderId=1
               $.get("/shop?id=1", {orderId: 1});
          });
               
   ```


1. 对数据处理

   ```
    $(function () {
              $.get("/shop?id=1", function (data, textStatus, jqXHR) {
                  console.log("数据:" + data);
                  console.log("状态信息:" + textStatus);
                  console.log("jq的xhr:" + jqXHR);
              });

              $.get("/shop?id=1", {sid: 2},
                  function (data, textStatus, jqXHR) {
                      console.log(data.name);//
                      console.log("状态信息:" + textStatus);
                      console.log("jq的xhr:" + jqXHR);
                  }, "json");

          });
   ```

### 3、post()

#### 3.1、说明

> 通过HTTP POST形式的AJAX请求获取服务器的数据

#### 3.2、语法格式

1. 格式一

   ```
   jQuery.post( url [, data ] [, success ] [, type ] )
   //等价于
   $.ajax({
    url: url,
    type: "POST",
    data: data,
    success: success,
    dataType: dataType
   });
   ```

#### 3.3、参数

> | 参数      | 描述                                       |
> | ------- | ---------------------------------------- |
> | url     | String类型指定请求的目标URL。                      |
> | data    | 可选/String/Object类型发送请求传递的数据。             |
> | success | 可选/Function类型请求成功时执行的回调函数。它有3个参数：一是请求返回的数据，二是请求状态文本(例如"success"、 "notmodified")，三是当前[jqXHR对象 |
> | type    | 可选/String类型指定请求返回的数据类型，可以为xml、 html、 script、 json、 jsonp、text。如果省略该参数，jQuery将会根据请求进行智能解析，解析范围为：xml、 json、 script或html。 |

#### 3.5、示例代码

1. 对数据不处理

   ```
    $(function () {
               // 等价于/shop?id=1的数据，但不作任何处理
               $.post("/shop?id=1");
               // 等价于shop?id=1&orderId=1
               $.post("/shop?id=1", "orderId=1");
               // 等价于 /shop?id=1&orderId=1
               $.post("/shop?id=1", {orderId: 1});
          });       
   ```

2. 对数据处理

   ```
    $(function () {
              $.post("/shop", function (data, textStatus, jqXHR) {
                  console.log("数据:" + data);
                  console.log("状态信息:" + textStatus);
                  console.log("jq的xhr:" + jqXHR);
              });
              
              $.post("/shop", {id: 2},
                  function (data, textStatus, jqXHR) {
                      console.log(data.name);//
                      console.log("状态信息:" + textStatus);
                      console.log("jq的xhr:" + jqXHR);
                  }, "json");

          });
   ```

### 4、getJSON()

#### 4.1、说明

> 通过HTTP GET形式的AJAX请求获取服务器JSON格式的数据

#### 4.2、语法格式

1. 格式一

   ```
   jQuery.getJSON( url [, data ] [, success ] )
   ```

#### 4.3、参数

| 参数      | 描述                                       |
| ------- | ---------------------------------------- |
| url     | String类型指定请求的目标URL。                      |
| data    | 可选/String/Object类型发送请求传递的数据。             |
| success | 可选/Function类型请求成功时执行的回调函数。它有3个参数：一是请求返回的数据，二是请求状态文本(例如"success"、 "notmodified")，三是当前jqXHR对象(在jQuery 1.4及之前版本中，该参数为原生的XMLHttpRequest对象)。 |

#### 4.4、参数说明

​	

#### 4.5、示例代码

### 5、getScript()

#### 5.1、说明

> 用于通过HTTP GET形式的加载JavaScript文件并运行js文件

#### 5.2、语法格式

1. 格式一

   ```
   jQuery.getScript(url, success);
   // 等价于
   $.ajax({
    url: url,
    type: "GET",
    success: success,
    dataType: "script"
   });
   ```

#### 5.3、参数

| 参数      | 描述                        |
| ------- | ------------------------- |
| url     | String类型指定请求的目标URL。       |
| success | 可选/Function类型请求成功时执行的回调函数 |

#### 5.4、示例代码

1. 加载本地的js文件

   ```
   $(function () {
     $("#btn").click(function () {
         $.getScript("test.js", function () {
         //回调函数
         });
     })
   });
   ```

2. 加载网络js文件

   ```
   $.getScript("https://cdn.bootcss.com/jquery/3.2.1/jquery.js", function(data, textStatus, jqXHR){
   } );
   ```

### 6、load()

#### 6.1、说明

> 从服务器加载数据，并使用返回的html内容替换当前匹配元素的内容。
> 默认使用GET方式，如果提供了对象形式的数据，则自动转为POST方式。
> 只会替换每个匹配元素的内部内容(innerHTML)。

#### 6.2、语法格式

1. 格式一

   ```
   jQueryObject.load( url [, data ] [, complete ] )
   ```

#### 6.3、参数

| 参数       | 描述                                  |
| -------- | ----------------------------------- |
| url      | String类型请求的目标URL字符串。                |
| data     | 可选/String/Object类型发送请求传递的数据。        |
| complete | 可选/Function类型请求完成(无论成功或失败)后执行的回调函数。 |

#### 6.4、示例代码

1. 加载静态HTML页面

   ```
   data.html
   <div >
       <p id="content">加载HTML文档数据,使用其中匹配选择器的元素内容来替换每个匹配元素的内容</p>
   </div>
   //load.html
   <div id="load">
       111111
   </div>
   //将data.html
    $(function () {
   	$("#load").load("data.html");
   });
   ```

   ```
    $(function () {
    	$("#load").load("data.html");
       });

   $(function () {
        //使用其中id为#content的内容添加到id为#load的子元素
       $("#load").load("data.html #content");
   });
   ```

## 四、工具方法

### 2、serialize()

#### 2.1、说明

> 用于提交的有效表单控件的name和value，将它们拼接为一个可直接用于表单提交的文本字符串，该字符串已经过标准的URL编码处理(字符集编码为UTF-8)。
>
> 该函数不会序列化不需要提交的表单控件，这和常规的表单提交行为是一致的。
>
> 1. 不在\<form>标签内的表单控件不会被提交、
> 2. 没有name属性的表单控件不会被提交、
> 3. 带有disabled属性的表单控件不会被提交、
> 4. 没有被选中的表单控件不会被提交

#### 2.2、语法格式

1. 格式一

   ```
   var  text = jQueryObject.serialize()
   ```

#### 2.3、示例代码

1. 将form表单的内容转化成String

   ```
    $(function () {
               $("#btn").click(function () { //uid=1&username=%E5%82%BB%E6%A0%B9&password=123456&grade=1&sex=1&star=1&star=2&star=3&star=4
                   console.log($("#form_id").serialize());
               });
           });

   <form id="form_id" >
       <input name="uid" type="hidden" value="1"/>
       <input name="username" type="text" value="傻根"/>
       <input name="password" type="text" value="123456"/>
       <select name="grade" id="grade">
           <option value="1" selected="selected">Java</option>
           <option value="2">H5</option>
           <option value="3">IOS</option>
           <option value="4">Android</option>
           <option value="5">PHP</option>
           <option value="6">Python</option>
       </select>
       <input name="sex" type="radio" checked="checked" value="1"/>男
       <input name="sex" type="radio" value="0"/>女
       <input name="star" type="checkbox" checked="checked" value="1"/>赵丽颖
       <input name="star" type="checkbox" checked="checked" value="2"/>杨幂
       <input name="star" type="checkbox" value="3"/>苍井空
       <input name="star" type="checkbox" value="4"/>小明
       <input name="btn" id="btn" type="button" value="提交"/>
   ```

2. 提交部分数据

   ```
    $(function () {
               $("#btn").click( function(){
    
                   $.post( "/register" ,$( $(":text, select, :checkbox").serialize()).serialize(),
                       function( data, textStatus, jqXHR ){
                       alert( "AJAX提交成功!" );
                   });
    
               } );
    
           });
   ```

### 3、serializeArray()

#### 2.1、说明

> 该函数会将**可用于提交**的每个表单控件封装成一个Object对象，该对象有name和value属性，对应该表单控件的name和value属性。然后将这些Object对象封装为一个数组并返回。
>
> 该函数不会序列化不需要提交的表单控件
>
> 1. 不在<form>标签内的表单控件不会被提交、
> 2. 没有name属性的表单控件不会被提交、
> 3. 带有disabled属性的表单控件不会被提交、
> 4. 没有被选中的表单控件不会被提交

#### 2.2、语法格式

1. 格式一

   ```
   jQueryObject.serializeArray( )
   ```

#### 2.3、示例代码

1. 将form表单的内容转化成数组

   ```
   <form id="form_id" >
       <input name="uid" type="hidden" value="1"/>
       <input name="username" type="text" value="傻根"/>
       <input name="password" type="text" value="123456"/>
       <select name="grade" id="grade">
           <option value="1" selected="selected">Java</option>
           <option value="2">H5</option>
           <option value="3">IOS</option>
           <option value="4">Android</option>
           <option value="5">PHP</option>
           <option value="6">Python</option>
       </select>
       <input name="sex" type="radio" checked="checked" value="1"/>男
       <input name="sex" type="radio" value="0"/>女
       <input name="star" type="checkbox" checked="checked" value="1"/>赵丽颖
       <input name="star" type="checkbox" checked="checked" value="2"/>杨幂
       <input name="star" type="checkbox" value="3"/>苍井空
       <input name="star" type="checkbox" value="4"/>小明
       <input name="btn" id="btn" type="button" value="提交"/>
   ```

2. 提交部分数据

   ```
    $(function () {
               $("#btn").click( function(){
               /*
                  [
                       { name: "uid", value: "1" },
                       { name: "username", value: "shagen" },
                       { name: "password", value: "123456" },
                       { name: "grade", value: "1" },
                       { name: "sex", value: "1" },
                       { name: "star", value: "1" },
                       { name: "star", value: "2" }
                   ]
                */
                   $.post( "/register" ,$( $(":text, select, :checkbox").serializeArray(),
                       function( data, textStatus, jqXHR ){
                       alert( "AJAX提交成功!" );
                   });
    
               } );
    
           }); 
   ```

## 六、 什么是跨域

### 1、 域名地址的组成：

1. http:// www . google : 8080 / index.html
2. http:// （协议号）
3. www  （子域名）
4. google （主域名）
5. 8080 （端口号）
6. /index.html （请求的地址）

> 当协议、子域名、主域名、端口号中任意一个不相同时，都算不同的“域”。
>
> 不同的域之间相互请求资源，就叫“跨域”。
>
> 比如：http://www.werner.com/index.html 请求 http://www.bbbb.com/index.html的数据 

### 2、为什么不能跨域请求

> 这是因为基于安全的考虑，AJAX只能访问本地的资源，而不能跨域访问。
>
> 比如说你的网站域名是google.com，想要通过AJAX请求baidu.com域名中的内容，浏览器就会认为是不安全的，所以拒绝访问

|  编号  | url                                      | 说明           | 是否允许通信 |
| :--: | ---------------------------------------- | ------------ | ------ |
|  1   | http://www.werner.com/index.html                                                    http://www.werner.com/home.html | 同一域名下        | 允许     |
|  2   | http://www.werner.com/index.html                                                    http://www.werner.com/admin/home.html | 同一域名不同文件夹    | 允许     |
|  3   | http://www.werner.com:8090/index.html                                             http://www.werner.com:8080/index.html | 同一域名不同端口号    | 不允许    |
|  4   | http://www.werner.com:8000/index.html                                             https://www.werner.com:8080/index.html | 同一域名不同协议     | 不允许    |
|  5   | http://www.werner.com:8090/index.html                                             http://www.werner.com:8080/index.html | 域名与域名对应的ip地址 | 不允许    |
|  6   | http://mail.werner.com:8090/index.html                                             http://www.werner.com:8080/index.html | 主域名相同，子域名不同  | 不允许    |
|  7   | http://mail.werner.com:8000/index.html                                             http://www.test.com:8080/index.html | 不同域名         | 不允许    |

### 3、如何解决跨域问题

#### 3.1、JSONP(常用)

1. 什么是JSONP？

   > JSONP是英文JSON with Padding的缩写，是一个非官方的协议。它允许在服务器端生成script tags返回至客户端，通过javascript callback的形式来实现站点访问。 JSONP是一种script tag的注入，将server返回的response添加到页面实现特定功能

2. 实现步骤

   > 1、首先在客户端注册一个callback, 然后把callback的名字传给服务器。此时，服务器先生成 JSON数据。然后以JavaScript 语法的方式，生成一个function, function名字就是传递上来的参数jsonp. 
   >
   > 2、将JSON数据直接以入参的方式，放置到function中，这样就生成了一段 js 语法的文档，返回给客户端。 
   >
   > 在客户端浏览器中解析script标签，并执行返回的JavaScript文档，此时数据作为参数，传入到了客户端预先定义好的回调函数里(动态执行回调函数) 。

3. 示例代码

   ```
   <!DOCTYPE html>  
   <html>  
   <head>  
       <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">  
       <title>Insert title here</title>  
       <script type="text/javascript" src="resource/js/jquery-1.7.2.js"></script>  
       <script type="text/javascript">  
       $(function(){     
           /*  
           //简写形式，效果相同  
           $.getJSON("http://app.example.com/base/json.do?sid=1494&busiId=101&jsonpCallback=?",  
                   function(data){  
                       $("#showcontent").text("Result:"+data.result)  
           });  
           */  
           $.ajax({  
               type : "get",  
               async:false,  
               url : "http://app.example.com/base/json.do?sid=1494&busiId=101",  
               dataType : "jsonp",//数据类型为jsonp  
               jsonp: "jsonpCallback",//服务端用于接收callback调用的function名的参数  
               success : function(data){  
                   $("#showcontent").text("Result:"+data.result)  
               },  
               error:function(){  
                   alert('fail');  
               }  
           });   
       });  
       </script>
   </head>  
       <body>  
           <div id="showcontent">Result:</div>  
       </body>  
   </html>
   ```

   ```
       public void doGet(HttpServletRequest request,HttpServletResponse response) {  
          try {  
           response.setContentType("text/plain");  
           response.setHeader("Pragma", "No-cache");  
           response.setHeader("Cache-Control", "no-cache");  
           response.setDateHeader("Expires", 0);  
           Map<String,String> map = new HashMap<String,String>();   
           map.put("result", "content");  
           PrintWriter out = response.getWriter();       
           JSONObject resultJSON = JSONObject.fromObject(map); //根据需要拼装json  
           String jsonpCallback = request.getParameter("jsonpCallback");//客户端请求参数   
         } catch (IOException e) {  
          e.printStackTrace();  
         }  
       }  
   ```

#### 3.2、CORS(常用)

1. 概要

   > CORS是一个W3C标准，全称是"跨域资源共享"（Cross-origin resource sharing）。
   >
   > 它允许浏览器向跨源服务器，发出XMLHttpRequest请求，从而克服了AJAX只能同源使用的限制


#### 3.3、代理请求方式(了解)

#### 3.4、JSONP和CORS区别

> 1. JSONP只能实现GET请求，而CORS支持所有类型的HTTP请求。  
> 2. 使用CORS，开发者可以使用普通的XMLHttpRequest发起请求和获得数据，比起JSONP有更好的错误处理。  
> 3. JSONP主要被老的浏览器支持，它们往往不支持CORS，而绝大多数现代浏览器都已经支持了CORS

跨域问题常见的错误

1. 问题一

   1、异常信息

   ```
   No 'Access-Control-Allow-Origin' header is present on the requested resource,
   The response had HTTP status code 404
   ```

   2、解决方案

   ```
   1>本次ajax请求是“非简单请求”,所以请求前会发送一次预检请求(OPTIONS)
   2>服务器端后台接口没有允许OPTIONS请求,导致无法找到对应接口地址
   ```

2. 问题二

   1、异常信息

   ```
   No 'Access-Control-Allow-Origin' header is present on the requested resource,
   status 200
   ```
   2、 解决方案

   ```
   后端增加对应的头部添加 
   response.setHeader("Access-Control-Allow-Origin ", "*"); 
   ```

