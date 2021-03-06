## 选择器

## 一、概要

> 使用jQuery 选择器选取元素，并封装为jQuery对象
>
> 在JS原生DOM中，我们想要对DOM元素进行操作，首先得获取到对应的元素(getElementById()、 getElementsByTagName()等)，然后再对这些元素进行操作。
>
> 同样的，jQuery也需要先选取所需的DOM元素，然后再针对这些元素进行操作。

## 二、基础选择器

### 1、ID选择器

1. 语法格式: $('#id Name')

2. 示例代码

   ```
   <script type="text/javascript">
   	$(function() {
   		//通过id找到元素。注意返回的jquery对象
   		var $box = $("#box");
   	})
   </script>
   ```

   ```
   <body>
   	<div id="box">这个是p标签</div>
   </body>
   ```

### 2、标签选择器

1. 语法格式: $('标签名')

2. 示例代码

   ```
   <body>
   	<p>这个是p标签</p>
   </body>
   ```

   ```
   var $p = $("p");
   ```

### 3、类选择器

1. 语法格式:

2. 示例代码

   ```
   <body>
   	<div class="div"></div>
   </body>
   ```

   ```
   var $div = $(".div");
   ```

### 4、组合选择器(并集)

1. 语法格式: $('id|class|标签,id|class|标签')

2. 示例代码

   ```
   <div>
       <div class="div1">
           <H4 id="title"></H4>
           <H4 class="cls2"></H4>
       </div>

       <div class="div2">
           <p class="cls1"></p>
           <p class="cls2"></p>
       </div>

       <p></p>
   </div>
   <div>
   ```

   ```
        $(function () {
               var $elements = $(".cls1,.cls2,#title,p");
               $elements.text("测试一下");
           });
   ```

### 5、通配符选择器（遍历所有元素）

1. 语法格式 : $(“*”)

2. 示例代码

   ```
   $(function () {
           // 遍历所有元素，将字体颜色设置为红色
           $('*').css('color', '#FF0000');
   });
   ```

### 6、标签+类选择器

1. ##### 语法格式:  $('标签.类选择器')

2. ##### 示例代码

   ```
   <div>
       <div class="div1">
           <H4 id="title"></H4>
           <H4 class="cls2"></H4>
       </div>

       <div class="div2">
           <p class="cls1"></p>
           <p class="cls2"></p>
       </div>
       <p></p>
   </div>
   <div>
   ```

   ​

   ```
      $(function () {
               var $elements = $("p.cls2");
               $elements.text("测试一下");
       });
   ```

## 三、层级选择器

### 1 、后代选择器(所有子元素)

1. ##### 语法格式:  $('div p')

2. ##### 示例代码

   ```
   <div>
       <h4>第一个列表</h4>
       <ul>
           <li></li>
           <li> </li>
           <li><a href="">这个有点屌啊</a> </li>
           <li> </li>
       </ul>
       <h4>第二个列表</h4>
       <ul>
           <li></li>
           <li></li>
           <li></li>
           <li></li>
       </ul>
   </div>
   ```

   ```
           $(function () {
   //            返回9个元素  8个li标签  1个a标签
               var $li_cate = $("div ul *");
               $li_cate.text("层级选择器")
           });
   ```

### 2、子类选择器(直接子元素)

1. 语法格式: $('div>p')

2. 示例代码

   ```
       <ul class="parent">
           <li></li>
           <li></li>
           <li>
                <ul class="child">
                   <li></li>
                   <li></li>
               </ul>
           </li>
           <li></li>
       </ul>
   ```

   ```
       $(function () {
       	//返回四个li标签
               var $li = $(".parent > li");
           });
   ```

### 3、相邻的元素

1. 语法格式:

   - 当前元素后面所有指定的兄弟 -- $('div ~ p')     等价于$('div').nextAll('p')
   - 当前元素后面所有的兄弟  -- $('div ~ *')      
   - 当前元素后面紧挨的第一个指定兄弟 -- $('.div2 + p')  等价于$('.div').next('p')
   - 当前元素前面所有指定的兄弟 -- $('div').prevAll('p')
   - 当前元素前面紧挨的指定兄弟 -- $('div').prev('p')
   - 当前元素的所有兄弟元素 -- siblings()

