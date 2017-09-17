## jQuery之Ajax

### 一、什么是 AJAX？

```
AJAX = 异步 JavaScript 和 XML（Asynchronous JavaScript and XML）。

简短地说，在不重载整个网页的情况下，AJAX 通过后台加载数据，并在网页上进行显示。

使用 AJAX 的应用程序案例：谷歌地图、腾讯微博、优酷视频、人人网等等。
```

### 二、 方法总结

#### 1 、发送并处理AJAX请求的方法

| 方法            | 版本   | 描述                                       |
| ------------- | ---- | ---------------------------------------- |
| $.ajax()      | 1.0  | 全局方法发送并处理AJAX请求。这是jQuery底层的AJAX实现，包含处理AJAX请求所需的一切功能。其他发送AJAX请求的方法都是对该方法的进一步封装。 |
| $.get()       | 1.0  | 全局方法发送并处理GET方式的AJAX请求。                   |
| $.post()      | 1.0  | 全局方法发送并处理POST方式的AJAX请求。                  |
| $.getJSON()   | 1.0  | 全局方法发送并处理GET方式、返回数据为JSON格式的AJAX请求。       |
| $.getScript() | 1.0  | 全局方法发送GET请求，用于加载一个JS脚本文件。                |
| $.load()      | 1.0  | 全局方法发送AJAX请求，用于加载一个HTML文件并替换匹配元素中的内容。    |

#### 2 、辅助函数-发送或处理AJAX请求，简化AJAX操作

| 方法                     | 版本   | 描述                                       |
| ---------------------- | ---- | ---------------------------------------- |
| jQuery.ajaxPrefilter() | 1.5  | 全局方法在$.ajax()处理参数选项之前，预处理参数选项。           |
| jQuery.ajaxSetup()     | 1.1  | 全局方法设置$.ajax()的全局默认选项。                   |
| jQuery.param()         | 1.0  | 全局方法将JS数组或对象序列化为字符串，以便用于URL查询字符串或AJAX请求。 |
| serialize()            | 1.0  | 将表单元素序列化为字符串，以便用于URL查询字符串或AJAX请求。        |
| serializeArray()       | 1.2  | 将表单元素序列化为一个JS数组。                         |

#### 3 、事件方法-用于为AJAX事件绑定处理一个或多个函数

| ajaxComplete() | 1.0  | 设置当AJAX请求完成(无论成功或失败)时执行的处理函数。 |
| -------------- | ---- | ----------------------------- |
| ajaxSuccess()  | 1.0  | 设置当AJAX请求成功时执行的处理函数。          |
| ajaxError()    | 1.0  | 设置当AJAX请求失败时执行的处理函数。          |
| ajaxStart()    | 1.0  | 设置当前第一个AJAX请求开始时执行的处理函数。      |
| ajaxSend()     | 1.0  | 设置在AJAX请求被发送前执行的处理函数。         |
| ajaxStop()     | 1.0  | 设置当前最后一个AJAX请求结束时执行的处理函数      |

### 三、Ajax使用

#### 5.2.1、 load() 方法





#### 5.2.2、  ajax方法

1. 完整格式:

   ```
   $.ajax({
   	//ajax请求地址
       url: "home?method=catedata",  
       //(默认: true,dataType为script和jsonp时默认为false)设置为 false 将不缓存此页面，建议使用默认
       cache: false,
       //请求方式 "POST" 或 "GET"， 默认为 "GET"。注意：其它 HTTP 请求方法，如 PUT 和 DELETE 也可以使用，但仅部分浏览器支持。
       type:"GET",
       dataType:"json",    //根据返回数据类型可以有这些类型可选：xml html script json jsonp text
       //发送到服务器的数据，可以直接传对象{a:0,b:1}，如果是get请求会自动拼接到url后面，如：&a=0&b=1
       //如果为数组，jQuery 将自动为不同值对应同一个名称。如 {key:["value1", "value2"]} 转换为 "&key=value1&key=value2"。
       data:{},
       //发送请求前可修改 XMLHttpRequest 对象的函数，如添加自定义 HTTP 头。XMLHttpRequest 对象是唯一的参数。这是一个 Ajax 事件。如果返回false可以取消本次ajax请求。
       beforeSend:function(xhr){
           //this 默认为调用本次AJAX请求时传递的options参数
       },
       //context这个对象用于设置ajax相关回调函数的上下文。也就是说，让回调函数内this指向这个对象（如果不设定这个参数，那么this就指向调用本次AJAX请求时传递的options参数）。
       //比如指定一个DOM元素作为context参数，这样就设置了success回调函数的上下文为这个DOM元素。
       context: document.body,
       //请求成功后的回调函数
       success: function(data,textStatus){
           //this 调用本次AJAX请求时传递的options参数 ,如果设置context来改变了this，那这里的this就是改变过的
       },
       //请求失败时调用此函数。有以下三个参数：XMLHttpRequest 对象、错误信息、（可选）捕获的异常对象。
       //如果发生了错误，错误信息（第二个参数）除了得到null之外，还可能是"timeout", "error", "notmodified" 和 "parsererror"。
       error：function(XMLHttpRequest, textStatus, errorThrown){
           // 通常 textStatus 和 errorThrown 之中
           // 只有一个会包含信息
           // this 调用本次AJAX请求时传递的options参数
       },
       //请求完成后回调函数 (请求成功或失败之后均调用)。参数： XMLHttpRequest 对象和一个描述成功请求类型的字符串
       complete:function(XMLHttpRequest, textStatus) {
           //this 调用本次AJAX请求时传递的options参数
       },
       //一组数值的HTTP代码和函数对象，当响应时调用了相应的代码。例如，如果响应状态是404，将触发以下警报：
       statusCode:{
           404:function(){
               alert('404，页面不存在');
           }
       }
   });
   ```

