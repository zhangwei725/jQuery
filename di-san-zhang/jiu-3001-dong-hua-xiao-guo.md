 show()
show()方法用于显示隐藏的元素。如果选择的元素是可见的，这个方法将不会改变任何东西。无论这个元素是通过hide()方法隐藏的还是在CSS里设置了display:none;，这个方法都将有效。
show()方法的语法为：
show([speed,[easing],[fn]])                           
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如显示一张隐藏的图片。
$('#theImg').show();                           
在对元素使用show()方法之前，该元素必须是处于隐藏状态，否则不会有任何效果。要隐藏一个元素可以通过hide()方法或通过CSS样式。
<img id="theDiv" style="display: none" src="..." />                            
show()方法的第一个参数是显示元素的动画速度，可以是三个预置的字符串或一个整数数值。
$('#theImg').show('slow');
$('#theImg').show('normal');
$('#theImg').show('fast');
$('#theImg').show(2000);                            
第3个参数是一个可选的回调函数，它在元素被完全显示后执行。
$('#theImg').show(function(){ alert('shown');} );
$('#theImg').show(2000, function(){ alert('shown');} );                            
 hide()
hide()方法用于隐藏元素。如果选择的元素是隐藏的，这个方法将不会改变任何东西。
hide()方法的语法为：
hide([speed,[easing],[fn]])                          
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码隐藏div元素。
$('#theDiv').hide();
$('#theDiv').hide('slow');
$('#theDiv').hide('normal');
$('#theDiv').hide('fast');
$('#theDiv').hide(2000);                            
也可以在元素被完全隐藏之后执行一个回调函数。
$('#theDiv').hide(function(){ alert('shown');} );
$('#theDiv').hide(2000, function(){ alert('shown');} );                            
 toggle()
toggle()方法用于切换一个元素的可见性。如果元素是可见的，切换为隐藏的；如果元素是隐藏的，切换为可见的。
toggle()方法的语法为：
toggle([speed],[easing],[fn])                        
参数：
speed： 隐藏/显示 效果的速度。默认是 "0"毫秒。可能的值：slow，normal，fast。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码切换div元素的可见性：
$('#theDiv').toggle();
$('#theDiv').toggle('slow');
$('#theDiv').toggle('normal');
$('#theDiv').toggle('fast');
$('#theDiv').toggle(2000);                            
也可以在元素的状态被切换之后执行一个回调函数。
$('#theDiv').toggle(function(){ alert('shown');} );
$('#theDiv').toggle(2000, function(){ alert('shown');} );                           
 slideDown()
slideDown()方法通过高度变化（向下增大）来动态地显示所有匹配的元素，在显示完成后可选地触发一个回调函数。这个动画效果只调整元素的高度，可以使匹配的元素以“滑动”的方式显示出来。
slideDown()方法的语法为：
slideDown([speed],[easing],[fn])                            
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码使div元素向下滑动显示。
$('#theDiv').slideDown();
$('#theDiv').slideDown('slow');
$('#theDiv').slideDown('normal');
$('#theDiv').slideDown('fast');
$('#theDiv').slideDown(2000);                           
也可以在元素向下滑动显示完成之后执行一个回调函数。
$('#theDiv').slideDown(function(){ alert('done');} );
$('#theDiv').slideDown(2000, function(){ alert('done');} );                            
 slideUp()
slideUp()方法通过高度变化（向上减小）来动态地隐藏所有匹配的元素，在隐藏完成后可选地触发一个回调函数。这个动画效果只调整元素的高度，可以使匹配的元素以“滑动”的方式显示出来。
slideUp()方法的语法为：
slideUp([speed],[easing],[fn])                            
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码使div元素向上滑动显示。
$('#theDiv').slideUp();
$('#theDiv').slideUp('slow');
$('#theDiv').slideUp('normal');
$('#theDiv').slideUp('fast');
$('#theDiv').slideUp(2000);                           
你也可以在元素向上滑动显示完成之后执行一个回调函数。
$('#theDiv').slideUp(function(){ alert('done');} );
$('#theDiv').slideUp(2000, function(){ alert('done');} );                         
 slideToggle()
slideToggle()方法通过高度变化来切换所有匹配元素的可见性，并在切换完成后可选地触发一个回调函数。这个动画效果只调整元素的高度，可以使匹配的元素以“滑动”的方式显示出来。
slideToggle()方法的语法为：
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码以滑动的发生切换div元素的可见性。
$('#theDiv').slideToggle();
$('#theDiv').slideToggle('slow');
$('#theDiv').slideToggle('normal');
$('#theDiv').slideToggle('fast');
$('#theDiv').slideToggle(2000);                           
你也可以在元素向上滑动显示完成之后执行一个回调函数。
$('#theDiv').slideToggle(function(){ alert('done');} );
$('#theDiv').slideToggle(2000, function(){ alert('done');} );                       
 fadeIn()
