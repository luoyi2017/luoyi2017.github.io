# WEB基础之JavaScript


## js 规范

1.严格区分大小写
2.每一行完整的语句要用 ; 分号
3.代码要缩进
4.js 半角符号	


## ECMAscript标准

//         单行注释
/**/       多行注释
命名规范   可以包含字母， _  $  还有数字，但是不能用数字开头，不能使用js保留字还有关键字
var        定义变量
	





## js 六大数据类型

```js
1. Number     数字, 包括NaN, js的不区分整数和浮点数
2. String     字符串
3. Boolean    布尔值
4. function   函数
5. undefined  未定义.值undefined
6. Object     对象, null/数组/字典等

var a =  1+2
var b = 'which';
var c = false;
var d = null;
var f = ['which',123,'slice']
var g = {
	name : 'which'
}
var fn =  function(){}
var abc;
alert(  typeof a)// typeof 解析数据类型

```



## Number数字

整数、小数(浮点数) 都是Number 
范围：`-2^53 ~ 2^53`
浮点数在计算机当中不精准
`0.8 - 0.1 = 0.7000000000000001`   
`0.3 - 0.1 = 0.19999999999999998`



## Number方法
    Number(param);   将参数转换为数字,能被转换才能使用Number 否则返回NaN; not a Number
    parseInt();  将参数(字符串)转换为数字，整数部分遇到不是数字就停
    parseFloat(); 讲参数转换为数字(浮点数)，遇到不是数就停。
		document.write(parseFloat("10.33aaa"));-----输出10.33
    toFixed(2); 保留2位小数(四舍五入)，返回字符串


### NaN未知数 
自己不等于自己，NaN的数据类型是Number
```javascript
alert( NaN == NaN);// false;
isNaN(参数);// 判断参数是否是NaN；
var n = 1 + undefined
alert(isNaN(n));// true

// 判断n的值是否等于n
alert(n==n);// false  他们自己都不等于自己  NaN的数据类型就是Number
```


### Math数学函数
    Math.pow( 2, 16 );    求2的16次方
    Math.round(0.51);     四舍五入到整数
    Math.ceil(5.1);       向上取整为6
    Math.floor(0.9);      向下取整为0
    Math.min(0,1,-5);     取最小值-5
    Math.max(9,8,7);      取最大值9
    Math.random();        无参数，生成一个0~1的伪随机数  
	Math.random()*30+20;  生成20-50的随机数
    Number没有length属性取长度方法



## String字符串方法

    str[0]                取单个字符索引从0开始 ———— IE8+
    str.charAt(0)         取单个字符索引从0开始 ———— *
    Number.toString()     转换数字为字符串
    str.toUpperCase()     将字符串字母变为大写，无参数
    str.toLowerCase()     将字符串字母变为小写，无参数
    str.indexOf("abc", 5) 查找文本，从第5位开始查找，成功返回索引否则返回-1，无第2个参数则从初始位置开始查找
    str.substring(5,1)    截取字符串(参数之间会做比较，哪个参数小自动放前边, 参数为负数的时候，变为0)
    str.slice(5,1)        截取字符串(参二不能小于参一，支持负数)，取不到为空
    str.split(" ");       用空格分割，返回数组



## Boolean布尔值
	true / false       首字母不要大写
	Boolean转Number    true为1、fasel为0
		Number(true)  ==> 1        Number(false)  ==>  0
	以下五个在做条件判断的时候都为假，其余都为真，包括空对象、空数组 
	undefined  
	null  
	0和-0  
	NaN  
	""
	
// 感叹号！ 取反的意思
if ( !false ) { 
    alert(true);
}




## null和undefined
	null是一个keyword关键字，非对象；
	undefined是预先定义好的全局变量不是关键字，变量声明没有赋值也是undefined，值就是undefined没有定义；
	null == undefined 返回true  在做条件判断的时候都为假   假和假相等
	null       转换成数字时为0    做条件判断为假  类似于正确空值的填补
    undefined  转换成数字时为NaN  做条件判断为假  类似于错误空值的填补
		1+undefined = NaN; // 会强制转换为数字进行计算 1+NaN = NaN；  
		1+null = 1; // 1+0 = 1;  



## Array数组
```javascript
var arr = [0, 1, 2];  
alert(typeof arr); // Object，无法确认
```
判断是否为数组：typeof返回的结果是Object对象，无法判断准确  
| Method                    | Description                              |
| ------------------------- | ---------------------------------------- |
| **Array.isArray(arr);**   | **返回true是数组**                            |
| **arr.join("== 字符串 ==")** | **[1, 2, 3]   ==> "0== 字符串 ==1== 字符串 ==2"** |



## 可以顶置的js代码

```javascript
// 当浏览器页面中完全(节点元素、图片、文字....)载入完成之后才执行，可置顶
window.onload = function() {}
```


## js运算符

运算符       +  -  *    /   %余   
赋值操作符   =  +=  -=  /=   %= 
能被计算才会执行计算，不能计算则会出现各种问题(报错 or NaN ...)  
	1. 除了加号,  - * / % 这4种会强制将参数转换为数字
	2. 加法运算 只要有一个为字符串  相加则是字符串拼接
	3. 布尔值和数字计算：true = 1，false = 0