2. 示例代码

   ```
   <div style="background: red; width: 100px; height: 100px ">
       <div class="div1">
           <H4 id="title">1</H4>
           <H4 class="cls2">1</H4>
       </div>

       <div class="div2">
           <p class="cls1">1</p>
           <p class="cls2">1</p>
       </div>
       <p></p>
       <p></p>
   </div>
   <div style="background: yellow; width: 100px; height: 100px ">
   </div>
   <p></p>
   ```

   ```
      $(function () {
                  var $div1 = $("div ~ p");
                  $div1.text("当前元素后面所有指定的兄弟")
          });
   ```

   ​

   ​

## 四、过滤选择器

### 1、基本过滤器

1. ##### 语法格式:

   - 选取第一个元素  -- :first 或者 .first()
   - 选取最后一个元素  -- :last 或者 .last()
   - 选取所有偶数个元素 -- :even
   - 选取所有奇数个元素 -- :odd
   - 选取对象，然后从中剔除相应元素 -- :not(selector)
   - 选取所有的h1...h6元素—:header
   - 根据索引来选取元素
     ​	等于索引 -- :eq(index)
     ​	小于索引 -- :lt(index)
     ​	大于索引 -- :gt(index)

2. ##### 示例代码

   ```
    <ul class="parent">
           <li>0</li>
           <li>1</li>
           <li>2</li>
           <li>3</li>
    </ul> 
   ```

   ```
   1. 基本过滤器-选取第一个元素
           $(function () {
               //var $first = $("ul>li").first();
               //等同于
               var $first = $("li:first");
               $first.text("基本过滤器,获取第一个子元素");
               //运行结构改变<li>0</li>的内容被改变<li>基本过滤器,第一个子元素</li>
           });
   2. 基本过滤器-选取最后一个元素
   	    $(function () {
               //var $last = $("ul>li").last();
               //等同于
               var $first = $("li:last");
               $first.text("基本过滤器,获取最后一个子元素");
               //运行结构改变<li>3</li>的内容被改变<li>基本过滤器,取最后一个子元素</li>
           });   
   3. 基本过滤器-取所有偶数个数的元素
      $(function () {

               var $li_even = $("ul > li:even");
               $li_even.text("获取所有偶数个数");
               // <li>0</li> <li>2</li> 的内容被改变
           });       
   4. 基本过滤器-
      $(function () {
               var $li_even = $("ul > li:odd");
               $li_even.text("获取所有偶数个数");
               // <li>1</li> <li>3</li> 的内容被改变
           });       
   5. 基本过滤器-取所有奇数个数的元素
      $(function () {
               var $li_even = $("ul > li:odd");
               $li_even.text("取所有奇数个数的元素");
               // <li>1</li> <li>3</li> 的内容被改变
           });       
   6    基本过滤器-索引来选取元素
   	$(function () {
               var $li_even = $("ul > li:eq(0)");
               $li_even.text("通过索引来获取元素");
               //<li>0</li> 被修改
           });
   ```

### 2、属性过滤器

1. 语法格式: [attribute]（取拥有attribute属性的元素）

   - 取attribute属性值等于value或不等于value的元素[attribute = value]和[attribute != value]（）
   - 选择开头 -- [**attribute ^= value**]
   - 选择结束 -- **[attribute $= value]**
   - 选择通用匹配 -- **[attribute *= value]**
   - **复合型属性过滤器，同时满足多个条件**  [selector1] selector2]