2. 常用格式

   ```
   $.ajax({
        type: 'POST',
        url: url ,
        data: data ,
        success: success ,
        dataType: dataType
   });
   ```

3. 示例代码

   ```
     $.ajax({
         type: "GET",
         url: cate_data_url,
         dataType: 'json',
         success: function (data) {
         init_cate(data)
         }

       });
   		
   	function init_cate(data) {
             //操作数据      
   	}
   ```

#### 5.2.3、 get() 方法



#### 5.2.4、 post() 方法

1. 常用格式

   ```
   $.ajax({
       type: "POST",
       url: "/home",
       dataType:'json',//可以不写 框架自己也会判断
       data: {name:"xiaoming",sex:1},//也可以是字符串链接"name=xiaoming&sex=1"，建议用对象
       success: function(data){
           //实际操作的时候，返回的json对象中可能会有成功错误的判断标记，所以可能也需要判断一下
       }
   });
   ```

#### 5.2.5、 getJSON() 方法

#### 5.2.6、 getScript() 方法

#### 5.2.7、 form表单处理

```
  $("form").on("submit",function(){
        var url = this.action;   //可以直接取到表单的action
        var formData = $(this).serialize();//必须要写
        $.post(url,formData,
            function(data){
                //返回成功，可以做一个其他事情
            },'json');
        //阻止表单默认提交行为
        return false
    })	
```

#### 5.2.8、 什么是跨域

##### 5.2.7.1、 域名地址的组成：

http:// www . google : 8080 / index.html

　　http:// （协议号）

　　www  （子域名）

　　google （主域名）

　　 8080 （端口号）

　　/index.html （请求的地址）

 当协议、子域名、主域名、端口号中任意一各不相同时，都算不同的“域”。

不同的域之间相互请求资源，就叫“跨域”。

比如：http://www.werner.com/index.html 请求 http://www.bbbb.com/index.html的数据 

##### 5.2.7.1、为什么不能跨域请求

这是因为基于安全的考虑，AJAX只能访问本地的资源，而不能跨域访问。

比如说你的网站域名是google.com，想要通过AJAX请求yztc.com域名中的内容，浏览器就会认为是不安全的，所以拒绝访问

| 编号   | url                                      | 说明           | 是否允许通信 |
| ---- | ---------------------------------------- | ------------ | ------ |
| 1    | http://www.werner.com/index.html                                             http://www.werner.com/home.html | 同一域名下        | 允许     |
| 2    | http://www.werner.com/index.html                                             http://www.werner.com/admin/home.html | 同一域名不同文件夹    | 允许     |
| 3    | http://www.werner.com:8090/index.html                                             http://www.werner.com:8080/index.html | 同一域名不同端口号    | 不允许    |
| 4    | http://www.werner.com:8000/index.html                                             https://www.werner.com:8080/index.html | 同一域名不同协议     | 不允许    |
| 5    | http://www.werner.com:8090/index.html                                             http://www.werner.com:8080/index.html | 域名与域名对应的ip地址 | 不允许    |
| 6    | http://mail.werner.com:8090/index.html                                             http://www.werner.com:8080/index.html | 主域名相同，子域名不同  | 不允许    |
| 7    | http://mail.werner.com:8000/index.html                                             http://www.test.com:8080/index.html | 不同域名         | 不允许    |

