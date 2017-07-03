# WEB基础之CSS
---
#### 什么是CSS
CSS（层叠样式表）用来规定HTML文档的展现形式，调整颜色，背景，文字风格 等等……

#### 使用CSS的四种方法
```
一、使用style属性： 将style属性直接加在个别的元件标签里。 
    <td style="color:blue; font-size:9pt; font-family:"标楷体"; line-height:150%> 
    这种用法的优点是可灵巧应用样式于各标签中，但是缺点则是没有整篇文件的『统一性』。
 
二、使用style标签： 将样式规则写在<style>...</style>标签之中。 
    通常是将整个的 <style>...</style>结构写在网页的<head> </head>部份之中。这种用法的优点就是在于整篇文件的统一性，只要是有声明的的元件即会套用该样式规则。缺点就是在个别元件的灵活度不足。
    <div class="box"></div>  用.box{}来写样式
    <div id="box"></div>     用#box{}来写样式

三、使用link标签： 将样式规则写在.css的样式档案中，再以<link>标签引入。 
    假设我们把样式规则存成一个example.css的档案，我们只要在网页中加入 
    <link rel="stylesheet" type="text/css" hree="example.css"> 
    即可套用该样式档案中所制定好的样式了。 通常是将link标签写在网页的<head></head>部份之中。这种用法的优点就是在於可以把要套用相同样式规则的数篇文件都指定到同一个样式档案即可。
    缺点也是在个别文件或元件的灵活度不足。 

四、使用@import引入： 跟link用法很像，但必放在<style>...</style> 中。 
    <style type="text/css"> 
        @import url(http://yourweb/ example.css); 
    </style> 
```

#### CSS样式