### 练习
```javascript
var a = 3;
a += "2"; // a = a + "2"; 32
a -= "2"; // a = a - "2"; 30  强制转换Number

a++; // 30+1  自己增加1，没有自己增加2...的符号写法
alert(a); // 31


a--;
alert(a); // 30

var b = a++; // 
alert(a); // 31
alert(b); // 30  因为是先把a变量的值赋给b，然后原来的a变量再自增1


var c = ++a;
alert(a); // 32
alert(c); // 32  先自己增加一次，然后再赋值给c

```

### 判断条件符号
```
>  <  ==   <=   >=   !=不等于   ===全等于(还会判断数据类型)   !== 不全等

```


### 逻辑运算符
```javascript
   &&  ||  !
   与  或  非
   和  或  取反
   & | 单位符号是位操作，这里不阐述
        与：遇到假就停  返回假   短路设置
        或：遇到真就停
```
    // if ( !"false" ) {
    //     alert(1);
    // } else {
    //     alert(2);
    // }注意"false"是字符串，不是布尔值！


### ||或 条件练习  
```javascript
var a = 1 > 2 || 2 > 3 || 8;
// 遇到真就停，短路设置，一不大于二false，二不大于三false，8没有判断符号转换布尔来进行判断true/false
// 除了0以外的数都为真；
```

### 非练习  
```javascript
var a = !false; // true
```


### 赋值运算符
=    -=    +=    ++(自增1)   --(自减1)   /=   *=    %=

    var a = 1;
    a += 1;  // 同a = a + 1;

    var b;
    b = a++;  // 等同于b = a; a++; 所以b=1,a=2;

	var c;
	c = ++a;  // 先a++;  再c=a; 所以a=3,c=3;



## 警告窗
```javascript
var a = function() {
    alert(666);
}
alert(a); // 弹出函数一整块


var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
alert(arr);// 弹出1,2,3,4,5,6,7,8,9


var obj = {name: "slice"};
alert(obj); // 弹出[object Obejct]
```


## 控制台打印日志
console.log("This is Console Print");



## for循环
```javascript

    for(var i=0; i<100; i++) { // 标准写法，i变量声明可以拿出去   第三个执行的操作也可以拿到里面去写
        console.log(i); // 0-100上面 声明变量必须要赋初始值0  否则undefined进行计算会变成NaN
    }
    
    for(var key in document) {
        console.log(key +"======"+document[key]); // 查看document里面所有的方法
    }

    var ulD = document.getElementById("list");
    var lis = ulD.getElementsByTagName("li");
    for( var i=0; i<lis.length; i++ ) {
        // 循环"绑定事件"
        lis[i].index = i;// index为自己取的变量名，非系统关键字
        lis[i].onclick = function() {
            alert("该点击的元素索引是：" + this.index + "\n\n\n内容是："+ this.innerHTML);
            //不能用alert("该点击的元素索引是：" + i + "\n\n\n内容是："+ this.innerHTML);因为页面测试点击后，循环就立马结束了，i为结束后的值！
        };
    }

```


## 流程控制语句
```javascript
    if ( 10>1 ) {
    	alert(1);
    }else if( 5<50 ){
    	alert(2);
    }else if( 10>20 ){
    	alert(3);
    }

    // 只有一条真语句
    if( 8 > 0 ) alert('This is 8 > 0');
    
    
    // 三目运算符(只有一条真语句和只有一条假语句的时候)
    var a = 10>1 ? 2 : 5;// 变量写在里面会报错
    
    
```



## 循环语句控制  
```javascript
// continue到循环尾
for(var i = 0; i<10; i++) {
    if(i==5) continue;
    console.log(i);
}


// Break跳出循环
for(var i = 0; i<10; i++) {
    if(i==5) break;
    console.log(i);
}
```




## for循环绑定事件  

```html
<ul id="list">
    <li>111</li>
    <li>222</li>
    <li>333</li>
</ul>
```
```js
for(var i=0; i<lis.length; i++ ) {
    lis[i].index = i;
    lis[i].onclick = function() {
        alert(this.index);
    };
}
```
> 注意索引只是循环绑定的序列号  写在事件里则不会达到预期   因为后面的函数只能在触发事件才能执行 已经是循环完了的i(index)



## 函数   
```javascript
function fn1() {...}

取名规范：
    1. 数字、字母、下划线、$ 任意组合 
    2. 不能用关键字  数字不能作为变量名开头

函数执行：
    1. 事件驱动函数的执行,异步事件驱动模型，例如按下按钮执行
    2. 函数名加括号来执行

函数表达式：
    var f = function() {};
    调用时用f();

匿名函数：
    没有名字的函数，就是匿名函数，不能单独出现；
    如：以下这种就不行，会报错
    function(){
        alert(666);
    }

及时函数(自执行函数)：
    立马、立即执行的函数
    例：国内喜欢用这种
    (function(){
        alert(666);
    })()
    或：国外喜欢用这种
    (function(){
        alert(666);
    }())
    或：以下不推荐使用
	!function() {alert(4);}()
	~function() {alert(4);}()
	-function() {alert(4);}()
	+function() {alert(5);}()



```




函数特点：  
	1. 匿名函数不能单独出现，需要给名字
	2. 函数默认返回undefined
	3. 函数名加括号执行，或通过事件驱动函数执行。
	4. 函数名字会覆盖变量名
	5. alert弹出函数的时候，弹出则是函数本身代码块、
        alert( function(){alert(1)}());
        弹出function(){alert(1)}()；
        alert( (function(){alert(1)})() );
        先弹出1，再弹出undefined;