fadeIn()方法通过不透明度的变化来实现所有匹配元素的淡入效果，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。
fadeIn()方法的语法为：
fadeIn([speed],[easing],[fn])                            
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码以淡入的方式显示div元素。
$('#theDiv').fadeIn();
$('#theDiv').fadeIn('slow');
$('#theDiv').fadeIn('normal');
$('#theDiv').fadeIn('fast');
$('#theDiv').fadeIn(2000);                            
你也可以在元素淡入显示完成之后执行一个回调函数。
$('#theDiv').fadeIn(function(){ alert('done');} );
$('#theDiv').fadeIn(2000, function(){ alert('done');} );                            
 fadeOut()
fadeOut()方法通过不透明度的变化来实现所有匹配元素的淡出效果，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。
fadeOut()方法的语法为：
fadeOut([speed],[easing],[fn])                           
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码以淡出的方式隐藏div元素。
$('#theDiv').fadeOut();
$('#theDiv').fadeOut('slow');
$('#theDiv').fadeOut('normal');
$('#theDiv').fadeOut('fast');
$('#theDiv').fadeOut(2000);                            
你也可以在元素淡出隐藏完成之后执行一个回调函数。
$('#theDiv').fadeOut(function(){ alert('done');} );
$('#theDiv').fadeOut(2000, function(){ alert('done');} );                         
 fadeToggle()
fadeToggle()方法通过不透明度的变化来开关所有匹配元素的淡入和淡出效果，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。
fadeToggle()方法的语法为：
fadeToggle([speed],[easing],[fn])                           
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码以淡入淡出的方式显示和隐藏div元素。
$('#theDiv').fadeToggle();
$('#theDiv').fadeToggle('slow');
$('#theDiv').fadeToggle('normal');
$('#theDiv').fadeToggle('fast');
$('#theDiv').fadeToggle(2000);                           
你也可以在元素淡入淡出显示和隐藏完成之后执行一个回调函数。
$('#theDiv').fadeToggle(function(){ alert('done');} );
$('#theDiv').fadeToggle(2000, function(){ alert('done');} );                       
 fadeTo()
fadeTo()方法把所有匹配元素的不透明度以渐进方式调整到指定的不透明度，并在动画完成后可选地触发一个回调函数。这个动画只调整元素的不透明度，也就是说所有匹配的元素的高度和宽度不会发生变化。
fadeToggle()方法的语法为：
fadeTo([[speed],opacity,[easing],[fn]])                          
参数：
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
opacity：一个0至1之间表示透明度的数字。
easing：可选参数，用来指定切换效果，默认是"swing"，可用参数"linear"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如下面的代码以动画的方式将div元素的透明度设置为0.5。
$('#theDiv').fadeTo(0.5);
$('#theDiv').fadeTo('slow', 0.5);
$('#theDiv').fadeTo('normal', 0.5);
$('#theDiv').fadeTo('fast', 0.5);
$('#theDiv').fadeTo(2000, 0.5);                            
你也可以在元素透明动画完成之后执行一个回调函数。
$('#theDiv').fadeTo(0.5, function(){ alert('done');} );
$('#theDiv').fadeTo(2000, 0.5, function(){ alert('done');} );                            
 animate()
animate()方法是用于创建自定义动画的函数。
这个函数的关键在于指定动画形式及结果样式属性对象。这个对象中每个属性都表示一个可以变化的样式属性（如“height”、“top”或“opacity”）。注意：所有指定的属性必须用骆驼形式，比如用marginLeft代替margin-left。
不是所有的属性都可以被动画，下面列出了一些可以被动画的属性。
borderWidth
width
height
fontSize
opacity
margin
padding
bottom
left
right
top
wordSpacing
等等.....
animate()方法的语法为：
animate(params,[speed],[easing],[fn])                          
参数：
params：一组包含作为动画属性和终值的样式属性和及其值的集合。
speed：三种预定速度之一的字符串("slow","normal", or "fast")或表示动画时长的毫秒数值(如：1000)。
easing：要使用的擦除效果的名称(需要插件支持).默认jQuery提供"linear" 和 "swing"。
fn：在动画完成时执行的函数，每个元素执行一次。
例如：
$('#theDiv').animate({"height" : 300}, 'slow');
$('#theDiv').animate({"width"  : 200}, 'slow');                            
你可以一次动画多个属性：
$('#theDiv').animate({"height" : 250, width:250 }, 'slow');                            
你还可以在动画结束之后执行一个回调函数。
$('#theDiv').animate({"width"  : 200}, 'slow',

    function(){ alert('done'); 
});                            
在animate()方法中你叶可以执行toggle动画。例如，如果你对width属性执行toggle操作，那么宽度首先会变为0，然后宽度在变回原来的值。
$('#theDiv').animate({"width"  : 'toggle'}, 'slow' );                            