# jQuery动画

一 、概述

jQuery提供了一组方法用于为HTML元素制作简单的动画效果。这些动画的方法都是根据实际动画效果来命名的，它们分别是：

show(),hide(),toggle(),slideDown(),slideUp(),slideToggle(),fadeIn(),fadeOut(),fadeToggle(),fadeTo(),animate()

## 二 、show()

### 1、作用

> 方法用于显示隐藏的元素。如果选择的元素是可见的，这个方法将不会改变任何东西。无论这个元素是通过hide()方法隐藏的还是在CSS里设置了display:none;，这个方法都将有效。



### 2、语法

​	show([speed,[easing],[fn]])                           

### 3、参数：

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

### 4、示例代码

1. 示例一

   ```
   $('#img').show();   
   注:在对元素使用show()方法之前，该元素必须是处于隐藏状态，否则不会有任何效果。要隐藏一个元素可以通过hide()方法或通过CSS样式。
   <img id="img" style="display: none" src="..." />      
   ```

2. 示例二

   ```
   show()方法的第一个参数是显示元素的动画速度，可以是三个预置的字符串或一个整数数值。
   $('#img').show('slow');
   $('#img').show('normal');
   $('#img').show('fast');
   $('#img').show(2000);  
   ```

3. 示例三

   ```
   第3个参数是一个可选的回调函数，它在元素被完全显示后执行。
   $('#img').show(function(){ alert('shown');} );
   $('#img').show(2000, function(){ alert('shown');} );                            
   hide()
   hide()方法用于隐藏元素。如果选择的元素是隐藏的，这个方法将不会改变任何东西。
   hide()方法的语法为：
   hide([speed,[easing],[fn]])                          
   参数：
   speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
   easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
   fn：在动画完成时执行的函数，每个元素执行一次。
   例如下面的代码隐藏div元素。
   $('#img').hide();
   $('#img').hide('slow');
   $('#img').hide('normal');
   $('#img').hide('fast');
   $('#img').hide(2000);                            
   也可以在元素被完全隐藏之后执行一个回调函数。
   $('#img').hide(function(){ alert('shown');} );
   $('#img').hide(2000, function(){ alert('shown');} );  
   ```

## 三、toggle()

### 1、作用

> 切换一个元素的可见性。如果元素是可见的，切换为隐藏的；如果元素是隐藏的，切换为可见的。

### 2、语法

​	toggle([speed],[easing],[fn])

### 3、参数

1. speed： 隐藏/显示 效果的速度。默认是 "0"毫秒。可能的值：slow，normal，fast。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

### 4、示例代码

1. 示例一

   ```
   $('#div').toggle();
   $('#div').toggle('slow');
   $('#div').toggle('normal');
   $('#div').toggle('fast');
   $('#div').toggle(2000);  
   ```

2. 示例二

   ```
   也可以在元素的状态被切换之后执行一个回调函数。
   $('#div').toggle(function(){ alert('shown');} );
   $('#div').toggle(2000, function(){ alert('shown');} );   
   ```

## 四、slideDown()

### 1、作用

> 通过高度变化（向下增大）来动态地显示所有匹配的元素，在显示完成后可选地触发一个回调函数。这个动画效果只调整元素的高度，可以使匹配的元素以“滑动”的方式显示出来。

### 2、语法

​	slideDown([speed],[easing],[fn])                            

### 3、参数

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

4、示例代码

1. div元素向下滑动显示

   ```
   $('#div').slideDown();
   $('#div').slideDown('slow');
   $('#div').slideDown('normal');
   $('#div').slideDown('fast');
   $('#div').slideDown(2000); 
   ```

2. 元素向下滑动显示完成之后执行一个回调函数

   ```
   $('#div').slideDown(function(){ alert('done');} );
   $('#div').slideDown(2000, function(){ alert('done');} );      
   ```

## 五、slideUp()

### 1、作用

> 通过高度变化（向上减小）来动态地隐藏所有匹配的元素，在隐藏完成后可选地触发一个回调函数。这个动画效果只调整元素的高度，可以使匹配的元素以“滑动”的方式显示出来。

### 2、语法

​	slideUp([speed],[easing],[fn])                            

### 3、参数

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

4 示例代码

1. 向上滑动显示。

   ```
   $('#div').slideUp();
   $('#div').slideUp('slow');
   $('#div').slideUp('normal');
   $('#div').slideUp('fast');
   $('#div').slideUp(2000);   
   ```

2. 向上滑动显示完成之后执行一个回调函数

   ```
   $('#div').slideUp(function(){ alert('done');} );
   $('#div').slideUp(2000, function(){ alert('done');} ); 
   ```

## 六、slideToggle()

### 1、作用

> 通过高度变化来切换所有匹配元素的可见性，并在切换完成后可选地触发一个回调函数。这个动画效果只调整元素的高度，可以使匹配的元素以“滑动”的方式显示出来。

### 2、语法

​	slideToggle(speed [,easing ,fn])

### 3、参数

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

4、示例代码

1. 滑动的发生切换div元素的可见性

   ```
   $('#div').slideToggle();
   $('#div').slideToggle('slow');
   $('#div').slideToggle('normal');
   $('#div').slideToggle('fast');
   $('#div').slideToggle(2000);    
   ```