## 传参数  
加入我要定义一个加法的方法，这个方法肯定是至少两个数 相加返回它的和
```js
// 普通方式，比较死  
var result = 95641156 + 156056;

// 封装成函数，较灵活，可以随时调用
    function fn(a, b, c) { // 形参   形式参数
        // var a = 1;
        // var b = "太帅了！"
        // var c = 30
        alert( a+c +"第二个参数是：" + b );
    }
    fn(5, "太帅了！", 30); // 执行函数所传递的参数 叫实际参数，实参

    //function add (a, b){
    //    return a*1 + b*1;可通过*1强制转换为数字
    //    return Number(a) + Number(b);正规写法
    //}
    //alert(add(1230,"231"));


// 不定参数，可变参数(变参、不定参)，函数隐藏参数(arguments)在函数调用时传递给函数真正的值。
function sum () {
    var result = 0;
    for(var i=0; i<arguments.length; i++) {
        result += arguments[i];
    }
    return result;
}
alert( sum(85456,5,56,8,87,546,9,63,6,48) );
alert( sum(1, 2, 3, "4", 5, 6, 7, 8 ) );//结果为?
```



## return返回值
函数执行返回的结果可以通过return 返回出去，默认函数返回undefined  



## 封装函数
```js
function $(idName) {
    return document.getElementById(idName);
}


// 严谨一点的写法
function $(nodeName) {
    if(nodeName && (typeof nodeName).toLowerCase() === "string") {
        if( document.getElementById(nodeName) ) {
            return document.getElementById(nodeName);
        }
    }
    
    return "没有获取到元素，请检查传入的是一个正确的字符串id名字";
}
```



## 函数作用域
```js
// 注：一个变量声明之后没有被赋值就是undefined
总结：
	第一步，定义：找全局var，全局的function函数
	第二步，执行：从上往下，遇到子作用域，则继续按定义，执行步骤
	
例一：
	// var a;
	// alert(a);
	// a = 1;
	/*
	    解：
	        第一步：声明，找var和function，除了var和function不是作为开头都为执行操作
	        第二步：执行。每一个单独的function里面是单独一个作用域

	    定义 var a;
	    执行 alert(a);// undefined
	         a = 1;// 1
	*/
	
例二：
	// var a = 0;
	// function fn() {
	//     alert(a);
	// }
	// fn();
	/*
	    定义：
	        var a = 0;    fn(){...}

	    执行：
	        a = 0;
	        fn();

	        定义：
	            
	        执行：
	            alert(a);// 0
	 */

例三：
    // var a = 0;
    // function fn() {
    //     alert(a);
    //     var a = 1;
    // }
    // fn();
    /*
        定义：
            var a=0;   fn() {...};
        
        执行：
            a = 0;
            fn()
                定义：
                    var a = 1;   // undefined

                执行：
                    alert(a); // undefined
                    a = 1;
     */
    
例四：
    // var a = 0;
    // function fn() {
    //     alert(a);
    //     a = 1;
    //     alert(a);
    //     var b = 2;
    // }
    // fn();
    /*
        定义：
            var a;   fn(){...};

        执行：
            a = 0;
            fn();
                定义：
                    b;

                执行：
                    alert(a);  // 0
                    a = 1;

                    alert(a); // 1
     */

例五：
    // fn();
    // alert(a);
    // var a = 1;
    // function fn() {
    //     a = 666;
    //     var b = 2;
    // }
    // alert(a);
    /*
        定义：
            a=1;   fn() {...};

        执行：
            fn();
                定义：
                    b=2;

                执行：
                    a = 666;
                    b = 2;

            alert(a); // 666
            a = 1;
     */

例六：
    fn(); 
    alert(a); // undefined
    a = 0;
    function fn() {
        alert(a); // undefined，注意，不会使用外面的全局变量a=0
        alert(b); // undefined
        alert(fn);// 函数本身，注意，不是alert(fn());
        var a = 1;
        var b = 2;
        function c() {
            alert(a);
        }
        return c;
    }
    /*
        定义：
            var a=0;   fn() {...};

        执行：
            fn();
                定义：
                    var a=1;  var b=2;  c(){...};
                    
                执行：
                    alert(a);  // undefined
                    alert(b);  // undefined
                    alert( fn ); // 一堆函数
                    a = 1;
                    b = 2;
                    return c;

            alert(a); // undefined
            a = 0;
     */
	 
```



## 回调函数  
当传入一个函数作为参数被另外一个函数调用时，此刻则是回调函数  
```js
function fn(callback) {

    // 传入一个函数 为true  | 判断数据类型为函数       |   执行函数  // 引用外面的函数作为参数进行调用执行
    callback && callback.toLowerCase() === 'function' && callback();
}

// 无参传入
fn(function() {
    alert(1);
})


// 传入参数(错误方式)  
fn( error(a, b, c) ); // 这里传入的是    运行完error函数返回的一个结果  没有返回值则传入的是undefined  加括号执行报错


// 传入参数(正确方式)
fn(function() {
    fnct(a, b ,c);
})
```



