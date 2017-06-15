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

# 按钮标签：
<button id="btn">变化</button>

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

# input：赋予不同的type值可实现不同的表单控件
type类型   描述
text      文本输入框，maxlength最大长度、onlyready只读、 disabled禁止、placeholder占位 
password  密码遮掩框
radio     单选按钮，checked默认选择
checkbox  多选框
submit    收集表单域的name数据，然后提交到服务器上

# 下拉列表框：
<!-- selected默认选择一项 -->
<!-- selected="selected"默认选中 -->
<!-- size="2"  实现两行下拉项 -->
<!-- disabled  禁止选择 -->
<select>
    <option value="music">听音乐</option>
    <option value="running">跑步</option>
    <option value="study">学习</option>
    <option value="coffee">找小姐姐一起喝咖啡</option>
</select>

# 多行文本输入框(文本域) textarea
cols显示多少列，rows现实多少行
<textare cols="30" rows="10"></textarea>

# 按钮：回到表单初始状态
<input type="reset" value="重置表单" />

# 隐藏域：目的在于收集或发送信息 页面上面没有任何效果  CSRF跨域攻击在此作用
<input type="hidden" value="ABCD1234" />

# label元素：
为input元素定义一个标记，label元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。如果你在label元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动將焦点转到和标签相关的表单控件上
<input id="man" type="radio" /><label for="man">男</label>

# 提交方式：
GET    URL地址栏上做拼接问号再加参数
POST   隐式提交方式，看不到，可以抓包

例：
<form action="" method="post">
<!-- post隐式提交，get显示提交 -->
<!-- action填提交的地址，如#，register.html -->
    账号：<input name="user" type="text" /><br /><br />
    密码：<input name="pwd" type="password" /><br /><br />
    性别：
        <input checked id="man" name="gender" value="man" type="radio" /><label for="man">男</label>
        <!-- checked或checked="checked"默认，label标签是为了让点击文字时同样可以选中 -->
        <input id="woman" name="gender" value="woman" type="radio" /><label for="woman">女</label>
        <input id="secret" name="gender" value="secret" type="radio" /><label for="secret">保密</label><br /><br />
        <!-- 此处name全写gender变成互斥作用，唯一 -->
    兴趣：
        <input id="music" name="music" type="checkbox" /><label for="music">听音乐</label>
        <input id="climbing" name="climbing" type="checkbox" /><label for="climbing">爬山</label>
        <input id="study" name="study" type="checkbox" /><label for="study">学习</label>
        <input id="sports" name="sports" type="checkbox" /><label for="sports">运动</label><br /><br />
    生日：
        <select name="year" id="">
            <option value="1991">1991</option>
            <option value="1992">1992</option>
            <option value="1993">1993</option>
            <option value="1994">1994</option>
            <option selected="selected" value="1995">1995</option><!-- selected为默认选择 -->
            <option value="1996">1996</option>
            <option value="1997">1997</option>
            <option value="1998">1998</option>
            <option value="1999">1999</option>
            <!-- option{199$}*9然后按tab键 -->
        </select>年<!-- 下拉列表框 -->
        <select name="month" id="">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
            <option value="11">11</option>
            <option value="12">12</option>
            <!-- option[value="$"]{$}*12 -->
        </select>月
        <select name="day" id="">
            <option value="1">1</option>
            <option value="2">2</option>
            <option value="3">3</option>
            <option value="4">4</option>
            <option value="5">5</option>
            <option value="6">6</option>
            <option value="7">7</option>
            <option value="8">8</option>
            <option value="9">9</option>
            <option value="10">10</option>
            <option value="11">11</option>
            <option value="12">12</option>
            <option value="13">13</option>
            <option value="14">14</option>
            <option value="15">15</option>
            <option value="16">16</option>
            <option value="17">17</option>
            <option value="18">18</option>
            <option value="19">19</option>
            <option value="20">20</option>
            <option value="21">21</option>
            <option value="22">22</option>
            <option value="23">23</option>
            <option value="24">24</option>
            <option value="25">25</option>
            <option value="26">26</option>
            <option value="27">27</option>
            <option value="28">28</option>
            <option value="29">29</option>
            <option value="30">30</option>
            <option value="31">31</option>
        </select>日<br /><br />
    个人说明：<br />
        <textarea name="description" cols="30" rows="10"></textarea><br /><br />
        <!-- 多行文本输入框，cols为列(不准确)，rows为行 -->
    <input type="submit" value="注册" />
    <!-- 没有value则默认显示"提交" -->
    <!-- 点击按钮后地址栏出现一个？，get方式 -->