2. 示例代码

   ```
   <body>
   <ul>
       <li><a href="#" title="t1" class="t1">title=t1 和 class = t1</a></li>
       <li><a href="#" title="t1" class="t2">title=t1 和 class = t2</a></li>
       <li><a href="#" title="t2" class="t3">title=t2 和 class = t3</a></li>
       <li><a href="#" title="t3" class="t4">title=t3 和 class = t4</a></li>
       <li><a href="#" title="ti7" class="t5">title=t4 和 class = t5</a></li>
       <li><a href="#" class="item">其他</a></li>
   </ul>
   </body>
   ```

   ```
   1.取拥有title属性的元素
   $(function () {
      $("a[title]").text("有title属性的全部给我改!!!!")
      //除了a标签是其他的其他的内容都会改变
   });
   2.取title属性值等于t1
   $(function () {
       $("a[title=t1]").text("有title属性的t1全部给我改!!!!")
       //前面两个a标签改变
   });
   3.取title属性值不等于t1的元素
   $(function () {
      $("a[title!=t1]").text("有title属性的值不等于 t1 全部给我改!!!!")
       //除前面两个a标签其他都会改变
   });
   4.选择通用匹配
   $(function () {
       $("a[title*=ti7]").text("有title属性的值包含t全部给我改!!!!")
      //倒数第二项被改变
      //必须是连续,不能ti17 这样是配配不上的
    });
   5复合型属性过滤器，同时满足多个条件
   $(function () {
      $("[href][class=item]").text("多匹配");
      //最后一项被改变
   });
    
   ```

3. 在属性选择器中，^$符号和正则表达式的开始结束符号表示的含义是一致的，*模糊匹配，类似于sql中的like '%t%'

### 3、表单选择器与过滤器

1. 选择器

   - 语法格式:

     - $(":input")                   选择所有的表单输入元素，包括input, textarea, select 和 button
     - $(":text")                     选择所有的text input元素
     - $(":password")           选择所有的password input元素
     - $(":radio")                   选择所有的radio input元素
     - $(":checkbox")           选择所有的checkbox input元素
     - $(":submit")                选择所有的submit input元素
     - $(":image")                 选择所有的image input元素
     - $(":reset")                   选择所有的reset input元素
     - $(":button")                选择所有的button input元素
     - $(":file")                       选择所有的file input元素
     - $(":hidden")                选择所有类型为hidden的input元素或表单的隐藏域

   - ##### 示例代码

     ```
     <form action="" method="post" enctype="application/x-www-form-urlencoded">
         <input type="hidden" name="jsessionid" value="我是隐藏的">
         <input type="text"><br>
         <input type="password"><br>
         主修技术选择:<br>
         <input type="radio" name="course" value="java">JAVA<br>
         <input type="radio" name="course" value="php">PHP<br>
         <input type="radio" name="course" value="h5">H5<br>
         <input type="radio" name="course" value="android">Android<br>
         <input type="radio" name="course" value="ios">IOS<br>
         选修技术选择<br>
         <input type="checkbox" name="cbox1" value="java">JAVA<br>
         <input type="checkbox" name="cbox2">PHP <br>
         <input type="checkbox" name="cbox3">H5<br>
         <input type="checkbox" name="cbox4">Android<br>
         <input type="checkbox" name="cbox4" value="ios">IOS<br>
         选择上传的文件:<input type="file" accept="image/*" name="file" multiple="multiple"> <br>
         <textarea cols="40" rows="10">   </textarea><br>

         <label>选择:
             <select name="date_select">
                 <optgroup label="第一个">
                     <option value="1">1</option>
                     <option value="2">2</option>
                     <option value="3">3</option>
                     <option value="4">4</option>
                     <option value="5">5</option>
                 </optgroup>
                 <!--默认选择第一项  如果想改变设置 selected="selected"-->
                 <option selected="selected" value="10">10</option>
                 <option value="20">20</option>
                 <option value="30">30</option>
                 <option value="40">40</option>
                 <option value="50">50</option>
             </select>
         </label><br>
         <input type="reset" name="重置">
         <input type="submit" name="提交">
     </form>
     ```

     ```
      
      1.取input,textarea,select,button元素
     $(function () {
        //选择所有的input标签
       // $("input").css("padding", "10px");
         // 取input,textarea,select,button元素
        $(":input").css("padding", "10px");

      });
       //选择所有的input type=text属性的标签
      $(function () {
      
       $(":text").height("500px");
      });
      
      //
        $(function () {
         $(":button").click(function () {
           var $checked = $(":checkbox").length;
           alert($checked);
         });
     });
      
     ```

     ```
       jquery操作复选框常用操作
         1、获取单个checkbox选中项(三种写法)
         $("input:checkbox:checked").val()
         或者
         $("input:[type='checkbox']:checked").val();
         或者
         $("input:[name='ck']:checked").val();
         2、 获取多个checkbox选中项
          var $checks = $("input:checkbox:checked");
                       $checks.each(function () {
                           var val = $(this).val();
                       })
         3、设置第一个checkbox 为选中值
         $('input:checkbox:first').attr("checked",'checked');
         或者
         $('input:checkbox').eq(0).attr("checked",'true');
         4、设置最后一个checkbox为选中值
         $('input:radio:last').attr('checked', 'checked');
         或者
         $('input:radio:last').attr('checked', 'true');
         5、根据索引值设置任意一个checkbox为选中值
         $('input:checkbox).eq(索引值).attr('checked', 'true');索引值=0,1,2....
         或者
         $('input:radio').slice(1,2).attr('checked', 'true');
         6、选中多个checkbox同时选中第1个和第2个的checkbox
         $('input:radio').slice(0,2).attr('checked','true');
         7、根据Value值设置checkbox为选中值
         $("input:checkbox[value='1']").attr('checked','true');
         8、删除Value=1的checkbox
         $("input:checkbox[value='1']").remove();
         9、删除第几个checkbox
         $("input:checkbox").eq(索引值).remove();索引值=0,1,2....
         如删除第3个checkbox:
         $("input:checkbox").eq(2).remove();
         10、遍历checkbox
         $('input:checkbox').each(function (index, domEle) {
         //写入代码
         });
         11、全部选中
         $('input:checkbox').each(function() {
                 $(this).attr('checked', true);
         });
         12、全部取消选择
         $('input:checkbox').each(function () {
                 $(this).attr('checked',false);
         });
     ```