## 闭包
```js
闭包：
    函数里面的变量是静态方式存储，创建之后不会被立即被销毁 ———————————— 这种特性在计算机当中科学文献称为：闭包

闭包作用：
    为了让外界访问到里面的变量.
    
    优点：
        1. 使用私有变量，可以避免命名重复的问题，保护全局污染；
        2. 延长变量生命周期，函数使用完成之后内部的变量不会释放，同全局变量一样不会被清理，下次调用函数 继续使用之前"保存"的局部变量

    缺点：
        1. 延长变量生命周期，注定就会导致常驻内存得不到及时清理 ==> 滥用闭包则会消耗大量性能
		2. 内存得不到释放，可能会导致内存泄漏甚至浏览器崩溃的情况

闭包例子:
	例一：
	    // function fn() {
	    //     var a = 1;
	    //     a++;
	    //     alert(a);
	    // }

	    // fn(); // 2
	    // fn(); // 3

	例二：
		var a = 1;
		function fn() {
		    a++;
		    alert(a);
		};

		fn(); // 2
		fn(); // 3

	例三：
	    function fn1() {
	        var a = 0;// 局部变量
	        function fn2() {// 闭包函数   返回出去，目的能够访问到上面的a变量
	            a++;// 访问上面的a变量 
	            alert(a);
	        }
	        return fn2;
	    }

	    var f = fn1();// 执行fn1函数，声明局部变量a    然后返回子函数fn2 (此时  局部变量和 函数一同被保存到了f变量中)
	    f(); // 1
	    f(); // 2
		var a = 10;
		alert(a); // 不冲突，避免了全局变量的污染
	    f(); // 3
```




## 属性操作  

```js
标签上面所支持的属性可以直接通过点属性来获取或设置  
例如a标签上面和link标签上面就有href这么一个属性别的标签是没有的  
    var btn = document.getElementById("btn");
    var img = document.getElementById("imgs");
    var aDom = document.getElementsByTagName("a")[0];

    // btn.onclick = function() {
    //     /*
    //         一个对象下面没有的属性返回undefined
    //         只有对象才能去点方法点属性
    //      */

    //     img.title = "风景真美";
    //     img.width = "300"
    //     img.height = "210"
    //     img.src = "http://pic.90sjimg.com/back_pic/u/00/02/82/06/561b457215461.jpg";
    //     img.href = "http://baidu.com";img没有这种属性

    //     aDom.href = "http://baidu.com";
    //     aDom.innerHTML = "跳转到百度";
    //     alert(img.value);
    // }

一个对象如果没有这个属性则返回undefined因为节点对象已经预先定义好了所有的属性并且把值保存在其中，我们自己定义的属性是没有预先被定义的，只能通过以下方法来操作
    /*
        节点对象.setAttribute("设置属性名", "设置属性值");
        节点对象.getAttribute("要获取的属性名");
        节点对象.removeAttribute("要移除的属性名字");
     */
	 
    btn.onclick = function() {
        alert(img["data-color"]);
        alert( img.removeAttribute("data-color") );
        box.className = "";//比如不能用img.class，要用img.className
    }
```




## class名字
class属性比较特殊，dom.className、  因为在ES6中 新加入了class类



## 获取最终显示在网页上面的样式  
```js
Dom.currentStyle.width        IE获取最终呈现样式的方法
getComputedStyle(Dom).width   Chrome、Firefox获取最终呈现样式的方法
例：
	var box = document.getElementById("box");
    // alert( getComputedStyle(box).backgroundColor );

    //dom对象，attr属性，以下为写兼容函数
    function getStyle(dom, attr) {
        if( dom.currentStyle ) {
            return dom.currentStyle[attr];//不能直接用.attr属性，用[]才能接收变量(字符串)里面的值
        } else {
            return getComputedStyle(dom)[attr];
        }
    }
    alert( getStyle(box, "width") );

注意：
	简写的css在一些浏览器当中得不到支持  
	所以background ==>  background-color OR background-image  
	border ==> border-width  ==> border-color  
```


## 数组

