# WEB基础之HTML
---
## HTML模板
```html
<!doctype html><!-- HTML标准声明  HTML5  只能在第一行 -->
<html>
    <head>
        <!-- charset声明文档的字符串编码集 -->
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />    
        <meta name="Keywords" content="关键字" />
        <meta name="description" content="描述 80字以内" />
        <title>网页标签上的标题</title>
    </head>
    <body>
        <!-- 在body里面写标签 -->
    </body>
</html>
<!--<meta http-equiv="cache-control" content="no-cache" />--><!-- 不保留缓存 -->
```

## HTML标签

> 标签是由尖括号 < > 把关键词括起来，标签通常是成对出现的

```html
# 标题标签：文字加粗、并且单独在一行
<h1>这是标题 1</h1><!-- h1只能出现一次，利于搜索引擎爬取 -->
<h2>这是标题 2</h2><!-- h1最大，h6最小 -->
<h3>这是标题 3</h3>
<h4>这是标题 4</h4>
<h5>这是标题 5</h5>
<h6>这是标题 6</h6>

# 加粗标签：
<b>加粗</b>
<strong>不仅能加粗，还利于搜索引擎优化</strong>

# 倾斜标签：
<i>倾斜文本</i>

# 加下划线：
<u>加下划线</u>

# 加删除线
<s>$998</s>

# 换行标签
<br />

# 水平线
<hr color="skyblue" size="5">

# p段落标签：单独在一行==块==，前后的元素都会被换行
<p>
    段落内容
</p>

# A标签：链接一个页面,点击则会跳转这个链接页面；使用锚点滚动到设定的位置
<a href=""></a>
<a href="#">#代表回到页面顶部</a>
<a href="javascript: void(0);">非跳转链接，可用于特效</a>
<a href="#name">锚点到一个标签上，点击则滚动到那个标签位置</a>
例：
    <a href="#top">跳到name="top"或id="top"的标签，id内的内容具有唯一性</a>
    <a href="http://baidu.com">直接跳转到百度</a>
    <a href="http://baidu.com" target="_blank">在新标签跳转到百度</a>

# 图片标签：
<img src="图片路径" alt="搜索关键词" width="图片宽" height="图片高" title="鼠标移到图片后的提示信息"/>

# 无序列表：默认会有小黑圆点 有的浏览器可能呈现空心小圆点
<ul type="circle">
    <li>disc:默认，实心小圆圈</li>
    <li>square：实心方块</li>
    <li>circle：空心圆</li>
</ul>

# 有序列表：type属性（1，默认值，数字列表排序；a，小写字母排序；A，大写字母排序；i，罗马小写字母排序；I，罗马大写字母排序；）
<ol>
    <li>1</li>
    <li>2</li>
    <li>3</li>
</ol>

# 自定义列表：没有type属性
<dl>
    <dt>标题</dt>
    <dd>数据1</dd>
    <dd>数据2</dd>
    <dd>数据3</dd>
</dl>

# 特殊符号：
空格：    &nbsp; 
小于：    &lt;   
大于：    &gt;   
引号：    &quot; 
版权：    &copy; 
×叉：     &times;
 &：      &amp;

# marquee标签：实现滚动效果
<marquee style="border: 1px solid red;" width="210" height="70">右往左移</marquee>
<marquee style="border: 1px solid red;" width="210" height="70" direction="right">左往右移</marquee><br />
<marquee style="border: 1px solid red;" width="100" height="300" direction="up">下往上移</marquee>
<marquee style="border: 1px solid red;" width="100" height="300" direction="down">上往下移</marquee>
<marquee behavior="alternate" style="border: 1px solid red;" width="100" height="300" direction="down">交替滚动</marquee>
<marquee behavior="slide" style="border: 1px solid red;" width="100" height="300" direction="down">滑落</marquee><br />
<marquee behavior="alternate" style="border: 1px solid red;" width="400" height="400" direction="down">
    <marquee behavior="alternate" direction="right">
        45度交替滚动
    </marquee>
</marquee>

# 表格：tr代表行，td代表列，colspan跨列，rowspan跨行
<table border="10">
    <caption>
        <b>同学录</b>
    </caption><!-- 表格标题 -->
    <thead>
        <tr><!-- 一行 -->
            <th>#</th>
            <th>名字</th>
            <th>年龄</th>
            <th>婚否</th>
        </tr>
    </thead>
    <tbody>               
        <tr>
            <td>01</td>
            <td>名字一</td>
            <td rowspan="2">年龄一</td><!-- 合并行 -->
            <td>婚否一</td>
        </tr>
        <tr>
            <td>01</td>
            <td>名字二</td>
            <!-- <td>年龄二</td> -->
            <td>婚否二</td>
        </tr>
        <tr>
            <td>01</td>
            <td>名字三</td>
            <td colspan="2">年龄三&nbsp;婚否三</td><!-- 合并列 -->
            <!-- <td>婚否三</td> -->
        </tr>
    </tbody>
</table>

# 表单：
<form>
    使用form标签建立表单域，当提交数据的时候会收集表单域里面的数据然后发送给服务器
</form>









```



















