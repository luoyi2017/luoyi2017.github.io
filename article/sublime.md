
#### 快捷键及技巧
```
ctrl + alt + h     快速创建由html模板生成的html文件  
ctrl + alt + enter 圈选中内容后，快速添加标签，标签可在下方改成想要的，回车即可  
alt + shift + w    圈选中内容后，快速添加标签，标签直接修改，然后鼠标移走即可  
ctrl + d           先鼠标选中一个标签（尖括号内的），然后每按一次快捷键可多选中一个相同内容，然后可同时修改成想要的标签  
ctrl + z           撤销
ctrl + /           光标放当前行位置，注释当前行；圈中则注释圈中部分
ctrl+shift+↑       光标放当前行位置，将当前行上移
ctrl+shift+↓       光标放当前行位置，将当前行下移
li*3 + table       快速创建3个li标签（先输入li*3，然后按table，不须圈选）
li{666}*3 + table  快速创建3个<li>666</li>
li{$}*3 + table    快速创建3个连续标签：
                    <li>1</li>
                    <li>2</li>
                    <li>3</li>
li{$@5}*3 + table  从5开始，快速创建3个连续标签
li{$@-5}*3 + table 从5开始，倒着快速创建3个连续标签
                    <li>7</li>
                    <li>6</li>
                    <li>5</li>
li*3>a[href="#"] + table 快速创建3个li标签，每个标签内包含href="#"的a标签；
                    <li><a href="#"></a></li>
                    <li><a href="#"></a></li>
                    <li><a href="#"></a></li>
li*3>a[href="#"]>img+span{小米} + table
.logo + table      可快速创建出<div class="logo"></div>
db + table         在css中快速创建出display: block;
dib + table        在css中快速创建出display: inline-block;
```

#### 改html模板
首选项-浏览插件目录-SublimeTmpl-templates-html.tmpl

#### 改编辑器布局
视图-布局-列：2或按快捷键alt+shift+2


PackageControl.io  包下载

Emmet  （HTML 补全）emmet.io 快捷键的表

ColorPicker（调色板，颜色选择器）

SublimeTmpl（模板）

view in browser(以浏览器打开预览)

Anaconda （Python代码提示插件）

Djaneiro（Django语法补全）
http://blog.csdn.net/u013861109/article/details/53106074
安装插件时，先使用Ctrl+Shift+P（Tools→Command Palette...）打开控制面板，输入PackageControl  回车
选择Package Control:Install Package,回车。

div#box>p.p$ + table  快速创建出如下：
        <div id="box">
			<p class="p1"></p>
		</div>

div#box>p.p*3 + table  快速创建出如下：
        <div id="box">
			<p class="p"></p>
			<p class="p"></p>
			<p class="p"></p>
		</div>
        


ctrl + w 关闭
ctrl + shift + t 找到历史记录并重新打开

### 安装插件
```
Package Control:
    安装插件之前，我们需要首先安装一个Sublime 中最不可缺少的插件 Package Control, 以后我们安装和管理插件都需要这个插件的帮助。
安装Package Control：
    快捷键 " ctrl + ` " 打开Sublime的控制台 ,或者选择 View > Show Console 。
    在控制台的命令行输入框，把下面一段代码粘贴进去，回车 就可以完成Pacakge Control 的安装了。

    import urllib.request,os,hashlib; h = 'eb2297e1a458f27d836c04bb0cbaf282' + 'd0e7a3098092775ccb37ca9d6b2e4b7d'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

```


### Markdown插件
```txt
MarkdownEditing:
    是Markdown写作者必备的插件，它可以不仅可以高亮显示Markdown语法还支持很多编程语言的语法高亮显示。
安装MarkdownEditing：
    Package Control 安装成功后我们就可以使用它方便的管理插件了，首先使用快捷键 'ctrl + shift + p ' 进入到Sublime 命令面板，输入 "package install" 从列表中选择 "install Package" 然后回车。这时候Sublime开始请求远程插件仓库的索引,看到列表的更新之后输入 "markdown ed" 关键字，选择“MarkdownEditing" 回车。 插件安装完毕后需要重新启动Sublime插件才能生效。
    MarkdownEditing常用快捷键：
    ctrl + alt + k 插入链接
    ctrl + shift + k 插入图片

OmniMarkupPreviewer:
    用来预览markdown 编辑的效果，同样支持渲染代码高亮的样式。
安装OmniMarkupPreviewer：
    键入 "ctrl + shift + p" 进入sublime的命令界面，输入 "package install" 然后回车 ，键入 "ominmarkup" 选择OmniMarkupPreviewer , 回车。
    OmniMarkupPreviewer常用快捷键：
    ctrl + alt + o: 在浏览器中预览
```


### Terminal插件
    安装方法同上。
    快捷键：
    ctrl + shift + t

