```js
数组特点：
    1. 通常情况下，数组访问元素会比对象访问属性要快很多，数组底层经过了一些优化。
    2. 数组是有序列的集合，每一个存放的值叫元素，可以通过索引、下标、偏移
    3. 数组可以装任意数据类型.
    4. 数组可容纳最大值2^32-1   4294967295
    5. 当前索引没有元素返回undefined.

创建数组：
	var arr = [1, 2, 3];
	var arr0 = [ , , ]; // 此方法只有两个元素，在数组中允许接受可选逗号结尾
	var arr1 = newArray([]);
	var arr2 = newArray(10); // 长度10的空数组,10个空元素
	var arr3 = newArray(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

判断是否为数组：
	Array.isArray(arr)
    [1, 2, 3] instanceof Array //判断左边是不是右边的实例，是数组返回true
    //不能直接alert("abc" instanceof String);除了对象外，要构造出来的才能用instanceof来判断；
    // var str = new String("abc");
    // alert(str instanceof String);
    // alert(str);
	
查看数组元素个数：
	arr.length
	
取元素：
	arr[0] // 如果该索引位置上面没有任何元素，或超出当前最大索引 则返回undefined
	arr[20] = 666; // 前面长度不够则用undefined 填充
	arr[arr.length-1] // 取最后个元素

[]的使用补充：
	var oBox = documentgetElementById('box');
	oBox['onclick'] = function(){
		var x = 'height';
		this['style'][x] = '200px'; 
		// this.style.height = '200px';
	}

逻辑删除元素：
	delete arr[index] // 逻辑删除，用undefined来占坑，类似于重新赋值为undefined一样

数组操作及真实删除：
    arr.push() 添加到数组末尾
    arr.unshift() 头部添加元素
    arr.pop()   末尾删除一个元素(不需传参数)  返回删除的元素
    arr.shift() 删除头部第一个元素  返回删除的元素

清空数组：
	arr.abc = "This is Abc Attr";
	arr = []; // 重新赋一个空数组，内存地址改变，之前绑定的属性将消失。

	var arr = [1, 2, 3];
	arr.abc = "User-defined Attribute";
	arr.length = 0; // 通过length设置为0清空元素，同时保留所绑定的属性
	alert(arr.abc); // 还能弹出abc绑定的属性

in运算符：
    对象：判断左边属性(键)是否在对象当中
		// var obj = {};
	    // obj.name = "sliceTeacher";
	    // alert("name" in obj);

	    var obj = {
	        "name": "sliceTeacher",
	    }
	    alert("name" in obj);
		
    数组：判断当前索引位置是否被赋值，通过索引判断
		var arr1 = [5, 7];
		alert(0 in arr1); // 判断索引0的位置是否有被赋值

		// 当前元素只要被赋值返回true  包括赋值undefined也会返回true
		var arr = [1, 2, 3, 4, 5];
		arr[9] = undefined;
		alert( 9 in arr );

数组剪切：  
    arr.splice();
        参一：起始位置，当只有一个参数的时候从当前参数索引位置开始剪
        参二：剪多少个元素
        参三以上：替换被减掉的元素或插入在被减掉的元素的位置上面
		return：返回被减掉的元素

	只有一个参数时:
	arr.splice(5) // 从索引5的位置开始减掉余下的元素
	arr.splice(0) // arr.splice(-arr.length) 两者皆可，支持负索引   从头开始剪完  清空数组，同时还保留绑定的属性

	两个参数时:
	arr.splice(3, 1)// 从索引3的位置开始减掉一个元素，返回被减掉的元素

	三个参数以上，插入或替换
	arr.splice( 2, 0, function() {}, true, {} ); // 剪掉的部分替换或插入

数组转字符串：  
	arr.toString(); // 转成字符串，每个元素会以逗号分割[1, 2, 3] ==> "1,2,3"
	arr.join(""); // 不传参数默认使用逗号拼接，必要的时候需要用空字符串作为参数，还可以拼接别的字符  

```

## 通过class获取元素兼容写法
```js
    document.getElementsByClassName("className"); // 返回集合，不兼容IE8以下
    使用原生的js写出一个兼容所有浏览器的方法 ———————— 通过class名字获取节点元素的方法，封装成函数
    
    思路：
        1. 获取所有的元素   
            document.all  IE8以下会多出一个元素 不过不受影响    
            document.getElmenetsByTagName("*"); 获取所有的元素
        2. 遍历每个元素，判断每个元素的class名字是否与我想获取的相同
        3. 如果相同把当前的元素推进临时数组里面
        4. 遍历完成之后返回这个数组
        
    思考：
        如果class名字有多个呢？   <div class="box box2"></div>


    // 通过class获取元素兼容写法
    var alls = document.all;
    var temp = [];
    for( var i=0; i<alls.length; i++ ) {
        if( alls[i].className == "xxxxx" ) {
            temp.push(alls[i]);
        }
    }
    alert(temp);

	
    /*
        多个class名字写法
            思考之后，多个class名字使用空格分割的，我们可以通过空格分割字符串返回数组遍历名字再判断
     */
     
    var alls = document.getElementsByTagName("*");
    var temp = [];
    for ( var i=0; i<alls.length; i++ ) {
        var names = alls[i].className.split(" ");
        for (var x=0; x<names.length; x++) {
            if( names[x] === "xxxx" ) {
                temp.push( alls[i] );
                break;
            }
        }
    }
    alert(temp);
    
    // 封装成函数
	function getDom(names) {
	    if( document.getElementsByClassName ) {
	        return document.getElementsByClassName(names);
	    }
	    var alls = document.getElementsByTagName("*");
	    var temp = [];
	    for(var i=0; i<alls.length; i++) {
	        var arr = alls[i].className.split(" ");

	        for(var x=0; x<arr.length; x++) {
	            if(arr[x] === names) {
	                temp.push(alls[i]);
	            }
	        }
	    }
	    return temp;
	}
	alert(getDom("names"));

```

## JSON  

```js
一种轻量级的数据交互格式，它是`字符串`(早期使用的是XML：清晰易懂，比JSON占空间大)  

JSON和JS对象:
    js对象:js的一种数据类型，是js特有的，无法传递数据。
    JSON:  一个交互的格式，可以传递数据，实际上传递的是"字符串"。

JSON语法规则：  
    1. JSON数据格式的键和字符串的值都为双引号,单引号则在某种情况下会报错;
    2. 可以装通用的数据类型，数字、字符串、布尔、数组(python中的list)、对象(python中的字典)、null(python中的none)，(除了undefined、function、NaN……之外)

JSON在js里的两种定义方式：
	早期IE(IE7-) 不支持可选逗号结尾
	
    //法一
    var obj = {
        "name" : "abc",
        "age"  : 18,
        "marry": true//要兼容IE7以下，此处不能有逗号
    }
    // '{"name":"abc","age":18,"marry":true}'
	// obj.age = 18

	//法二
	var obj1 = new Object(); // 只要new的构造函数  返回的都是对象
	obj1.name = "abc";
	obj1.family = new Object();
	obj1.family.sister = new Array();
	obj1.family.sister[0] = "大姐";
	obj1.family.sister[0] = "二姐";

转换为JSON：
    var s = '{"name":"slice", "age": 18, "marry": false}';

JSON字符串转JS对象:  
	主要将后台返回的JSON数据转换成js对象，便于操作
	JSON是内置对象是ES5添加的，支持IE8+;  
	<script src="json2.js"></script>// 通过调用json2.js让IE7及以下兼容JSON
    var obj = JSON.parse('{"name":"abc", "age":18, "marry": true}');
    alert(obj.name);

JS对象转JSON字符串:  
	用于发送到后台。
	json.stringify(js对象)转JSON字符串  
	var obj = {name:"slice", age: 18};
	obj = JSON.stringify(obj);
	alert(typeof obj);
	
```


