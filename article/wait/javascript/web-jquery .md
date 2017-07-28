# WEB基础之jQuery


<script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script>
    /*
        jQuery：
            jQuery写更少的代码，做更多的事情，繁琐的代码使用jQ几句代码就能搞定，并且有着非常好的兼容
            jQ1X 兼容IE678 还兼容CSS3
            jQ2X 不兼容兼容IE678
        

     */
    
    /*
        $符号
            jQuery对象
            $和jQuery是一个对象，两则完全相等
     */
    
    var box = document.getElementsByClassName("box");
    // alert(box);
    // box.innerHTML = "This is JavaScript";


    /*
        jQ获取元素
        参数：css选择器     字符串
        返回：jQ对象
        jQ对象只能使用jQuery的方法，原生js获取不能使用jQuery方法
     */
    
    // $('.box').html("<a href='http://baidu.com'>This is jQuery</a>"); // ==> innerHTML
    // $('.box').text("<a href='http://baidu.com'>This is jQuery</a>"); // innerText


    /*
        $(function() {}); jQuery参数传匿名函数 等价于$(document).ready(function() {});  等所有节点加载完成之后执行匿名函数里面的代码   —————— 比原生js的onload事件好用多了
     */
    // alert( $('.box').size() );  // == length;


    // $('.box').html("6666666666").hide(2000).show(1000);
    //hide(2000)为2秒后消失，show(1000)为1秒后显示
    

    /*
        js对象和jQ对象互转
            jQ转js对象只能拿单个  jQ.get(index);  or  jQ[index];
            js对象转jQ对象  $(原生的js获取到的元素);
     */
    
    // $(box)[0].innerHTML = "This is JS";
    // $(box)[1].innerHTML = "This is JS";
    // $(box)[2].innerHTML = "This is JS";
    // $(".box").eq(2).html("this is jQ");//jq对象的jq方法
    // $('.box').get(0).innerHTML = '这样可以吗';//jq对象的js方法
    

    /*
        在内容之后添加
            添加子元素的末尾

            $('#box').append('123456'); 追加子内容
            $('#box').append(   $("a")   )   把后面获取到的所有a转移到#box末尾
     */
    // $("#box").append( $('.link') ); // 转移元素
    // $('#box').append( "<a href='http://baidu.com'>跳转</a>" );  // 解析字符串标签

    /*
        在内容之前添加
            添加子元素最前面
     */
    // $('#box').prepend("我是prepend");


    /* 
        插入的同级关系
        before之前   after之后
     */
    // $('#box').after( $('.link') );


    /*
        清空元素empty
            清空所有内容包括子元素
     */
    // $('#box').empty();
    


    /*
        移除元素
     */
    // $('#box').remove();


    /*
        CSS样式
            只传参一表示获取样式的值
            参一和参二： 设置样式   样式属性, 样式值
            设定多个样式需要使用"对象"{}
     */
    // alert($('#box').css('background-color'));要使用全称，不能简写成background，有兼容性问题
    // $('#box').css('width', "500px");
    $('#box').css({
        width        : 150, 
        height       : "200px", 
        "background" : "pink",
        "border-radius" : "50%"
    });
    // alert( $('#box').height() );
    

获取CSS值
    // 当前元素距离整个网页的一个距离
    // alert($(".box").offset().left);
    

    /*
        距离定位父级的距离（不包括外边距）
     */
    // alert($('.box').position().top);

属性
    // alert( $('img').attr('class', "") );

    // 完全移除属性
    $('img').eq(1).removeAttr("title");

    // 添加class名字
    $('div').addClass("box");

    // 移除class名字
    // $('div').removeClass();

    /*
        事件
            去掉on，把事件名变为方法
            参数传事件函数
     */
    // $('div').mouseover(function() {
    //     alert(1);
    // })

    // $('ul li').click(function() {
    //     alert(1);
    // })//此写法后面的li标签不能弹
    
    function fn() {
        alert(1);
    }
    $('ul').on('click', 'li', fn);//此写法后面的li标签也能弹
    $('ul').append("<li>4</li>");
    $('ul').append("<li>5</li>");
    $('ul').append("<li>6</li>");
    $('ul').off('click', 'li', fn);//移除事件

效果
    // $("#box").slideUp(2000).slideDown(1000).hide(500).show(1000).fadeOut(1000).fadeIn(500);
    // $("#box").fadeTo(1000, 0.5);

    // $("#box").click(function(){
    //     $(this).hide(2000).show(2000);
    // })

    // $("#box").click(function() {
    //     $(this).hide(2000).show(2000, function() {   //回调函数
    //         $(this).hide(2000, function(){
    //             $(this).show(2000);
    //         })
    //     });
    // })

    // toggle，如果显示状态就变成隐藏，如果隐藏状态就变成显示
    // $("#box").toggle(2000).toggle(2000).toggle(2000)

    // slideUp向上收起，slideDown向下展开
    // $("#box").slideUp(2000).slideDown(1000);

    // fadeIn淡入，fadeOut淡出，fadeTo淡到什么程度
    // $("#box").fadeTo(1000, 0.5);

    // animate，动画，不支持背景颜色变化
    // $('#box').animate({
    //     "width": "500px",
    //     "height": "500px",
    //     "border-radius": "50%"
    // }, 2000);


    //定时器setInterval()

    //stop()会清空队列，animate本身会储存队列
    $('#box').hover( function() {
        $(this).stop().animate({
            "width": "500px",
            "height": "500px",
            "border-radius": "50%"
        }, 1000);
    }, function() {
        $(this).stop().animate({
            "width": "300px",
            "height": "300px",
            "border-radius": "0%"
        }, 800);
    });
    
    
    /*
        Ajax前后端进行交互，在不刷新页面的情况下。
        url: 请求哪个地址
        type: form 
     */
    
    setInterval(fn, 1000);//每隔1秒执行一次

    function fn() {
        var user = $('.user').val();
        var pass = $('.password').val();
        var DATA = "user="+user+"&pass="+ pass;
        
        var opt = {
            url: 'server.php',
            type: 'POST',
            data: DATA,//要发送什么数据给服务器
            // 请求成功则：
            success: function(data) {
                data = JSON.parse(data).teacher;
                $('body').html("");//先清空对象
                for(var key in data) {

                    $('body').append("<div>"+key+"====="+data[key]+"</div>");
                }
            },
            // 请求失败则：
            error: function(xhr, errorCode, errorInfo) {
                console.log(errorCode, errorInfo);
            }
        };

        $.ajax(opt);
    };

<?php


# $a = $_POST['user'];
# $b = $_POST['pass'];

# echo "This is PHP, 后台接收到的GET数据为 $a  ==========  $b";

$JSON = array(
        "teacher" =>
            array(
                    "slice"=> "Slice老师很帅！",
                )
    );

echo JSON_encode($JSON);

?>