2. ##### 过滤器

   1. ##### 语法格式

      - $(":enabled")              选择所有的可操作的表单元素
      - $(":disabled")             选择所有的不可操作的表单元素
      - $(":checked")             选择所有的被checked的表单元素
      - $("select option:selected") 选择所有的select 的子元素中被selected的元素

   2. ##### 示例代码

      ```
      <form action="" method="post" enctype="application/x-www-form-urlencoded">
          <input type="hidden" name="jsessionid" value="我是隐藏的">
          <!--disabled 属性无法与 <input type="hidden"> 一起使用-->
          <input type="text" name="able" disabled="disabled" value="不想说话"><br>
          <input type="text"><br>
          <input type="password"><br>
          主修技术选择:<br>
          <input type="radio" name="course" value="java">JAVA<br>
          <input type="radio" name="course" value="php">PHP<br>
          <input type="radio" name="course" value="h5">H5<br>
          <input type="radio" name="course" value="android">Android<br>
          <input type="radio" name="course" value="ios">IOS<br>
          选修技术选择<br>
          <input type="checkbox" name="cbox1" value="java">JAVA<br>
          <input type="checkbox" name="cbox2">PHP <br>
          <input type="checkbox" name="cbox3">H5<br>
          <input type="checkbox" name="cbox4">Android<br>
          <input type="checkbox" name="cbox4" value="ios">IOS<br>
          选择上传的文件:<input type="file" accept="image/*" name="file" multiple="multiple"> <br>
          <textarea cols="40" rows="10">   </textarea><br>

          <label>选择:
              <select name="date_select">
                  <optgroup label="第一个">
                      <option value="1">1</option>
                      <option value="2">2</option>
                      <option value="3">3</option>
                      <option value="4">4</option>
                      <option value="5">5</option>
                  </optgroup>
                  <!--默认选择第一项  如果想改变设置 selected="selected"-->
                  <option selected="selected" value="10">10</option>
                  <option value="20">20</option>
                  <option value="30">30</option>
                  <option value="40">40</option>
                  <option value="50">50</option>
              </select>
          </label><br>
          <input type="reset" name="重置">
          <input type="button" name="btn" value="提交btn">
          <input type="submit" name="提交">
      </form>
      ```

      ```
      $(function () {
             $(":button").click(function () {
              var $checked = $("input[type=checkbox]");
              alert($checked.length);
            });
       });
      ```

### 4、可见性过滤器