## 定时器

```js
到一时间，执行函数

延时定时器：  
	setTimeout()
		参一：延时执行的函数(匿名函数或函数名字，传参数变为'a(1, 2)')
		参二：延时多少毫秒ms
    例：
    setTimeout(fn, 2000)-----注意，fn不能加()
    function fn(){
        alert("1111");
    }

    如果要传参数，则：
    setTimeout(function(){
        fn("22222")
    },2000)
    
    function fn(name){
        alert(name);
    }

    或：
    setTimeout('fn("3333")', 2000)

    function fn(name){
        alert(name);
    }

    或：
    setTimeout('alert(1+2);', 2000)


清除延时定时器：
	clearTimeout()   参数为定时器返回的序列号  从1开始


循环定时器：  
	setInterval()
		参一：循环执行的函数(匿名函数或函数名字)，传参数变为字符串"fn(1,5,6)"
		参二：延时多少毫秒ms，循环执行参数一
    例：
    setInterval(function(){
        alert(1);
    }, 2000);
	

清除循环定时器：  
	clearInterval(定时器的序列号)
	例一：
    var i = 0;
    var num = setInterval(function() {
        i++;
        if(i>=3) {
            clearInterval(num);//清除循环
        } else {
            alert(i);
        }
    }, 2000);
	
	例二：
    var level = 5;
    var timer = setInterval(function(){
        if(level) {
            clearInterval(timer);
        }
    }, 2000)
	
	例三：
	(function() {
	    var i = 0;
	    var timer2 = setInterval(function(){
	        i++; 
	        if(i>=3) {
	            clearInterval(timer2);
	        } else {
	            alert('每两秒我就弹一次广告'); // 一定要使用else   如果清除了定时器 当前这一次函数 还是会执行完
	        }
	    }, 2000)
	})()
	
```
	
## 时间日期 
 
```js
方法：
	date*1                 时间戳
    date.getTime()         十三位时间戳
    date.getFullYear()     获取年
    date.getMonth()        获取月份 从一份月开始为0
    date.getDate()         获取某一天  多少号
    date.getDay()          星期几  星期天返回0
    date.getHours          获取几点
    date.getMinutes        获取分
    date.getSeconds        获取秒
	以上获取返回都为Number
	
例：
    var date = new Date();
    // alert(date);// 弹出日期
    // alert(Number(date));// 弹出时间戳
    // alert(date*1);// 弹出时间戳
    // alert(date.getTime());// 弹出十三位时间戳

    var temp = date.getDay();

    setInterval(function(){
        var date = new Date();
        console.log(date.getHours()+"点"+date.getMinutes()+"分"+date.getSeconds()+"秒");
    }, 1000);

```

## 节点操作

```js
DOM 和 BOM
    DOM：
        Document Object Model-----简单的说，就是标签
        文档     对象   模型

    BOM:
        Browser Object Model
        浏览器  对象   模型
        window
    
    window.onresize = function(){
    	console.log('=====');
    }//window代表浏览器，onresize代表重置大小
	

方法：
    children                  获取所有的子元素，类数组
    nextSibling               下一个兄弟节点，IE8-
    nextElementSibling        下一个兄弟节点，IE9+ Chrome Firefox
    previousSibling           上一个兄弟元素 IE8-
    previousElementSibling    上一个兄弟元素  IE9+ Chrome Firefox
    parentNode                找到父节点
	nodeName                  节点标签名
    removeChild(移除的子元素)  通过父元素删除子元素
    appendChild()              追加元素在内容末尾
    document.createElement("link")  创建Dom元素
    insertBefore( 要插入的元素, 插入哪个元素之前 );
	例：
    alert( box3.parentNode.id );
    alert( box3.parentNode.nodeName);//nodeName为节点标签名
	
创建元素：  
	var a = document.createElement("a");
	a.href="http://www.qq.com";

插入元素：  
	插入在元素的前面 ==> 同级关系
	参一：插入的元素
	参二：插入哪个元素之前
	boxparent.insertBefore( xxx, box ) // 父元素里面把xxx元素 插入到box元素之前

获取宽高度：
	document.body.clientWidth   获取body宽度，内容+内边距 
	document.body.clientHeight  获取body高度    
	box.offsetWidth             内容+内边距+边框 
	box.offsetHeight         
	box.offsetLeft              当前元素距离定位父级的定位值，包括外边距
	box.offsetTop
	例：
	var box = document.getElementsByClassName("box")[0];
    // alert( document.body.clientWidth );

    // function getStyle(dom, attr) {
    //     if(dom.currentStyle) {
    //         return dom.currentStyle[attr];
    //     } else {
    //         return getComputedStyle(dom)[attr];
    //     }
    // }

    // alert(getStyle(box, "width"));
    alert( box.offsetTop );
    // alert(box.offsetLeft);

```

## 事件对象

