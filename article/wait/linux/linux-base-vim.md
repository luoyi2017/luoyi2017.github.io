### Vim 编辑器

将 vi 替换为 vim 

```shell
[root@vagrant-centos65 ~]# echo 'alias vi=vim' >>/etc/profile
[root@vagrant-centos65 ~]# tail -1 /etc/profile
alias vi=vim
[root@vagrant-centos65 ~]# source /etc/profile
```

* vim 路径等配置知识

```txt
.viminfo        				 用户使用 vim 的操作历史
.vimrc           				 当前用户 vim 的配置文件
/etc/vimrc       				 系统全局 vim 的配置文件
/usr/share/vim/vim74/colors/     配色模板文件存放路径   
```

常用 vim 按键说明

```txt
[Ctrl] + [f]: 屏幕向下移动一页，相当于 [Page Down]按键
[Ctrl] + [f]: 屏幕向上移动一页，相当于 [Page Up]按键
0或功能键[Home]: 这是数字“0”，移动到这一行的最前面字符处
$或功能键[End]: 移动到这一行的最后面字符处
G: 移动到这个文件的最后一行
N[Enter]: n为数字。光标向下移动 n 行
:n1,n2s/word1/word2/g    n1和n2为数字。在第n1和n2行之间寻找word1这个字符串，并将该字符串替换为word2。例如：在100到200行之间查找 mac并替换为 MAC则用":10,200s/mac/MAC/g"  
:1,$s/word1/word2/g     从第一行到最后一行查找 word1 字符串，并将该字符串替换为 word2。
:1,$s/word1/word2/gc    从第一行到最后一行查找 word1 字符串，并将该字符串替换为 word2。且在替换前显示提示字符给用户确认（confirm）是否需要替换
x,X:   在一行字中，x 为向后删除一个字符（相当于[Del]按键），X 为向前删除一个字符（相当于[Backspace]）
dd:    删除光标所在的那一行
ndd:   n为数字。删除光标所在的向下n行，例如 20dd 则是删除 20 行
yy:    复制光标所在的那一行
nyy:   n为数字。复制光标所在的向下n行，例如20yy则是复制20行
p,P:   p为将已复制的数据在光标下一行粘贴，P为粘贴在光标上一行。例如：我目前光标在 20 行，且已经复制了 10 行数据。则按下 p 后，那 10 行数据会粘贴在原本的 20 行之后，也即由 21 行开始粘贴。但如果是按下 P 呢？那么原本的第 20 行会被变成 30 行
u:     复原前一个操作
[Ctrl] + r:     重做上一个操作
. :    小数点。重复前一个操作的意思。如果想要重复删除、重复粘贴等操作，按下小数点 "." 就好了

:w         将编辑的数据写入硬盘文件中
:w!        若文件属性为 “只读” 时，强制写入该文件。不过，到底能不能写入，还是跟你对该文件的文件权限有关
:q         离开 vi
:q!        若曾修改过文件，又不想存储，使用 "!" 为强制离开不保存的文件
注意： "!" 在 vi 中具有 “强制” 的意思
wq:        保存后离开，若为 "wq!" 则为强制保存后离开
:set nu    显示行号，设置之后会在每一行的前缀显示改行的行号
:set nonu  与 set nu 相反，为取消行号
```