</form><br /><br /><!-- 给了name才会收集输入内容 -->

<form action="#" method="get">
    账号：<input name="user" type="text" /><br /><br />
    密码：<input name="pwd" type="text" /><br /><br />
    <input type="button" value="我是一个按钮" />
    <input type="reset" /><!-- 重置 -->
    <input name="hidden" type="hidden" value="abcd1234" />
    <!-- hidden：隐藏参数，防止攻击 -->
    <input type="submit" /><!-- 提交 -->
</form>
<!-- 在input标签中，name和id的意思都差不多，name就是名称咯类似于你的变量名，id是唯一标识这个标签，name和id在JS中都会用到，用来定位
具体某个标签；但value含义就不同了要看你使用的是哪个类型的标签，譬如type=text文本框，value是显示在文本框中的初始语句；但是在
type=radio单选框中，value的含义是你所选的值，然后提交给服务器的； -->
<!-- name 属性用于对提交到服务器后的表单数据进行标识，或者在客户端通过 JavaScript 引用表单数据。
只有设置了 name 属性的表单元素才能在提交表单时传递它们的值。
而id属性是为了作标识用的，因为id具有唯一性
value 属性为 input 元素设定值。
对于不同的输入类型，value 属性的用法也不同：
type="button", "reset", "submit" - 定义按钮上的显示的文本
type="text", "password", "hidden" - 定义输入字段的初始值
type="checkbox", "radio", "image" - 定义与输入相关联的值
注意：<input type="checkbox"> 和 <input type="radio"> 中必须设置 value 属性。
value 属性无法与 <input type="file"> 一同使用。 -->
<!-- id用于标记自身，可用于dom操作或者CSS选择器找到自身；
name用于定义这个input收到的值的变量名，例如type="text", name="txt"的input输入“hello",那么就有txt="hello";用于dom操作取值
value就是该input的值，也是显示出来的东西，例如type="button" value="btn"的input，按钮上的文字就btn；
input 必要的属性是type,其他都不是必须的。 -->
<!-- name是给自己看的，value是网页显示出来给大家看的，ID相当于身份证号码，是独一无二的，并且可以用ID来进行操作 -->
<!-- name是标签的名字，当表单提交到处理页面后要根据name来获得值，比如一个文本框name="key"，处理页面要获得文本框的值就用
$_POST['key'](或$_GET['key'])来得到文本框里面的值。
value就是标签的值，比如文本框里默认值是‘请输入用户名’就写在value="请输入用户名"里。如果是按钮就是显示在按钮上面的文字，例如value="登陆"。
id是用来做标记的，比如写JavaScript需要对这个input做操作可以加个id找起来方便。 -->

# 格式化文本：主要用于在网页上显示代码。
<pre>
&lt!DOCTYPE html&gt &lt!-- 给浏览器解析的，我这个文档是html --&gt
&lthtml&gt
    &lthead&gt
        &ltmeta http-equiv="Content-Type" content="text/html;" charset="utf-8" /&gt 
        &ltmeta name="description" content="描述，80字以内" /&gt
        &ltmeta name="keyword" content="关键字" /&gt
        &lttitle&gttitle&lt/title&gt
    &lt/head&gt
    &ltbody&gt
        &lth1&gt&lt/h1&gt&lt!-- h1只敲一次，利于SEO搜索引擎优化 --&gt
        &ltp&gt
            段落内容
        &lt/p&gt
    &lt/body&gt
&lt/html&gt
</pre>
网页效果如下：
<!DOCTYPE html> <!-- 给浏览器解析的，我这个文档是html -->
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html;" charset="utf-8" /> 
        <meta name="description" content="描述，80字以内" />
        <meta name="keyword" content="关键字" />
        <title>title</title>
    </head>
    <body>
        <h1></h1><!-- h1只敲一次，利于SEO搜索引擎优化 -->
        <p>
            段落内容
        </p>
    </body>
</html>


P标签内不能嵌套P标签

```



