```js
作用：  
	获取用户的鼠标点击位置，或者按下了某键等等。

事件对象获取：  
	全局Event接收或事件函数中第一个形参接收事件对象。
	全局event      谷歌和IE都支持，Firefox会报错。
	形参接收方式    Chrome FireFox IE9+ (IE8返回undefined)
	例：
	// 假设外面var了个a，函数里面也var了个a，想在函数里面调用外部的a，则用window.a;
	document.onclick = function(event) {
	    event = event || window.event;
	    for(var key in event) {
	        console.log(key + "=======" + event[key]);
	    }
	}

metaKey事件：
	metaKey 事件属性可返回一个布尔值，指示当事件发生时，"meta" 键是否被按下并保持住。
	metaKey对应键盘上的windows键
	语法：event.metaKey
	例：
	function isKeyPressed(event){
	    if (event.metaKey==1){
	        alert("meta键被按下!");
	    }else{
	        alert("meta键没被按下!");
	    }
	}

clientX,Y事件：
	返回当事件被触发时鼠标指针向对于浏览器页面（可视区域）的坐标。

pageX,Y事件：
	总网页文档坐标 

button事件：
	可返回一个整数，指示当事件被触发时哪个鼠标按键被点击。
	左键0 滚动键1 右键2 IE8-值会变化 
	语法：event.button=0|1|2

which事件：
	获取按下的键盘按键Unicode值。

oncontextmenu事件：
	在元素中用户右击鼠标时触发并打开上下文菜单。
	例：
	document.oncontextmenu = function() {
	    return false;// 禁止浏览器系统右键菜单
	}

Drag拖拽事件：
	原理：鼠标按下 ==> 拖动 ==> 抬起
	例：
	var box = document.getElementById("box");

	box.onmousedown = function(e) {
	    e = e || event;// 兼容写法
	    var initX = e.clientX; // 获取初始点击的坐标
	    var initY = e.clientY;
	    var initLeft = box.offsetLeft; // 到定位父级左边的距离
	    var initTop = box.offsetTop;

	    document.onmousemove = function(e) {
	        e = e || event;
	        // 获取移动后点击的坐标
	        var moveX = e.clientX,//另一种var的写法
	        	moveY = e.clientY,
	        	// 变化量
	        	changeX = moveX - initX,
	        	changeY = moveY - initY;

	        // 变化量加上初始的位置
	        box.style.left = changeX + initLeft + "px";
	        box.style.top = changeY + initTop + "px";
	        console.log(changeX, changeY);
	    };
	};

	document.onmouseup = function() {
	    document.onmousemove = function() {};// 赋值空让鼠标弹起时不再移动
	}

cancelBubble取消冒泡事件：  
	当父元素与子元素都绑定了"相同的事件"
		子元素触发事件时候会传递给父元素，相当于父元素也触发了事件 ———————— 事件传播，冒泡事件
		
	鼠标滑入     / 鼠标滑出
    onmouseenter / onmouseleave //除了这两个，大部分事件都是冒泡事件
    onmouseover  / onmouseout
    onmouseenter   滑入滑出时只触发一次
    onmouseover    滑入滑出时可反复触发

	例：
	var parent = document.getElementById("parent");
    var box1 = document.getElementById("box1");

    box1.onmouseover = function(e) {
        e = e || event;

        e.cancelBubble = true;//取消冒泡
        console.log("我是子元素!============");
    }

    parent.onmouseover = function() {
        console.log("我是父元素");
    }

事件监听方法：  
	假如我想要绑定两个事件函数呢，传统方式会被覆盖如下：
	document.onclick = function() {
	    alert(1);
	}
	document.onclick = function() {
	    alert(2);
	}// 弹出2 会覆盖上面的

	这时候就需要addEventListener()方法 IE9+
		参一：事件名，去掉on，如onclick去掉on
		参二：函数
		参三：true捕获事件，false冒泡事件。默认false，可不写
	document.addEventListener('click', fn1);
    document.addEventListener('click', fn2);

	IE事件监听方法：
		attachEvent() IE10-
			参一：事件名字必须加on
			参二：事件函数  
			没有第三个参数，IE8以下会从最后添加的时间开始往上面执行
		document.attachEvent('onclick', fn1);
	    document.attachEvent('onclick', fn2);

	注册事件兼容写法：
		function addEvent(obj, event, fn) {
		    if(event.substring(0, 2)=='on') {
		        event = event.substring(2);
		    }
		    obj.attachEvent ? obj.attachEvent('on'+event, fn) : obj.addEventListener(event, fn, false)
		};
		
		function addEvent(dom, eventName, fun) {

	        if(eventName.substring(0, 2) === "on") eventName = eventName.substring(2);

	        // 三目运算符
	        dom.addEventListener
	            ? dom.addEventListener(eventName, fun, false)
	            : dom.attachEvent("on"+eventName, fun);
	    }
		
		// alert(document.addEventListener);
	    addEvent(document, 'click', fn1);
	    addEvent(document, 'onclick', fn2);

	取消事件监听：
		从新赋值为空无效，匿名函数不可取消  
		// document.onclick = null;不能用此办法取消事件
		dom.removeEventListener(事件名, 函数名)两个参数必填
		dom.detachEvent(事件名，函数名) 
		注册的时候怎么填写，移除时间就需要怎么填写  
		兼容写法  
		function removeEvent(obj, event, fn) {
		    if(event.substring(0, 2)=="on") event = event.substring(2);
		    obj.detachEvent ? obj.detachEvent("on"+event, fn) : obj.removeEventListener(event, fn);
		};
		
		function removeEvent(dom, eventName, fun) {
	        // if( eventName.substring(0, 2) === "on" ){
	        //     eventName = eventName.substring(2);
	        // }
	        // 假如只有一条语句，且没有else，可简写为如下：
	        if( eventName.substring(0, 2) === "on" ) eventName = eventName.substring(2);

	        // if( dom.removeEventListener ) {
	        //     dom.removeEventListener(eventName, fun);
	        // } else {
	        //     dom.detachEvent("on"+eventName, fun);
	        // }
	        // 一真一假可简写成如下：
	        // 三目运算符
	        dom.removeEventListener
	            ? dom.removeEventListener(eventName, fun)
	            : dom.detachEvent("on"+eventName, fun);
	    }

	    removeEvent(document, 'click', fn1);

	总结：
		addEventListener     添加事件 Chrome、IE9+ 
		attachEvent          添加事件 IE10-        
		removeEventListener  移除事件 Chrome、IE9+ 
		detachEvent          移除事件 IE10-        

键盘事件：
	只有能被输入才能触发键盘事件、input、textarea  
	如果要实时获取用户输入的字符需要使用onkeyup，onkeydown会延迟一个字符
	事件触发顺序: 1.onkeydown  2.onkeypress  3.onkeyup
	例一：
	// onkeypress 属性在按下按键时触发。
	var inp = document.getElementsByTagName("input")[0];
	inp.onkeypress = function() {
	    console.log(this.value);
	};
	
	例二：
	// onkeyup 属性在松开按键时运行脚本。
	var inp = document.getElementById("inp");
    inp.onkeyup = function() {
        console.log(this.value);
    }

	如果要判断ctrl+c ctrl+alt+c shift+方向键 需要通过是否按下c的event事件中的功能键属性是否为true
	例：
	var box = document.getElementById("box");
	document.onkeydown = function(e) {
	    e = e || event;
	    
	    // 获取定位移动的数值
	    var left = box.offsetLeft;
	    var top = box.offsetTop;
	    
	    switch(e.keyCode) {
	        case 37:
	            left -= 5;// 按下左键，移动5
	            break;
	        case 38:
	            top -= 5;
	            break;
	        case 39:
	            left += 5;
	            break;
	        case 40:
	            top += 5;
	            break;
	        default:// 都没有，则提示
	            console.log("请按下键盘上面的上下左右方向键进行移动");
	    }
		
	    // 设定样式
	    box.style.left = left + "px";
	    box.style.top = top + "px";
	}
	<!-- 百度keycode 键盘 -->
	<!-- ctrl+c为e.keycode == 67 e.ctrlkey == true -->
	<!-- switch()可简化一些如下操作
	if () {
	    
	} else if() {
	    
	} else if() {
	    
	} else if() {
	    
	} -->

```

