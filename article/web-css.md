# WEB基础之CSS
---
#### 使用CSS的四种方法
```
一、使用style属性： 将style属性直接加在个别的元件标签里。 
<td style="color:blue; font-size:9pt; font-family:"标楷体"; line-height:150%> 
这种用法的优点是可灵巧应用样式于各标签中，但是缺点则是没有整篇文件的『统一性』。
 
二、使用style标签： 将样式规则写在<style>...</style>标签之中。 
通常是将整个的 <style>...</style>结构写在网页的<head> </head>部份之中。这种用法的优点就是在于整篇文件的统一性，只要是有声明的的元件即会套用该样式规则。缺点就是在个别元件的灵活度不足。

三、使用link标签： 将样式规则写在.css的样式档案中，再以<link>标签引入。 
假设我们把样式规则存成一个example.css的档案，我们只要在网页中加入 
<link rel="stylesheet" type="text/css" hree="example.css"> 
即可套用该样式档案中所制定好的样式了。 通常是将link标签写在网页的<head></head>部份之中。这种用法的优点就是在於可以把要套用相同样式规则的数篇文件都指定到同一个样式档案即可。缺点也是在个别文件或元件的灵活度不足。 

四、使用@import引入： 跟link用法很像，但必放在<style>...</style> 中。 
<style type="text/css"> 
    @import url(http://yourweb/ example.css); 
</style> 
```

#### CSS样式

```css
border-radius: 50%; 把图形变成圆形


text-align: center; 让文字居中




# color颜色：
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
.box1:hover{
    color: green;
}/*当鼠标移动到某个单元格时变绿色*/    





```