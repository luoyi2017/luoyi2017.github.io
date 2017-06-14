## 表格
```html
<table>
    <tr>
        <td>111</td>
        <td>222</td>
    </tr>
    <tr>
        <td>111</td>
        <td>222</td>
    </tr>
</table>
```
|  属性  | 描述 |
|  ---   |  --- |
|   tr   | 代表行 |
|   td   | 代表列 |
| colspan| 跨列   |
| rowspan| 跨行   |



## 表单元素一  
```html
<form>
    使用form标签建立表单域，当提交数据的时候会收集表单域里面的数据然后发送给服务器
</form>
```



## input
赋予不同的type值可实现不同的表单控件  
| type类型 | 描述 |
| --- | --- |
| text      | 文本输入框  maxlength最大长度、onlyready只读、 disabled禁止、 placeholder |
| password  | 密码遮掩框                                                                |
| radio     | 单选按钮，checked默认选择                                                 |
| checkbox  | 多选框                                                                    |
| submit    | 收集表单域的name数据，然后提交到服务器上                                  |



## 下拉列表框
```html
<select>
    <option value="music">听音乐</option>
    <option value="running">跑步</option>
    <option value="study">学习</option>
    <option value="coffee">找小姐姐一起喝咖啡</option>
</select>
<!-- selected="selected"默认选中 -->
<!-- size="2"  实现两行下拉项 -->
<!-- disabled  禁止选择 -->
```
> selected默认选择一项



## 多行文本输入框(文本域) textarea
```html
<textare cols="30" rows="10"></textarea>
```
cols显示多少列，rows现实多少行



## 按钮
```html
<input type="button" value="自定义按钮标题" />
```


## 重置按钮
回到表单初始状态
```html
<input type="reset" value="重置表单" />
```


## 隐藏域
目的在于收集或发送信息 页面上面没有任何效果  CSRF跨域攻击在此作用
```html
<input type="hidden" value="ABCD1234" />
```



## label元素

为input元素定义一个标记，label元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。如果你在label元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动將焦点转到和标签相关的表单控件上
```html
<input id="man" type="radio" /><label for="man">男</label>
```



## form表单属性  
| 属性 | 描述 |
|  --- | ---  |
|action| 指定提交到哪个url上 |
|method| 提交方式，常用的**GET / POST** |



## 提交方式
| Method | Description |
|  ---   | ---         |
| GET    | URL地址栏上做拼接问号再加参数  |
| POST   | 隐式提交方式，看不到，可以抓包 |



## 格式化文本
* **pre** 可定义预格式化的文本。  
* **pre** 元素中的文本通常会保留空格和换行符。  
主要用于在网页上显示代码。



## 作业课题
* 写一个关于注册的网页