----------------------------
待整理：

// document.write可解析html标签，如果放到文档流的最后，则里面的内容会把前面的覆盖掉

var oBox = document.getElementById('box');
var aP = oBox.getElementsByTagName('p');
// alert(aP.length)弹出aP（即p标签）的数量

document.getElementById('id名字');
// getElementById前必须是document

document.getElementsByClassName('class名字')
document.getElementsByTagName('标签名');
// getElementsByClassName和getElementsByTagName前不一定是document，如var aP = oBox.getElementsByTagName('p');


	var oBox = document.getElementById('box');
	// oBox.onclick = function(){
	// 	this.style.float = 'right';
	//  this.style.marginTop = '100px';// 不能用margin-top的写法
	//  this.style.cssText = 'width:300px;height:300px;margin-top:100px;'
	// }


var oNli = document.getElementById('nav_li');
var oHide = document.getElementById('hide');
oNli.onmouseenter = function(){
	oHide.style.display = 'block';
}
oNli.onmouseleave = function(){
	oHide.style.display = 'none';
}


// 通过id名字获取元素  返回 单个元素
var box = document.getElementById("box");

// 通过class名字获取元素  返回 类数组、集合
var parent = document.getElementsByClassName("parent")[0];

// 通过标签名字获取元素  （类似于标签选择器）
var tag = document.getElementsByTagName("div")[0];

// 通过name标签获取
var names = document.getElementsByName("user")[0];
names.value = "666666";
names.innerHTML = "同学们辛苦啦!";


// box.innerHTML = "This is Slice Teacher!<a href='#'>跳转百度</a>";
// box.innerText = "<p>我是段落</p>！";

var arr = ["This", "is", "String!", "slice"];
alert( Array.isArray(arr) );//判断arr是不是数组，是的话返回true;

遍历：类似python的for i in ...
for(var key in document) {
    console.log( key +"======="+ document[key]);
}

function $(idName) {
    if (idName && (typeof idName) == "string" ) {
        if( document.getElementById(idName) ) {
            return document.getElementById(idName);
        }
    }
    // if (idName && (typeof idName) == "string" )判断传入的参数是否是字符串，而不是数字
    // if( document.getElementById(idName) )判断传入的参数是否存在，存在为真，不存在为假
    // return "请输入正确的 id名字  数据类型为字符串！"
}

```js
transition + table键      渐变（用table变成以下3行，是为了兼容性）
例：
-webkit-transition: all 1s linear;
-o-transition: all 1s linear;
transition: all 1s linear;

transform: rotate(90deg); 旋转?
```