1. 语法格式 

   - 选取所有不可见元素 -- :hidden    
     - 表单元素type="hidden"    
     - 设置样式display:none  
     - 设置样式宽高为0：width:0；height:0    
     - 父元素隐藏，子元素也是隐藏的
   - 选取所有可见元素 -- :visable

2. 示例代码

   ```
   <style type="text/css">
           div
           {
               margin: 10px;
               width: 200px;
               height: 40px;
               border: 1px solid #FF0000;
               display:block;
           }
           .hid-1
           {
               display: none;
           }
           .hid-2
           {
               visibility: hidden;
           }
       </style>

   <body>
       <div class="hid-1">display: none</div>
       <div class="hid-2">visibility: hidden</div>
       <input type="hidden" value="hello"/>
       <div>可见的元素</div>
   </body>
   ```

   ```
    $(function() {
               $('div:hidden').show(1000);
               alert($('input:hidden').val());
     });
     
   $(function() {
     $('div:visible')..css('background', '#BBB);   
   });
    
   ```

3. jQuery至1.3.2之后的:hidden选择器仅匹配display:none或<input type="hidden" />的元素，而不匹配visibility: hidden或高宽:0的元素,hidden只匹配那些“隐藏的”并且不占空间的元素

### 5、内容过滤

1. 语法格式

   - 过滤出包含给定文本的元素。(innerText中包含) -- :contains(text)
   - 过滤出所有不包含子元素或者文本的空元素  -- :empty
   - 过滤出元素中包含（即子元素中）selector选择器能选择到的元素 -- :has(selector)
   - 过滤出可以当做父元素的元素（即该元素有子元素或者元素中包含文本。） -- :parent

2. 示例代码

   ```
   <dl>
       <dt>技术</dt>
       <dd>JAVA PHP,H5,Android,IOS</dd>
       <dt>SEO</dt>
       <dd>关键字排名</dd>
       <dt>其他</dt>
       <dd></dd>
   </dl>

   <div>
       <p>测试<span> has </span>过滤</p>
   </div>

   <ol>
       <li></li>
       <li>parent（取包含子元素或文本的元素</li>
       <li></li>
       <li></li>
   </ol>
   ```

3. 过滤出所有不包含子元素或者文本的空元素

   ```
   $(function () {
              $('dd:empty').html('没有内容');
   });
   ```


1. 过滤出元素中包含（不是直系子元素也会生效）selector选择器能选择到的元素

   ```
      $(function () {
   	$("div:has(span)")
   	.css("border", "1px solid black");
      });
   ```

2. 取包含子元素或文本的元素

   ```
   $(function () {
      $('ol li:parent').css('border', '1px solid #000');
   });
   ```

### 6、总结

1. 基本过滤选择

   | 选择器        | 说明              | 返回   |
   | ---------- | --------------- | ---- |
   | :first     | 匹配找到的第1个元素      | 单个元素 |
   | :last      | 匹配找到的最后一个元素     | 单个元素 |
   | :eq        | 匹配一个给定索引值的元素    | 单个元素 |
   | :even      | 匹配所有索引值为偶数的元素   | 集合元素 |
   | : odd      | 匹配所有索引值为奇数的元素   | 集合元素 |
   | :gt(index) | 匹配所有大于给定索引值的元素  | 集合元素 |
   | :lt(index) | 匹配所有小于给定索引值的元素  | 集合元素 |
   | :not       | 去除所有与给定选择器匹配的元素 | 集合元素 |
   | :animated  | 选取当前正在执行动画的所有元素 | 集合元素 |
   | focus      | 选取当前正在获取焦点的元素   | 集合元素 |

2. 内容过滤选择器

   | 选择器             | 描述               | 返回   |
   | --------------- | ---------------- | ---- |
   | :contains(text) | 选取含有文本内容为text的元素 | 集合元素 |
   | :empty          | 选取不包含子元素获取文本的空元素 | 集合元素 |
   | :has(selector)  | 选择含有选择器所匹配的元素的元素 | 集合元素 |
   | :parent         | 选取含有子元素或者文本的元素   | 集合元素 |

3. 可见过滤选择器

   | 选择器      | 描述         | 返回   |
   | -------- | ---------- | ---- |
   | :hidden  | 选择所有不可见的元素 | 集合元素 |
   | :visible | 选取所有可见的元素  | 集合元素 |

