 

# Ajax

# 一、什么是Ajax

> AJAX = 异步 JavaScript 和 XML。
>
> AJAX 是一种用于创建快速动态网页的技术。
>
> 通过在后台与服务器进行少量数据交换，AJAX 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。
>
> 传统的网页（不使用 AJAX）如果需要更新内容，必需重载整个网页面

# 二、Ajax的原生写法

### 1、XMLHttpRequest对象

> XMLHttpRequest 对象用于在后台与服务器交换数据，能够在不重新加载页面的情况下更新网页，在页面已加载后从服务器请求数据，在页面已加载后从服务器接收数据，在后台向服务器发送数据。所以**XMLHttpRequest对象是Ajax技术的核心所在**

### 2、 执行步骤

1. 流程图

   ![](http://opzv089nq.bkt.clouddn.com/17-9-4/73927704.jpg)

2. 工作流程

   > 1、创建兼容性XHR对象 → 2、初始化请求 →3 、发送请求 → 4、接收数据 → 5、解析数据 → 6、完成

## 三、流程详解

### 1、创建兼容性XHR对象

1. XMLHttpRequest对象兼容IE7+，Chrome，FireFox等浏览器。如果不需要兼容IE7以下版本的浏览器，直接使用XMLHttpRequest构造函数即可

   ```
   var xhr = new XMLHttpRequest();
   ```

2. 在IE7以下版本的浏览器中对这个对象是采用ActiveX插件的方式来实现的。在IE浏览器中可能会遇到三种不同版本的XHR对象，即MSXML2.XMLHttp,MSXML2.XMLHttp.3.0,MSXML2.XMLHttp.6.0，要使用MSXML库中的XHR对象的话

   ```
   var xhr = new ActiveXObject('Microsoft.XMLHttp');
   ```

3. 完整代码

   ```
   function getXHR(){
       var xhr = null;
       try{
           xhr = new XMLHttpRequest();
       }catch(e){
           xhr = new ActiveXObject('Microsoft.XMLHttp');
       }
       return XHR;
   }
   ```

### 2、设置回调函数

1. 通过XMLHttpRequest对象的onreadystatechange属性设置回调函数，用于当请求成功后接收服务器端返回的数据

   ```
   xhr.onreadystatechange=function()
           case 0 :
               //alert("请求未初始化");
               break; 
           case 1 :
               //alert("请求启动，尚未发送");
               break;
           case 2 :
               //alert("请求发送，尚未得到响应");
               break;
           case 3 : 
               //alert("请求开始响应，收到部分数据");
               break;
           case 4 :
               alert("请求响应完成得到全部数据");
               if((xhr.status >= 200 && xhr.status < 300) || xhr.status == 304) {
                   var  data = xhr.responseText;
                   alert(data);
               }else {
                   alert("Request was unsuccessful : " + xhr.status + " " + xhr.statusText);
               }
               break;
     }
   ```

2. 常用的属性说明

   1、readyState状态信息

   > | 状态码  |      说明      |
   > | :--: | :----------: |
   > |  0   |    请求未初始化    |
   > |  1   |   服务器连接已建立   |
   > |  2   |    请求已接收     |
   > |  3   |    请求处理中     |
   > |  4   | 请求已完成，且响应已就绪 |

   2、 responseText 作为响应主体被返回的文本

​	responseText属性返回从服务器接收到的字符串，该属性为只读。如果本次请求没有成功或者数据不完整，该属性就会等于null。如果服务器返回的数据格式是JSON，就可以使用responseText属性。

​	var data = ajax.responseText;
​	data = JSON.parse(data);

   4、statusText 响应HTTP状态

> | 状态码  |    说明    |
> | :--: | :------: |
> | 200  | 服务器正常响应  |
> | 400  |  错误的请求   |
> | 403  |  没有访问权限  |
> | 404  | 请求的资源不存在 |
> | 500  | 服务器内部错误  |

### 3、初始化对象

1. 通过XMLHttpRequest对象的open()方法，传入参数完成初始化XMLHttpRequest对象的工作

   ```
   xhr.open('GET','url');
   xhr.open('POST','url');
   ```

2. 说明

   - method	

     Http请求方式，选择发送Http get 请求，因此参数为get，支持get跟post请求

   - url

     要请求服务器的url路径

   - async

     是否以异步的方式发送，true为异步，false为同步，默认为true

     同步：会停留并等待服务器发送回复然后再继续

     ```
       /* 开发中不要使用同步 */
         var xhr = new XMLHttpRequest();
         console.log("1、实例化");
         xhr.onreadystatechange = function () {
             if (xhr.readyState === 4 && xhr.status === 200) {
                 console.log("4、请求数据完成");
                 console.log(this.responseText);
             }
         };
         console.log("2、监听设置完成");
         xhr.open("GET", "/web/ajax", false);
         console.log("3、初始化配置!!!");
         xhr.send();
         console.log("5、请求发送完成!!!");
     ```

     异步：允许页面继续其进程并处理可能的回复

     ```
        var xhr = new XMLHttpRequest();
         console.log("1、实例化");
         xhr.onreadystatechange = function () {
             if (xhr.readyState === 4 && xhr.status === 200) {
                 console.log("5、请求数据完成");
                 console.log(this.responseText);
             }
         };
         console.log("2、监听设置完成");
         xhr.open("GET", "/web/ajax", true);
         console.log("3、初始化配置!!!");
         xhr.send();
         console.log("4、请求发送完成!!!");
     ```

### 4、发送请求

#### 1、概要

> send方法用于实际发出HTTP请求。如果不带参数，就表示HTTP请求只包含头信息，也就是只有一个URL，典型例子就是GET请求；如果带有参数，就表示除了头信息，还带有包含具体数据的信息体，典型例子就是POST请求。

#### 2、参数

> 1、void send();
>
> 2、void send(String data);
>
> 3、void send(FormData data);
>
> 4、void send(ArrayBufferView data);
>
> 5、void send(Blob data);
>
> 6、void send(Document data);

#### 3、参数详解

##### 1、FormData

1. 构造表单数据

   ```
   var formData = new FormData();
   formData.append('username', '张三');
   formData.append('email', 'zhangsan@163.com');
   var xhr = new XMLHttpRequest();
   xhr.open("POST", "/register");
   xhr.send(formData);
   ```

   上面的代码构造了一个formData对象，然后使用send方法发送。它的效果与点击下面表单的submit按钮是一样的。

   ```
   <form id='register' name='register' action='/register'>
          <input type='text' name='username' value='张三'>
          <input type='email' name='email' value='zhangsan@163.com'>
          <input type='submit'>
      </form>   
   ```

2. 现有表单构造生成

   ```
   var form = document.querySelector("form");
   var request = new XMLHttpRequest();
   request.open("POST", "/rigesiter");
   request.send(new FormData(form));
   ```

3. FormData对象还可以对现有表单添加数据

   ```
   function sendForm(form) {
          var formData = new FormData(form);
          var xhr = new XMLHttpRequest();
          xhr.open('POST', "/rigester", true);
          xhr.onload = function(e) {
              // ...
          };
          xhr.send(formData);
          return false;
      }
      var form = document.querySelector('#register');
      sendForm(form);
   ```

4.  FormData对象也能用来模拟File控件，进行文件上传。

   ```
   function uploadFiles(url, files) {
        var formData = new FormData();
        for (var i = 0, file; file = files[i]; ++i) {
          formData.append(file.name, file); // 可加入第三个参数，表示文件名
        }
        var xhr = new XMLHttpRequest();
        xhr.open('POST', url, true);
        xhr.onload = function(e) { ... };
        xhr.send(formData);  // multipart/form-data
      }
      document.querySelector('input[type="file"]').change(function() {
        uploadFiles('/upload', this.files);
        return false;
      });
   ```



##### 2、String

1. 传递键值对

   ```
   function getData(url) {
        var formData = new FormData();
        for (var i = 0, file; file = files[i]; ++i) {
          formData.append(file.name, file); // 可加入第三个参数，表示文件名
        }
        var xhr = new XMLHttpRequest();
        xhr.open('POST', url);
        xhr.onload = function(e) { ... };
        xhr.send("uid=1");  //application/x-www-form-urlencoded
      }
   ```

2. 传递多个键值对

   ```
   function getData(url) {
        var formData = new FormData();
        for (var i = 0, file; file = files[i]; ++i) {
          formData.append(file.name, file); // 可加入第三个参数，表示文件名
        }
        var xhr = new XMLHttpRequest();
        xhr.open('POST', url);
        xhr.onload = function(e) { ... };
        xhr.send("page=1&size=10");  //application/x-www-form-urlencoded
      }
   ```

   ​