2. 元素向上滑动显示完成之后执行一个回调函数

   ```
   $('#theDiv').slideToggle(function(){ alert('done');} );
   $('#theDiv').slideToggle(2000, function(){ alert('done');} );  
   ```

   ​

   ​

## 七、fadeIn()

### 1、作用

> 通过不透明度的变化来实现所有匹配元素的淡入效果，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。

### 2、语法

​	fadeIn([speed],[easing],[fn])                            

### 3、参数

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

### 4、示例代码

1. 淡入的方式显示div元素

   ```
   $('#div').fadeIn();
   $('#div').fadeIn('slow');
   $('#div').fadeIn('normal');
   $('#div').fadeIn('fast');
   $('#div').fadeIn(2000);   
   ```

2. 元素淡入显示完成之后执行一个回调函数

   ```
   $('#theDiv').fadeIn(function(){ alert('done');} );
   $('#theDiv').fadeIn(2000, function(){ alert('done');} );  
   ```

## 八、fadeOut()

### 1、作用

> 通过不透明度的变化来实现所有匹配元素的淡出效果，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。

### 2、语法

fadeOut([speed],[easing],[fn])                           

### 3、参数

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

### 4、参数

1. 以淡出的方式隐藏div元素。

   ```
   $('#div').fadeOut();
   $('#div').fadeOut('slow');
   $('#div').fadeOut('normal');
   $('#div').fadeOut('fast');
   $('#div').fadeOut(2000);  
   ```

2. 淡出隐藏完成之后执行一个回调函数。

   ```
   $('#div').fadeOut(function(){ alert('done');} );
   $('#div').fadeOut(2000, function(){ alert('done');} );      
   ```

## 九、fadeToggle()

### 1、作用

> fadeToggle()方法通过不透明度的变化来开关所有匹配元素的淡入和淡出效果，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。

### 2、语法

​	fadeToggle([speed],[easing],[fn])                           

### 3、参数

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
3. fn：在动画完成时执行的函数，每个元素执行一次。

### 4、示例代码

1. 以淡入淡出的方式显示和隐藏div元素

   ```
   $('#div').fadeToggle();
   $('#div').fadeToggle('slow');
   $('#div').fadeToggle('normal');
   $('#div').fadeToggle('fast');
   $('#div').fadeToggle(2000);   
   ```

2. 元素淡入淡出显示和隐藏完成之后执行一个回调函数

   ```
   $('#div').fadeToggle(function(){ alert('done');} );
   $('#div').fadeToggle(2000, function(){ alert('done');} );                          
   ```

## 十、 fadeTo()

### 1、作用

> 把所有匹配元素的不透明度以渐进方式调整到指定的不透明度，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。

### 2、语法

​	fadeTo([[speed],opacity,[easing],[fn]])                          

### 3、参数

1. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
2. opacity：一个0至1之间表示透明度的数字。
3. easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
4. fn：在动画完成时执行的函数，每个元素执行一次。

### 4、示例代码

1. 以动画的方式将div元素的透明度设置为0.5

   ```
   $('#div').fadeTo(0.5);
   $('#div').fadeTo('slow', 0.5);
   $('#div').fadeTo('normal', 0.5);
   $('#div').fadeTo('fast', 0.5);
   $('#div').fadeTo(2000, 0.5);    
   ```

2. 元素透明动画完成之后执行一个回调函数

   ```
   $('#div').fadeTo(0.5, function(){ alert('done');} );
   $('#div').fadeTo(2000, 0.5, function(){ alert('done');} );   
   ```

## 十一、animate()

### 1、作用

> 用于创建自定义动画的函数。
>
> 这个函数的关键在于指定动画形式及结果样式属性对象。这个对象中每个属性都表示一个可以变化的样式属性（如“height”、“top”或“opacity”）。注意：所有指定的属性必须用骆驼形式，比如用marginLeft代替margin-left。
> 不是所有的属性都可以被动画，下面列出了一些可以被动画的属性。
> borderWidth,width,height,fontSize,opacity,margin,padding,bottom,left,right,top,wordSpacing

### 2、语法

> animate(params,[speed],[easing],[fn])

### 3、参数

1. params：一组包含作为动画属性和终值的样式属性和及其值的集合。
2. speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
3. easing：要使用的擦除效果的名称(需要插件支持).默认jQuery提供"linear" 和 "swing"。
4. fn：在动画完成时执行的函数，每个元素执行一次。

### 4、示例代码

1. 示例一

   ```
   $('#div').animate({"height" : 300}, 'slow');
   $('#div').animate({"width"  : 200}, 'slow');                            
   你可以一次动画多个属性：
   $('#div').animate({"height" : 250, width:250 }, 'slow');                            
   你还可以在动画结束之后执行一个回调函数。
   $('#div').animate({"width" : 200}, 'slow',
   function(){
   	alert('done'); 
   }); 
   ```

2. 示例二

   ```
   在animate()方法中你也可以执行toggle动画。
   如果你对width属性执行toggle操作，那么宽度首先会变为0，然后宽度在变回原来的值。
   $('#div').animate({"width"  : 'toggle'}, 'slow' );                      
   ```