4. 属性过滤选择器

   | 选择器               | 说明                | 返回   |
   | ----------------- | ----------------- | ---- |
   | [attribute]       | 选取拥有此属性的元素        | 集合元素 |
   | [attribute=value] | 选取属性值为value值的元素   | 集合元素 |
   | [attribue^=value] | 选取属性的值以value开始的元素 | 集合元素 |
   | [attribue$=value] | 选取属性的值以value结束的元素 | 集合元素 |

5. 子元素过滤选择器

   | 选择器                        | 说明                                   | 返回   |
   | -------------------------- | ------------------------------------ | ---- |
   | :nth-child(index/even/odd) | 选取每个父元素下的第index个子元素或者奇偶元素（index从1算起） | 集合元素 |
   | :first-child               | 选取每个元素的第一个子元素                        | 集合元素 |
   | :last-child                | 选取每个元素的最后一个子元素                       | 集合元素 |

   - :nth-child()选择器是很常用的子元素过滤选择器，如下
     - :nth-child(even)选择每个父元素下的索引值是偶数的元素
     - :nth-child(odd)选择每个父元素下的索引值是奇数的元素
     - :nth-child(2)选择每个父元素下的索引值是2的元素
     - :nth-child(3n)选择每个父元素下的索引值是3的倍数的元素 (n从1开始)

6. 表单对象属性过滤选择器**

   | 选择器       | 说明                  | 返回   |
   | --------- | ------------------- | ---- |
   | :enabled  | 选取所有可用元素            | 集合元素 |
   | :disabled | 选取所有不可用元素           | 集合元素 |
   | :checked  | 选取所有被选中的元素（单选框、复选框） | 集合元素 |
   | :selected | 选取所有被选中的元素（下拉列表）    | 集合元素 |

7. 表单选择器

   | 选择器       | 说明                                 |
   | --------- | ---------------------------------- |
   | :input    | 选取所有input textarea select button元素 |
   | :text     | 选取所有单行文本框                          |
   | :password | 选取所有密码框                            |
   | :radio    | 选取所有单选框                            |
   | :checkbox | 选取所有多选框                            |
   | :submit   | 选取所有的提交按钮                          |
   | :image    | 选取所有的图像按钮                          |
   | :reset    | 选取所有的重置按钮                          |
   | :button   | 选取所有的按钮                            |
   | :file     | 选取所有的上传域                           |
   | :hidden   | 选取所有的不可见元素                         |

## 五、优化原则

1. 尽量ID选择器。其背后机理其实是调用原生的document.getElementById()，所以速度较其他选择器快。

2. 使用类选择器时表指定元素的类型。不信你看这个性能比较

   ```
   var $products = $("div.products"); // 慢
   var $products = $(".products"); // 快
   ```

3. ID父亲容器下面再查找子元素请用.find()方法。这样做快的原因是通过id选择元素不会使用Sizzle引擎(选择器查询底层算法)

4. 多级查找中，右边尽量指定得详细点而左边则尽量简单点

   ```
   $(".data td.gonzalez");
   ```


1. 避免冗余。

   ```
   $(".data table.attendees td.gonzalez");
   好的方式：去掉了中间的冗余
   $(".data td.tb");

   $(".data td.gonzalez");
   ```


1. 指定选择的上下文。

   ```
    // 劣质的代码：因为需要遍历整个DOM来找到.class
    $('.class');
    // 高品代码：因为只需在指定容器范围内进行查找
    $('.class', '#class-container');
   ```

2. 不要使用万能选择器

   ```
    $('div.container > *'); // 差
    $('div.container').children(); 
   ```

3. 警惕隐式的万能选择器。省略的情况下其实使用的就是*号通配符  

   ```
   $('div.someclass :radio'); // 差
   $('div.someclass input:radio'); // 棒
   ```

4. ID已经表示唯一了，背后使用的是document.getElementById()，
   所以表跟其他选择器混搭了。

   ```
   $('#outer #inner'); // 脏

   $('div#inner'); // 乱

   $('.outer-container #inner'); // 差

   $('#inner'); // 干净利落，后台只需调用document.getElementById()
   ```