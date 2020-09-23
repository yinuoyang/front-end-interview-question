
# Questions:

## [html] html的元素有哪些（包含H5）？ What are the elements in html?
> Answer:
> ### 行内元素：
> * a
> * b
> * span
> * strong
> * i
> * em
> * button
> * input
> * label
> * br
> * textarea
> * select
> 
> ### 块元素
> * div
> * p
> * h1-h6
> * ol
> * ul
> * li
> * table
> * tbody
> * td
> * tr
> * thead
> * dl
> * dt
> * dd
> 
> ### H5新增元素
> * section
> * article
> * audio
> * video
> * hearder
> * footer
> * small


## [js] 写一个方法去掉字符串中的空格. Write a function to remove the space in stirng
> Answer:
```javascript
var trim = function(str){
return str.replace(/\s*/g,"");
}
str.replace(/\s*/g,""); //去除字符串内所有的空格
str.replace(/^\s*|\s*$/g,""); //去除字符串内两头的空格
str.replace(/^\s*/,""); //去除字符串内左侧的空格
str.replace(/(\s*$)/g,""); //去除字符串内右侧的空格
```

## [html] What is the differences between link and @import? link 和 @ import的区别是什么？

>Answer:
>>- 1. link is the html tag, @ import is introduced by css.
>>- 2. The css introduced by link loaded when page loaded. @import load after the page loaded.
>>- 3. link does not have the  problem of compatblity where as @import only support ie5 ^.
>>- 4. link can use js to change its css by use DOM manipulation. @import can't

## [css] CSS3有哪些新增的特性？What's the new feature in css3?

> Answer
> ### 边框(borders):
> * border-radius 圆角
> * box-shadow  盒阴影
> * border-image 边框图像
> 
> ### 背景:
> * background-size 背景图片的尺寸
> * background_origin 背景图片的定位区域
> * background-clip 背景图片的绘制区域
> 
> ### 渐变：
> * linear-gradient 线性渐变
> * radial-gradient 径向渐变
> 
> ### 文本效果;
> * word-break
> * word-wrap
> * text-overflow
> * text-shadow
> * text-wrap
> * text-outline
> * text-justify
> 
> ### 转换：
> * 2D转换属性
> * transform
> * transform-origin
> * 2D转换方法
> * translate(x,y)
> * translateX(n)
> * translateY(n)
> * rotate(angle)
> * scale(n)
> * scaleX(n)
> * scaleY(n)
> * rotate(angle)
> * matrix(n,n,n,n,n,n)
> 
> ### 3D转换：
> *3D转换属性：
> 
> * transform
> * transform-origin
> * transform-style
> * 3D转换方法
> * translate3d(x,y,z)
> * translateX(x)
> * translateY(y)
> * translateZ(z)
> * scale3d(x,y,z)
> * scaleX(x)
> * scaleY(y)
> * scaleZ(z)
> * rotate3d(x,y,z,angle)
> * rotateX(x)
> * rotateY(y)
> * rotateZ(z)
> * perspective(n)
> 
> ### 过渡
> * transition
> 
> ### 动画
> * @Keyframes规则
> * animation
> 
> ### 弹性盒子(flexbox)
> ### 多媒体查询@media



##  圣杯布局和双飞翼布局的理解和区别

> Answer
>> 作用：圣杯布局()和双飞翼布局()解决的问题是一样的，就是两边顶宽，中间自适应的三栏布局，中间栏要在放在文档流前面以优先渲染。
>> 区别：圣杯布局，为了中间div内容不被遮挡，将中间div设置了左右padding-left和padding-right后，将左右两个div用相对布局position: relative并分别配合right和left属性，以便左右两栏div移动后不>> 遮挡中间div。双飞翼布局，为了中间div内容不被遮挡，直接在中间div内部创建子div用于放置内容，在该子div里用margin-left和margin-right为左右两栏div留出位置。
>> 圣杯布局代码：
```html
<body>
<div id="hd">header</div>
<div id="bd">
  <div id="middle">middle</div>
  <div id="left">left</div>
  <div id="right">right</div>
</div>
<div id="footer">footer</div>
</body>

<style>
#hd{
    height:50px;
    background: #666;
    text-align: center;
}
#bd{
    /*左右栏通过添加负的margin放到正确的位置了，此段代码是为了摆正中间栏的位置*/
    padding:0 200px 0 180px;
    height:100px;
}
#middle{
    float:left;
    width:100%;/*左栏上去到第一行*/
    height:100px;
    background:blue;
}
#left{
    float:left;
    width:180px;
    height:100px;
    margin-left:-100%;
    background:#0c9;
    /*中间栏的位置摆正之后，左栏的位置也相应右移，通过相对定位的left恢复到正确位置*/
    position:relative;
    left:-180px;
}
#right{
    float:left;
    width:200px;
    height:100px;
    margin-left:-200px;
    background:#0c9;
    /*中间栏的位置摆正之后，右栏的位置也相应左移，通过相对定位的right恢复到正确位置*/
    position:relative;
    right:-200px;
}
#footer{
    height:50px;
    background: #666;
    text-align: center;
}
</style>
```
双飞翼布局代码：
```html
<body>
<div id="hd">header</div> 
  <div id="middle">
    <div id="inside">middle</div>
  </div>
  <div id="left">left</div>
  <div id="right">right</div>
  <div id="footer">footer</div>
</body>

<style>
#hd{
    height:50px;
    background: #666;
    text-align: center;
}
#middle{
    float:left;
    width:100%;/*左栏上去到第一行*/     
    height:100px;
    background:blue;
}
#left{
    float:left;
    width:180px;
    height:100px;
    margin-left:-100%;
    background:#0c9;
}
#right{
    float:left;
    width:200px;
    height:100px;
    margin-left:-200px;
    background:#0c9;
}

/*给内部div添加margin，把内容放到中间栏，其实整个背景还是100%*/ 
#inside{
    margin:0 200px 0 180px;
    height:100px;
}
#footer{  
   clear:both; /*记得清楚浮动*/  
   height:50px;     
   background: #666;    
   text-align: center; 
} 
</style>
```
## [js]用递归算法实现，数组长度为5且元素的随机数在2-32间不重复的值. use recursion to have an array length 5 and array has no-repeat number between 2 and 32.

>Answer:
```javascript
var arr = new Array[5];
var randomNum = randomNumber();
var i = 0;
randomArr(arr, num);

function randomArr(arr, num){
    if(arr.indexOf(num) < 0){
        arr[i] = num;
        i++;
    } else {
        num = randomNum;
    }
    if( i > arr.length){
        console.log(arr);
        return;
    } else {
        randomArr(arr,num)
    }

}

function randomNum(){
    return Math.floor(Math.random()*31 + 2);
}
```