```css
正常文档流：
    html是从什么方向开始显示元素的呢？ `从上到下 从左到右`，这叫正常文档流 

外边距：
    定义了元素与元素之间的距离。允许负数；
    内联元素：没有垂直方向的外边距，也没有宽高度。
    margin-top: 100px;          添加上外边距，允许为负值
    margin-right: 100px;        添加右外边距，允许为负值
    margin-bottom: 100px;       添加下外边距，允许为负值
    margin-left: 100px;         添加左外边距，允许为负值
    margin: 50px 0 100px 100px; 上 右 下 左；顺时针
    margin: 50px 100px 100px;   上 水平 下，中间一个代表左右各100px
    margin: 100px 100px;        垂直 水平
    margin: 100px;              4边都是100px

外边距重合：
    一个块级元素的下外边距，和下面一个块级元素的上外边距，只会应用一个外边距（谁的外边距大，就用谁的外边距）
    父盒子装子盒子，子盒子会与父盒子的上下边距重合
    当父盒子没有給【宽高】（width、height）的时候会被子元素撑开
    只有块级元素，垂直方向的外边距会发生重合（折叠）
    解决方法：
        1. 在父元素添加border: 1px solid transparent;  #transparent为透明颜色
        2. 或者在父元素添加overflow: hidden;  或  overflow: auto;   或   padding: 1px;
    
内边距：
    定义了内容和边框的距离。只能为正数；无法居中；比如长方形的长和宽不可能为负数；
    假如我想让一个盒子里面的内容距离盒子的左边有段距离：  
    1. 给盒子里面的内容套一个标签，然后使用`margin-left`  
    2. 在外边的大盒子直接给上内边距
    padding-top: 10px;        添加上内边距
    padding-right: 10px;      添加右内边距
    padding-bottom: 10px;     添加下内边距
    padding-left: 10px;       添加左内边距
    padding-left: 48%;
    padding: 参数;            上 右 下 左；上 水平 下；垂直 水平；4边；（注意：中间没逗号）

边框：
    border边框特点：会增大体积
    border-width: 10px;       边框宽10px
    border-color: red;        边框颜色
    border-style: solid;      边框风格：solid实线；dashed虚线；dotted点状；double双线；
    border-top: 5px solid white; 上边框，如事先未定义，则定义hover后鼠标滑上去会影响布局
    border-top-width: 10px;
    border-top-style: solid;
    border-top-color: red;
    border-right              右边框
    border-bottom             下边框
    border-left               左边框
    border: 1px solid red;    边框简写方式，盒子外套个1像素红色实线边框
    border: 1px solid transparent;  transparent完全透明
    border-collapse: collapse;  合并为一个单一的边框
    
圆角：
    border-radius: 4px;       圆角
    border-radius: 0 0 0 0;   左上角，右上角，右下角，左下角
    border-radius: 宽高的一半px；  假设宽=高，则变成圆
    border-radius: 50%;       把正方形变成圆形，正方体大于50%都是圆，不建议写100%
    border-radius: 164px 164px 164px 164px;
    border-top-left-radius: 75px;  左上角变圆弧
    border-bottom-right-radius: 75px;  右下角变圆弧 

边框制作三角形：
    /* CSS部分 */
    .box {
        width: 0;
        height: 0;
        border-top: 5px solid red;
        border-left: 5px dashed transparent;
        border-right: 5px dashed transparent;
    }
    <!--===== HTML部分 =====-->
    <div class="box"></div>

通配符*：
    * {margin: 0; padding: 0;}  
    * 表示选择所有的元素除了<!doctype>以外的元素
    为解决不同浏览器默认内外边距不同的问题，均初始化为0；企业用专门的样式表：resetcss

CSS权重(子代选择器)：
    选择器谁多就应用谁的
    相同的选择器 样式也相同，则是由上到下应用样式
    id选择器 > class选择器 > 元素(标签)选择器
    id    吨
    class 千克
    标签  克

文本样式：
    文本颜色	  color: red;
    背景颜色	  background: red;
    字符间距 	  letter-spacing: 2em; 或 letter-spacing: 10px; 
    空格间距	  word-spacing: 6px
    行高     	    line-height: 14px;
    段落最小高度  min-height: 2em; 
    对齐方式  	  text-align: center/left/right;  可居中/左/右文字、内联元素、内联块
    文本缩进	  text-indent: 2em;  首字符缩进2个字体大小
    <!-- px:像素; em:相对单位，相对字的大小;  -->

装饰文本：
    text-decoration: overline;      上划线
    text-decoration: line-through;  中划线（删除线）
    text-decoration: underline;     下划线
    text-decoration: none;          去除划线，a标签默认包含下划线样式

字体样式：
    font-family: "微软雅黑";
    font-family: "楷体";      冲突则下面的覆盖上面的
    font-size: 30px;          字体大小为30像素
    font-weight: bold;        粗体，默认为400，可用normal代替;600-900加粗,可用bold代替；200-500默认状态；100变细；（100-300 细体；400-500 默认；600-900 粗体?）
    font-style: italic;       字体风格，倾斜    
    <!-- 样式相冲突的以最下面的为准 -->

背景属性:
    background: skyblue;           背景颜色：天空蓝
    background-color: skyblue;     背景颜色：天空蓝
    background: url();             背景图片：内填网址；带空格的图片名字需加""
    background-image: url('**.png'); 背景图片
    background-repeat: repeat-x;   背景填充，只重复x方向
    background-repeat: no-repeat;  背景填充，将重复部分去除
    <!-- repeat，以平铺的方式重复图像(默认x+y)；repeat-y，以y垂直(纵向)方向重复图像-->
    background: url() no-repeat 0 center;  合并简写方式，IE9以上才支持
    background-size: 200px 100px;  背景大小，前宽度后高度
    background-size: 100% 100%;    背景大小，扩展到整个屏幕，不能加在body元素上，可能不会生效
    background-size: 100%;         如果只设置一个值，则第二个值会被设置为 "auto"
    background-size: cover;        把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。背景图像的某些部分也许无法显示在背景定位区域中。
    background-position: 100px 0px;位移图片，背景定位X值 Y值，水平方向平移100像素，支持反方向，即"-100px"；
    <!-- 浏览器中调整位移，F12，先鼠标单击，然后方向键上下调整；ctrl+上下方向键可每下调整100像素，貌似不成功？ -->
    <!-- shift+上下方向键可每下调整10像素；alt+上下方向键可每下调整0.1像素 -->





color颜色：
所有浏览器都支持十六进制颜色值。
    十六进制颜色是这样规定的：#RRGGBB，其中的 RR（红色）、GG（绿色）、BB（蓝色）十六进制整数规定了颜色的成分。所有值必须介于 0 与 FF 之间。
所有浏览器都支持 RGB 颜色值。
    RGB 颜色值是这样规定的：rgb(red, green, blue)。每个参数 (red、green 以及 blue) 定义颜色的强度，可以是介于 0 与 255 之间的整数，或者是百分比值（从 0% 到 100%）。
RGBA 颜色值得到以下浏览器的支持：IE9+、Firefox 3+、Chrome、Safari 以及 Opera 10+。
    RGBA 颜色值是 RGB 颜色值的扩展，带有一个 alpha 通道 - 它规定了对象的不透明度。
    RGBA 颜色值是这样规定的：rgba(red, green, blue, alpha)。alpha 参数是介于 0.0（完全透明）与 1.0（完全不透明）的数字。
所有浏览器都支持颜色名。
    HTML 和 CSS 颜色规范中定义了 147 中颜色名（17 种标准颜色加 130 种其他颜色）。
    17 种标准色是 aqua（浅绿）, black（黑色）, blue, fuchsia（紫红）, gray（灰色）, green, lime（绿黄色）, maroon（褐红色）, navy（深蓝色）, olive（橄榄色）, orange, purple（紫色）, red, silver（银白色）, teal（青色）, white, yellow。
例：
#000000; 或 rgb(0,0,0);     黑色
#FF0000; 或 rgb(255,0,0);   红色
#FF0000; 可简写为#F0;
rgba(0,255,0,0.5);          半透明绿色
transparent;                完全透明
.class名:hover{
    color: green;
}/*当鼠标移动到该class位置时变绿色*/    

盒子：
    1.自适应宽度，默认占据一行，固定宽度没有margin-right，没有设置宽度且宽度自适应的盒子是可以使用右边距的
    2.默认高度0，没有设定高度的时候，可以由子元素撑起来
    3.浮动（无法居中）、和定位（absolute、fixed）后会变成块，浮动后会变成排一行的块。




CSS元素类型有三类:
块级元素：
    1.前后的元素都会被换行，默认占据一行。允许设置宽高。
    / p / h / br / ul.ol.dl / li / form / div / table / body / html /
    2. 脱离文档流，不占空间的时候，变为块元素(但不能用margin居中)
       包括内联元素脱离文档流也会变为块

内联元素：
    行内元素，主要针对文字，设置宽高度无意义
    在一行的元素（前后元素不会被换行的元素），不允许设置宽高度，不允许设置垂直方向的外边距。
    只能设置水平方向外边距。一般是用span标签。（p标签是块元素，strong是内联元素）
    
内联块：
    内联元素的块，但是拥有了块的特质，除了占据一行（允许设置宽高和垂直外边距），而且不能用margin来居中，使用text-align居中。
    
居中样式text-align：
    可以居中内容中的文字、内联元素、内联块，子元素会继承，如果子元素是块，继承样式之后显然是没有效果的。
    
块居中：
    块水平使用auto进行居中，没有竖向的auto  
    margin-left: auto; 
    margin-right: auto;         左右auto使块居中
    margin: 0 auto;             居中
    margin: auto;               居中
    
display属性：
    display: block;           转变成块
    display: inline;          转变成内联元素inline，取消前后换行
    display: inline-block;    转变成内联块，这样便可以设置宽度高度       
    display: none;            隐藏元素
    例：实现鼠标移动到盒子a上时显示b，离开时隐藏b；
    /* CSS部分 */
    .a {
        position: absolute;
        width: 50px;
        height: 50px;
        background: blue;
    }
    .a:hover .b {
        display: block;
    }
    .b {
        display: none;
        position: absolute;
        top: 50px;
	    z-index: 1;
        width: 150px;
        height: 150px;
        background: green;
    }
    <!--===== HTML部分 =====-->
    <div class="a">
	    <div class="b"></div>
    </div>
    
CSS浮动：
    连续两个div左浮动则变成两个div并列在同一行。
    float: left;       左浮动，后面的元素会跑上来，在盒子下方；浮动后，文字就会环绕，不会跑底下

overflow及清除浮动：
    外边的大盒子包不住里面浮动的小盒子，这时候就需要`清除浮动`来让他有实际的内容，能被父元素包裹着
    清除浮动可想象为浮动后仍占据着下层空间，让后面的块无法挤上来；
    在浮动的div后面再加个空div，样式写clear: both;可清除浮动。
    在浮动的div外面再包个div，样式写overflow: hidden;或overflow: auto;也可清除浮动。
    overflow: hidden;         清除浮动/文字超出部分隐藏
    overflow: auto;           清除浮动/文字如果超出，出现滚动条，没超出则没滚动条
    overflow: scroll;         文字无论超不超出都有滚动条
    .clear {
        clear: both;
    }                         清除浮动

定位：
    随心所欲的摆放元素，可以使其不影响别的元素位置 
    只要使用了定位 除了无定位（static）以外，都拥有四个样式top right bottom left 值允许正负
    定位比浮动飘得更高
    
相对定位（relative）：
    生成一个相对定位元素，（如果不使用定位的移动样式，则不会产生任何效果）
    可理解为下层空间不变，又占据中层空间（相对下层位置移动）
    1. 以自身所在位置参考进行移动；
    2. 移动后还占据我们原来的空间;
    position: relative;       相对定位
    top: 200px;
    right: 100px;

绝对定位（absolute）：
    生成一个相对定位元素，（如果不使用定位的移动样式，则不会产生任何效果）
    可理解为上升到顶层空间
	1. 它的移动位置是以最近的(不是最外的)定位父级作为参考的（祖辈有定位的元素，即上级盒子有relative/absolute/fixed之一，
    一般父级用相对定位），否则以浏览器边框作为参考移动。
    2. 不占据任何空间
    position: absolute;       绝对定位
    right: 0;
    bottom: 0;

固定定位（fixed）：
    1. 只会以浏览器窗口作为参考移动
    2. 不占任何空间
    position: fixed;
    top: 50%;
    left: 50%;

层级关系(z-index)：
    调整定位的元素层级显示关系，值越大显示越靠前，如果相同则会覆盖显示，允许为负数
    定位有z-index参数（确定优先显示），浮动没有
    z-index: 1;               

透明样式：
    IE8以下不支持透明
    opacity: 0.5;              透明度0~1，IE8及以下不生效，transparent是完全透明，只能用在颜色上面
    filter: alpha(opacity=50); filter在IE8生效，值为0~100
    filter: opacity(50%);      Chrome、Firefox
    background-color: rgba(0, 0, 0, 0.7); RGB颜色透明，不会影响子元素

伪类选择器：
    在选择器上面进行筛选，来选择最终的一个元素，还有触发条件的时候添加新样式的功能的伪类
    :hover                鼠标划上去添加的样式，划出来还原，后面可以跟子代选择器
    :first-child          选择前面选择器中的第一个元素，兼容IE8，第一个标签必须为div才会生效
    :last-child           选择前面选择器中的最后一个元素，不兼容IE8
    :nth-child(1)         选择所在同级中的第几个，会把所有同级算进去，比如p标签
    :not(p)               前面选择器挑出里面所有的P元素
    .box:not(.a)          .box的元素 排除还有另外.a名字的元素
    .box:not(.a):not(.b)  除了.a和.b名字的.box元素可以添加多个`非`
    .box:last-child:not(:first-child)  选择最后一个，同时不是第一个元素

placeholder属性：
    input输入框提示信息，该提示会在输入字段为空时显示，并会在字段获得焦点时消失。
    <input type="search" name="user_search" placeholder="Search W3School" />

Shadow阴影：
    box-shadow: 27px 20px 15px black;   第1个参数是水平方向，第2个参数是垂直方向，第3个参数是模糊大小，第4个参数是阴影颜色
    text-shadow: 0 5px 15px black;

阿里巴巴矢量字体图标的使用：
    iconfont.cn           选择图标，添加入库，按使用帮助来使用


li标签：
    li {list-style: none;}    可把li标签的小黑点去掉

link标签：
    <link rel="stylesheet" href=""><!-- href内填**.css -->
    <link rel="shortcut icon" href="https://thumbs.dreamstime.com/x/交叉剑-10113257.jpg"><!-- href内填**.ico，实现title小图标功能 -->
    
span标签：
    一般用于文字上的样式，不给样式没有任何效果

div标签：
    主要用来装其他元素，单独对div进行css样式或布局，默认占据一行，没有给宽度会撑开这一行，与p标签相同
    
    
id值：
    给元素置顶一个`唯一`的标识符，这种标识符仅能单独对一个元素应用样式   通常用于JS获取元素
    按规定id的值只能使用一次



未整理样式：
    height: 100% !important;  !important为将优先级提到最高
    cursor: pointer;          让鼠标滑上去后变小手指

基线：
    哪个高，抬哪个的基线，一般文字基线肯定比图片低，所以设置文字的基线就体现不出效果了
    vertical-align: middle;   让基线对准中间
    vertical-align: bottom;   不按基线排列，按底部线排列



max-width: 100%;    自适应上层盒子的最大宽度




```