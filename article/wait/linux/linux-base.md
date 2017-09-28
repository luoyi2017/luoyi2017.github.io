## linux基本命令


#### 路径
```
cd /tmp/aa    绝对路径，以正斜线“/”开头
cd ../tmp     相对路径，不以正斜线开头
pwd           查看当前所在的工作目录
```

#### 关机/重启  
shutdown命令可以安全地关闭或重启Linux系统，它在系统关闭之前给系统上的所有登录用户提示一条警告信息。该命令还允许用户指定一个时间参数，可以是一个精确的时间，也可以是从现在开始的一个时间段。精确时间的格式是hh:mm，表示小时和分钟，时间段由+ 和分钟数表示。系统执行该命令后会自动进行数据同步的工作。  

halt是最简单的关机命令，其实际上是调用shutdown -h命令。halt执行时，杀死应用进程，文件系统写操作完成后就会停止内核。  

reboot的工作过程与halt类似，其作用是重新启动，参数也与halt类似。reboot命令重启动系统时是删除所有的进程，而不是平稳地终止它们。因此，使用reboot命令可以快速地关闭系统，但如果还有其它用户在该系统上工作时，就会引起数据的丢失。所以使用reboot命令的场合主要是在单用户模式。
  
init是所有进程的祖先，其进程号始终为1。init用于切换系统的运行级别，切换的工作是立即完成的。定义在/etc/inittab文件设定。

>系统重新启动总结：shutdown -r now，reboot，init 6；
系统关机总结：half，shutdown -h now, init 0；

```
shutdown [选项] [时间] [警告信息]    该命令只能由超级用户使用
shutdown -k    并不真正关机而只是发出警告信息给所有用户
shutdown -r    关机后立即重新启动
shutdown -h    关机后不重新启动
  shutdown -h 15:00        设定电脑15:00就关机且不重启
  shutdown -r +10 (now)    10分钟后(马上)关机并且马上重启
shutdown -f    快速关机重启动时跳过fsck
shutdown -n    快速关机不经过init 程序
shutdown -c    取消一个已经运行的shutdown
shutdown -P    直接关闭电源
reboot         马上重启（或reboot halt）
halt           马上关机并且不重新启动
halt -f        没有调用shutdown而强制关机或重启
halt -i        关机或重新启动之前，关掉所有的网络接口
halt -p        立即关机，此选项为缺省选项（或poweroff）
init 0         马上关机，ssh无提示
init 1         默认没有用户和密码验证，单用户模式，忘记管理员密码用来修改密码，或者一些简单的排错
init 2         不带网络的文本模式
init 3         带网络的文本模式
init 4         保留，没用
init 5         带图形的模式
init 6         重新启动
原来一登录系统的时候，就是运行级别3，要想运行图像界面：1、 startx；2、 init 5；
要使用init对系统进行重启或者关机，建议先运行以下命令：sync 强制被改变的内容立刻写入磁盘
```

#### 切换目录
```
cd             直接回到当前用户的家目录
cd ~           直接回到家目录
cd ..          返回上级目录
cd .           回到当前目录
cd -           在两个目录之间切换
```

#### 查看文件
```
ls             查看当前目录包含哪里些内容
ls .. 	       查看上层目录包含哪里些内容
ls -a          查看当前目录中所有的文件，包括以点开头的隐藏文件
ls -l	       详细方式列出目录中的内容
ls -al         以长格式列出目录中所有的内容，包括隐藏文件
ls -ltr	       以长格式和时间及以时间反向顺序来显示目录中的内容
ls -R	       递归列出目录中的内容（注意R大写）
tree /home/    查看home目录的目录树结构
ls -lh         列出文件的同时查看文件的大小
```
#### 更新文件
> touch:更新文件的时间戳/如果目标不存在，会创建一个空文件

```
touch aa        如a存在则更新时间戳，不存在则创建空文件aa
```

#### 序列(sequence)
```
seq 100                   产生1到100的序列
seq 0 2 10                在0~10中产生以2为步长的序列，即0 2 4 6 8 10
seq 1 2 10 |xargs touch   创建或更新1到10内的偶数文件，很多命令不支持|管道来传递参数，所以用xagrs（资料待查）
[ly@vagrant-centos65 ~]$ seq 1 2 10 |xargs touch
[ly@vagrant-centos65 ~]$ ls
1  111  3  5  7  9  a
[ly@vagrant-centos65 ~]$ seq 2 2 10 |touch    #未使用xargs
touch: missing file operand
Try `touch --help' for more information.

mkdir 'seq 1 2 10'        创建出1到10内的奇数文件目录，不能与文件名相同，否则无法创建
[ly@vagrant-centos65 ~]$ mkdir 'seq 1 2 10'
mkdir: cannot create directory '1': File exists
mkdir: cannot create directory '3': File exists
mkdir: cannot create directory '5': File exists
mkdir: cannot create directory '7': File exists
mkdir: cannot create directory '9': File exists
[ly@vagrant-centos65 ~]$ cd 111
[ly@vagrant-centos65 111]$ mkdir 'seq 1 2 10'
[ly@vagrant-centos65 111]$ ls
1  222  3  5  7  9
```
#### 创建目录
```
mkdir b	          新建目录b
mkdir -p c/d	  新建多级不存在目录 已存在不会报错(静默模式)
```

#### 删除空目录
```
rmdir b           删除空目录b
rmdir -p c/d      删除多级目录
```

#### 拷贝
> 常用的2条命令:  cp -a(拷贝文件) ；  cp -ar（当我们需要拷贝目录的时候）

```
cp /dir1/file1	/dir2/
cp /dir1/file1	/dir2/file2
cp -a /dir1/file1 /dir2	      从dir１目录拷贝文件至２，过程中文件中所有的属性不变
cp -r /dir1/ /dir2            递归拷贝，即拷贝目录
\cp /dir1/file1 /dir2/file1   如果有重名的不讯问是否覆盖，直接覆盖
```

#### 移动文件
```
mv /dir1/file1	/dir2
mv /dir1/file1	/dir2/file2   移动并改名
mv /dir1/file1	/dir1/file2   改名字
```

#### 删除目录或文件
> 注意：  rm -rf /（强制删除根目录）绝对不要用

```
rm              删除文件
[ly@vagrant-centos65 ~]$ ls
10  111  22  222  3  4  5  6  7  8  9  a
[ly@vagrant-centos65 ~]$ rm 3
[ly@vagrant-centos65 ~]$ ls
10  111  22  222  4  5  6  7  8  9  a

rm -f           强制删除，忽略不存在的文件，从不给出提示。
rm -i           交互模式删除文件，删除文件前给出提示。
rm -r           删除目录及目录内的文件
[ly@vagrant-centos65 ~]$ ls
10  111  222  4  5  6  7  8  9  a
[ly@vagrant-centos65 ~]$ ls 222
1  2  222  3  5  7  9
[ly@vagrant-centos65 ~]$ rm -r 222
[ly@vagrant-centos65 ~]$ ls
10  111  4  5  6  7  8  9  a

rm -R           同上，删除目录及目录内的文件
rm -v           显示运行时详细信息
rm --help       显示命令在线帮助
rm --version    显示命令版本信息
```

#### 快捷键
```
crtl + c        强制结束进程
ctrl + d        发送一个exit信号，类似ctrl+c的操作，没有那么强烈，可在root用户和普通用户中来回切换，继续ctrl+d则会注销
[root@vagrant-centos65 ~]# su ly
[ly@vagrant-centos65 root]$ exit    #ctrl + d
[root@vagrant-centos65 ~]# logout   #ctrl + d
ctrl + l        清屏
ctrl + z        把当前任务调至后台
jobs            查看后台任务
fg 任务编号      将后台中的命令调至前台继续运行
bg 　任务编号    将一个在后台暂停的命令，变成在后台继续执行
ctrl + k        删除当前光标到后面的所有内容
ctrl + u        删除当前光标到前面的所有内容
```

#### 命令帮助
```
help pwd        内部命令获取简单帮助用help
ls --help       外部命令获取简单帮助用--help
man	--帮助手册
man man
man [123456789] command（资料待整理）
1	用户命令
2	内核系统调用（从用户空间到进入点内核的）
3	库函数
4	特殊文件和设备
5	文件格式和规范
6	游戏
7	规范、标准和其他页面
8	管理员用的命令帮助手册
man -k passwd   执行关键字搜索
man -f useradd useradd的man page 文件是哪个？
```

|按键  |进行工作|
|------|--------|
|空格键|向下翻一页|
|pagedown|向下翻一页|
|page up| 向上翻一页|
|home| 去到第一页|
|end| 去到最后一页|
|/ string |向下搜索string这个字符串|
|?string|向上搜寻string这个字符串|
|n,N|n继续下一个搜寻,N进行反向搜寻|
|q|退出man page|


#### 时间
> 常用的：date "+%Y-%m-%d %H:%M:%S"

```
date                            获取当前时间
date +%F                        获取当前日期
date +%F --date="30 day ago"    获取30天前日期
[root@vagrant-centos65 ly]# date +%F
2017-06-08
[root@vagrant-centos65 ly]# date +%F --date="30 day ago"
2017-05-09
date -R                         获取当前时间及时区
date +%z                        获取当前时区，中国在+8区，所以应为+0800
cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime   将时区改到上海
[ly@vagrant-centos65 ~]$ date -R; date +%z
Thu, 08 Jun 2017 06:03:34 +0000
+0000
[ly@vagrant-centos65 ~]$ su root
Password:
[root@vagrant-centos65 ly]# cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
cp: overwrite `/etc/localtime'? y
[root@vagrant-centos65 ly]# date -R; date +%z
Thu, 08 Jun 2017 14:06:13 +0800
+0800
date -s 20121019                设置日期
date -s 23:40:00                设置时间
[root@vagrant-centos65 ly]# date -s 15:40:00
Thu Jun  8 15:40:00 CST 2017
[root@vagrant-centos65 ly]# date -R
Thu, 08 Jun 2017 15:40:08 +0800
ntpdate 192.168.0.254           远程同步服务器时间 不建议大家手动修改时间
#linux同步时间的时间服务器?
/usr/sbin/ntpdate time.windows.com
date "+%Y-%m-%d %H:%M:%S"       获取"人性化"的时间
[root@vagrant-centos65 ~]# date "+%Y-%m-%d %H:%M:%S"
2017-06-08 16:28:38
date +%s                        当前时间戳，以秒计
echo $(($(date +%s)/86400))     计算距离1970－01－01到现在的天数
[root@vagrant-centos65 ~]# echo $(($(date +%s)/86400))
17325
```

#### 软件安装
> centos当中有一个yum的工具(ubuntu为apt) ， 这个工具相当于windows里面的360软件管理 ， 就相当于一键安装

#### yum配置
```
ls /etc/yum.repos.d/          查询是否有.repo后缀的配置文件，以repo结尾的都是yum源
扩展：
yum -y install lrzsz          先安装lrzsz
rz -bye                       上传到centos
```

#### yum命令
```
yum clean all                 清空以前的缓存列表
yum list                      更新列表
yum list |grep 软件关键字      查询软件
yum -y install 软件关键字      安装
yum -y remove 软件名称         卸载（会把一些依赖包给卸载了）
rpm -qa |grep nginx
rpm -e 软件具体名称            另一种卸载法，会发现依赖多，很不好卸载
rpm -e --nodeps 软件具体名称   不管依赖，强制卸载
扩展：
yum -y install nginx          安装nginx
/etc/init.d/nginx start       启动nginx服务（web网站）
ifconfig                      查看当前ip，浏览器内输入即可访问

```

#### 重点命令
```
whatis      查看命令的完整名称(一般名称里面有解释命令的含义)
whereis     查看命令所在的具体位置
find        查找文件
rpm         查看当前安全的软件（待查资料）
```

## 常用指令


- ls 显示文件或目录  
    - -l 列出文件详细信息l(list)  
    - -a 列出当前目录下所有文件及目录，包括隐藏的a(all)  
- mkdir 创建目录  
    - -p 直接创建多层目录
- cd 切换目录  
- touch 创建空文件  
- echo 类似print，且可创建带有内容的文件。  
- cat 查看文件内容  
- cp 拷贝  
- mv 移动或重命名  
- rm 删除文件  
    - -r 递归删除，可删除子目录及文件  
    - -f 强制删除  
- find 在文件系统中搜索某文件  
```
[root@vagrant-centos65 opt]# ls
aaa  aaab  mysql.txt  VBoxGuestAdditions-4.3.6  xxx
[root@vagrant-centos65 opt]# cd
[root@vagrant-centos65 ~]# find / -name 'aaa*'
/opt/aaab
/opt/aaa
```
- wc 统计文本中行数、字数、字符数  
```
# 统计出mysql.txt中有多少行（wc -m为统计chars）
[root@vagrant-centos65 opt]# cat mysql.txt |wc -l
103
```
- grep 在文本文件中查找某个字符串  
- rmdir 删除空目录  
- tree 树形结构显示目录，需要安装tree包  
- pwd 显示当前目录  
- ln 创建链接文件  
    - ln ** ** 硬链接，在你选定的位置上生成一个和源文件大小相同的文件
    - ln -s ** ** 软链接，类似创建快捷方式
    - 无论是软链接还是硬链接，文件都保持同步变化。
```
# 安装后键入命令python3提示不存在该命令，这是因为我们自定义了安装目录，因此需要添加文件链接：
ln -s /usr/local/python3/bin/python3 /usr/bin/python3
```
- more、less 分页显示文本文件内容  
- head、tail 显示文件头、尾10行内容  
- ctrl+alt+F1 命令行全屏模式  

####　系统管理命令  
- stat 显示指定文件的详细信息，比ls更详细  
- whereis 查找位置
```
[root@vagrant-centos65 opt]# whereis yum
yum: /usr/bin/yum /etc/yum /etc/yum.conf /usr/share/man/man8/yum.8.gz
```
- who/w 显示在线登陆用户，w更详细点  
- whoami 显示当前操作用户  
- hostname 显示主机名  
```
# 修改主机名
[root@vagrant-centos65 opt]# vim /etc/sysconfig/network
HOSTNAME=vagrant-centos65.vagrantup.com    -----修改此行
NETWORKING=yes
~
~
~
```
- uname 显示系统信息  
```
[root@vagrant-centos65 opt]# uname
Linux
[root@vagrant-centos65 opt]# uname -a
Linux vagrant-centos65.vagrantup.com 2.6.32-431.3.1.el6.x86_64 #1 SMP Fri Jan 3 21:39:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
- top 动态显示当前耗费资源最多进程信息 
```
[root@vagrant-centos65 opt]# top
top - 21:02:15 up 10:22,  2 users,  load average: 0.00, 0.00, 0.00
Tasks:  80 total,   1 running,  79 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    603576k total,   326028k used,   277548k free,    40420k buffers
Swap:  1254392k total,        0k used,  1254392k free,   200928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      20   0 19232 1492 1212 S  0.0  0.2   0:00.20 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.29 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0 
注解：top-当前时间；    up-系统启动了多长时间；    load average：平均负载；  
     80 total-当前有80个进程；    Mem-内存分配；    PID-进程号
``` 
- ps 显示瞬间进程状态
    - ps-a 显示其他用户启动的进程
    - ps-x 查看系统中属于自己的进程
    - ps-u 启动这个进程的用户和它启动的时间
```
[root@vagrant-centos65 opt]# ps axu |grep ssh
root       946  0.0  0.2  66608  1232 ?        Ss   10:39   0:00 /usr/sbin/sshd
root      1071  0.0  0.6  98320  4044 ?        Ss   10:39   0:00 sshd: root@pts/0 
root      1540  0.0  0.1   8388   844 pts/0    S+   21:26   0:00 grep ssh
``` 
- du 查看目录大小 
    - du -h /home 带有单位显示目录信息  
- df 查看磁盘大小 
    - df -h 带有单位显示磁盘信息  
- ifconfig 查看网络情况  
- ping 测试网络连通   
- netstat 显示网络状态信息  
```
# 查看22端口状态
[root@vagrant-centos65 opt]# netstat -tnlp |grep 22
tcp        0      0 0.0.0.0:22                  0.0.0.0:*                   LISTEN      946/sshd            
tcp        0      0 127.0.0.1:25                0.0.0.0:*                   LISTEN      1022/master         
tcp        0      0 :::22                       :::*                        LISTEN      946/sshd            
tcp        0      0 ::1:25                      :::*                        LISTEN      1022/master         
```
- man 获取帮助
- clear 清屏  
- alias 对命令重命名
    - alias showmeit="ps -aux" 
    - unaliax showmeit  解除
- kill 杀死进程，可以先用ps 或 top命令查看进程的id，然后再用kill+进程号杀死进程。  

#### 打包压缩相关命令
- gzip  
    - gzip ** 压缩为.gz格式的压缩文件，源文件会消失
    - gzip -c ** **.gz 压缩为.gz格式，源文件保留
    - gzip -r ** 压缩目录下所有的子文件，但是不能压缩目录
    - gzip -d **.gz 解压缩
    - gunzip **.gz 解压缩
- bzip2  
    - bzip2 ** 压缩为.bz2格式，不保留源文件
    - bzip2 -k ** 压缩之后保留源文件
    - 注：bzip2命令不能压缩目录
    - bzip2 -d **.bz2 解压缩
    - bunzip2 **.bz2 解压缩
    - bzip2 -k 解压缩，保留压缩文件
- tar: 打包压缩  
    - -c 归档文件  
    - -x 压缩文件  
    - -z gzip压缩文件  
    - -j bzip2压缩文件  
    - -v 显示压缩或解压缩过程 v(view)  
    - -f 使用档名  
    - tar -cvf /home/abc.tar /home/abc 只打包，不压缩  
    - tar -zcvf /home/abc.tar.gz /home/abc 打包，并用gzip压缩  
    - tar -jcvf /home/abc.tar.bz2 /home/abc 打包，并用bzip2压缩 
    - tar cvzf fff.tar.gz  dfddd    把dfddd这个目录打包成fff.tar.gz 打包目录
    - tar xvf  fff.tar.gz 解压目录到当前文件
    - tar xvfC fff.tar.gz /opt/ 解压到其他路径
    - 当然，如果想解压缩，就直接替换上面的命令 tar -cvf / tar -zcvf / tar -jcvf 中的“c” 换成“x” 就可以了。 

#### 关机/重启机器  
- shutdown  
    - -r 关机重启  
    - -h 关机不重启  
    - now 立刻关机  
- halt 关机  
- reboot 重启  
- Linux管道｜  
    - 将一个命令的标准输出作为另一个命令的标准输入。也就是把几个命令组合起来使用，后一个命令除以前一个命令的结果。  
```  
例：
grep -r "close" /home/* | more   在home目录下所有文件中查找，包括close的文件，并分页输出。  
```

#### Linux软件包管理  
- dpkg (Debian Package)管理工具，软件包名以.deb后缀。这种方法适合系统不能联网的情况下。比如安装tree命令的安装包，先将tree.deb传到Linux系统中。再使用如下命令安装:  
    - sudo dpkg -i tree_1.5.3-1_i386.deb 安装软件  
    - sudo dpkg -r tree 卸载软件  
    - 注：将tree.deb传到Linux系统中，有多种方式。VMwareTool，使用挂载方式；使用winSCP工具等；  
- APT（Advanced Packaging   Tool）高级软件工具。这种方法适合系统能够连接互联网的情况。  
依然以tree为例  
    - sudo apt-get install tree 安装tree  
    - sudo apt-get remove tree 卸载tree  
    - sudo apt-get update 更新软件  
    - sudo apt-get upgrade  
- 将.rpm文件转为.deb文件  
.rpm为RedHat使用的软件格式。在Ubuntu下不能直接使用，所以需要转换一下。  
    - sudo alien abc.rpm  

####　编辑器
- vim使用  
    - vim三种模式：命令模式、插入模式、编辑模式。使用ESC或i或：来切换模式。命令模式下：   
    - :q 退出  
    - :q! 强制退出  
    - :wq 保存并退出  
    - :set number 显示行号  
    - :set nonumber 隐藏行号  
    - gg 回到行首
    - G  跳到尾巴
    - yy 赋值一行  按p粘贴
    - dd 删除
    - u  撤回  
    - 在所有行之前添加“#”：
        - 将游标定位到第一行第一列
        - ctrl-v 进入纵向编辑模式
        - G 移动游标到最后一行第一列 可视块覆盖了第一列
        - I 进入行首插入模式，输入所要求字符“#”
        - ESC退出纵向编辑模式的同时所有选中的字符前都添加了“#”，回到命令模式
    - 在所有行之后添加“#”：
        - 以上第4步 I 改成 A ，其余步骤类似上面
    - 批量修改：
        - 以上第4步 I 改成 r ，其余步骤类似上面
    - yyp 复制光标所在行，并粘贴  
    - h(左移一个字符←)、j(下一行↓)、k(上一行↑)、l(右移一个字符→)  

#### 用户及用户组管理  
- /etc/passwd 存储用户账号  
- /etc/group 存储组账号  
- /etc/shadow 存储用户账号的密码  
- /etc/gshadow 存储用户组账号的密码  
- useradd 用户名  
- userdel 用户名  
- adduser 用户名  
- groupadd 组名  
- groupdel 组名  
- passwd root 给root设置密码  
- su root  切换到root用户
- su - root  
- /etc/profile 系统环境变量  
- bash_profile 用户环境变量  
- .bashrc 用户环境变量  
- su user 切换用户，加载配置文件.bashrc  
- su - user 切换用户，加载配置文件\/etc\/profile ，加载bash_profile  
- 更改文件的用户及用户组  
sudo chown [-R] owner[:group] {File|Directory}  
例如：还以jdk-7u21-linux-i586.tar.gz为例。属于用户hadoop，组hadoop  
- 要想切换此文件所属的用户及组。可以使用命令。  
sudo chown root:root jdk-7u21-linux-i586.tar.gz  

#### 文件权限管理  
- 三种基本权限  
    - R 读 数值表示为4  
    - W 写 数值表示为2  
    - X 可执行 数值表示为1  
```
例：jdk-7u21-linux-i586.tar.gz文件的权限为-rw-rw-r--  
-rw-rw-r--一共十个字符，分成四段。  
第一个字符“-”表示普通文件；这个位置还可能会出现“l”链接；“d”表示目录  
第二三四个字符“rw-”表示当前所属用户的权限。 所以用数值表示为4+2=6  
第五六七个字符“rw-”表示当前所属组的权限。 所以用数值表示为4+2=6  
第八九十个字符“r--”表示其他用户权限。 所以用数值表示为2  
所以操作此文件的权限用数值表示为662  
```
- 更改权限  
    - sudo chmod [u所属用户 g所属组 o其他用户 a所有用户] [+增加权限 -减少权限] [r w x] 目录名  
```
例如：有一个文件filename，权限为“-rw-r----x”   ,将权限值改为"-rwxrw-r-x"，用数值表示为765  
sudo chmod u+x g+w o+r filename  
上面的例子可以用数值表示  
sudo chmod 765 filename  
```


## 脚本常用命令

如果在工作中遇到故障怎么处理
* CPU被占满了怎么处理
* 内存被占满了怎么处理
* 带宽被占满了怎么处理
* 磁盘被占满了怎么办 两种情况 第一种有大文件占磁盘空间,磁盘空间不足    一个是有程序在疯狂的读写磁盘 导致其他程序打不开 


###  实用的命令  
####  小命令  
* ping    测试主机是否存活

```shell
[root@vagrant-centos65 ~]# ping IP地址
参数：
-c：次数
-s：数据包的大小
-i：间隔（单位秒）
```
 
echo 1 >/proc/sys/net/ipv4/icmp_echo_ignore_all   禁ping
* ip addr  和 ifconfig   查看 ip 地址

```shell
[root@vagrant-centos65 ~]# ifconfig
[root@vagrant-centos65 ~]# ip addr
```

nslookup 域名解析需要使用 nslookup www.baidu.com 211.157.15.189  
linux没有自带需要额外安装   
 
arp 负责将ip地址解析成mac地址  
[root@vagrant-centos65 ~]# arp 192.168.1.6  
tracepath和更为强大和更为广泛使用的程序traceroute一样，可以让我们看到IP数据报从一台主机传到另一台主机所经过的路由。  
使用场景,当你的网络出现问题的时候，一般运营商会要你提供一份路由跟踪的表 就是用这个命令来实现  
traceroute通过发送小的数据包到目的设备直到其返回，来测量其需要多长时间。一条路径上的每个设备traceroute要测3次。输出结果中包括每次测试的时间(ms)和设备的名称（如有的话）及其IP地址。 
在Windows系统下是执行tracert的命令：  
tracert hostname   
[root@vagrant-centos65 ~]# tracepath www.baidu.com   
[root@vagrant-centos65 ~]# traceroute 192.168.1.1  
[root@vagrant-centos65 ~]# traceroute www.baidu.com  

* 可以使用yum provides */nslookup反查 查询这个命令在哪个包里面 
  
#### top 以动态的方式查看进程状态  
top命令是Linux下常用的性能分析工具，能够实时显示系统中各个进程的资源占用状况，类似于Windows的任务管理器。  
下面详细介绍它的使用方法。  
load average 'w' 'uptime' 'free' 'find' 'iostat' '\/proc' cpuinfo meminfo zoneinfo mouts  
“需要进行调查法则”： 如果长期你的系统负载在 0.70 上下，那么你需要在事情变得更糟糕之前，花些时间了解其原因。  
“现在就要修复法则”：1.00 。 如果你的服务器系统负载长期徘徊于 1.00，那么就应该马上解决这个问题。否则，你将半夜接到你上司的电话，这可不是件令人愉快的事情。  
“凌晨三点半锻炼身体法则”：5.00。 如果你的服务器负载超过了 5.00 这个数字，那么你将失去你的睡眠，还得在会议中说明这情况发生的原因，总之千万不要让它发生。 
如果没有办法可以想了  就迁移你们的业务
常用交互命令  
CPU
* us 用户空间占用CPU百分比  
* sy 内核空间占用CPU百分比  
* ni 用户进程空间内改变过优先级的进程占用CPU百分比  
* id 空闲CPU百分比  
* wa CPU等待磁盘写入完成时间  
如果一台机器看到wa特别高，那么一般说明是磁盘IO出现问题，可以使用iostat等命令继续进行详细分析  
* hi 硬中断消耗时间   
由与系统相连的外设(比如网卡、硬盘)自动产生的。主要是用来通知操作系统系统外设状态的变化。比如当网卡收到数据包
的时候，就会发出一个中断。我们通常所说的中断指的是硬中断(hardirq)。  
* si 软中断消耗时间    
为了满足实时系统的要求，中断处理应该是越快越好。Linux为了实现这个特点，当中断发生的时候，硬中断处理那些短时间
就可以完成的工作，而将那些处理事件比较长的工作，放到中断之后来完成，也就是软中断(softirq)来完成。  
比如我们的U盘 在你弹出来的时候 有的时候需要等待比较长的时间  但是有的时候非常快  
* st: 虚拟机偷取时间  
st的名字很生动，偷取。。。是专门对虚拟机来说的，一台物理是可以虚拟化出几台虚拟机的。在其中一台虚拟机上用top查看发现st不为0，就说明本来有这么多个cpu时间是安排给我这个虚拟机的，但是由于某种虚拟技术，把这个cpu时间分配给了其他的虚拟机了。这就叫做偷取。  
```
[root@vagrant-centos65 ~]# top
参数： 
h 显示帮助画面，给出一些简短的命令总结说明。    
k 终止一个进程。系统将提示用户输入需要终止的进程PID，以及需要发送给该进程什么样的信号。一般的终止进程可以使用15信号；如果不能正常结束那就使用信号9强制结束该进程。默认值是信号15。在安全模式中此命令被屏蔽。    
m 切换显示内存信息。  
t 切换显示进程和CPU状态信息。  
c 切换显示命令名称和完整命令行。  
M 根据驻留内存大小进行排序。  
P 根据CPU使用百分比大小进行排序。  
T 根据时间/累计时间进行排序。    
W 将当前设置写入~/.toprc文件中。这是写top配置文件的推荐方法。
```

```
USER   启动进程用户身份
PID    进程号
%CPU   CPU的利用率
%MEM   内存的利用率
VSZ    预留分配的虚拟内存
RSS    真实分配的内存
TTY    在哪个终端启用的进程
STAT   当前进程的状态
D    ：运行中的进程
R    ：运行中的进程
S    ：可中断的睡眠
T    ：停止或被追踪
Z    ：僵尸进程
X    ：死掉的进程
<    ：高优先级别的进程
nVN  ：低优先级别的进程
s    ：是一个进程组，代表还有子进程
+    ：前台进程
START   进程启动时间
TIME    进程运行了多长时间
COMMAND 用什么命令启动的进程
```

#### ps 查看进程状态 以静态的方式  
```txt
参数：
-a：显示其他用户启动的进程
-u:启动这个进程的用户和它启动的时间
-x：查看系统中属于自己的进程
-f：显示进程的父子关系
USER   启动进程用户身份
PID    进程号
%CPU   CPU的利用率
%MEM   内存的利用率
VSZ    预留分配的虚拟内存
RSS    真实分配的内存
TTY    在哪个终端启用的进程
STAT   当前进程的状态
D    ：运行中的进程
R    ：运行中的进程
S    ：可中断的睡眠
T    ：停止或被追踪
Z    ：僵尸进程
X    ：死掉的进程
<    ：高优先级别的进程
nVN  ：低优先级别的进程
s    ：是一个进程组，代表还有子进程
+    ：前台进程
START   进程启动时间
TIME    进程运行了多长时间
COMMAND 用什么命令启动的进程
ps -elf
-e：   显示所有进程
-l：   长格式
-f：   全格式
找出内存消耗最多的前 10 名进程
ps -auxf | sort -nr -k | head -10
找出使用 CPU 最多的前 10 名进程
ps -auxf | sort -nr -k 3 | head -10
```


####  netstat 查看本机开放的端口  

​   `netstat`命令英语显示各种网络相关信息，如网络连接、路由表接口状态（Interface  Statistics），masquerade连接，多播成员（Multicast Memberships）等等。

``` txt
[root@vagrant-centos65 ~]# netstat
常用参数：
-a：（all）显示所有选项，默认不显示LISTEN相关
-t：（tcp）仅显示 tcp 相关选项
-u：（udp）仅显示 udp 相关选项
-l：仅列出有在 Listen（监听）的服务状态

-p：显示简历相关链接的程序名
-r：显示路由信息，路由表
-e：显示扩展信息，例如 uid 等
-s：按各个协议进行统计
-c：每隔一个固定时间，执行该 netstat 命令
注：LISTEC 和 LISTENING 的状态只有用 -a 或者 -l 才能看到
```

用法如下：

* 列出所有端口号（包括监听和未监听）

```shell
# netstat -a      列出所有端口
# netstat -at      列出所有 tcp 端口
# netstat -au      列出所有 udp 单口
```

* 列出所有处于监听状态的 sockets

```shell
# netstat -l      只显示监听端口
# netstat -lt     只列出所有监听 tcp 端口
# netstat -lu     只列出所有监听 udp 端口
# netstat -lx     之列吃所有监听 UNIX 端口
```

* 显示每隔协议的统计信息

```shell
# netstat -s      显示所有端口的统计信息
# netstat -st      显示 tcp 端口的统计信息
# netstat -sc      显示 udp 端口的统计信息
```

* 在 netstat 输出中显示 PID 和进程名称 

```shell
# netstat -pt
```

* 显示核心路由信息

```shell
# netstat -r
```

* 找出程序运行的端口

  并不是所有的进程都能找到，没有权限的会不显示，使用 root 权限查看所有的信息。

```shell
# netstat -ap | grep ssh
```

* 找出运行在指定端口的进程

```shell
# netstat -an | grep ':80'
```

* 显示网络接口列表

```shell
# netstat -i
```

```txt
-t tcp连接
-u udp
-n  不作反解
-l  侦听
-p  进程号
-a 所有
netstat -anp    TCP/UDP/socket监听列表，对应网络连接列表
netstat -tnp    TCP 的网络连接状态
netstat -tnlp   所有 TCP 的侦听列表
netstat -unp    UDP 的网络连接
netstat -unlp   UDP 的侦听列表
netstat -tunlp  TCP/UDP 侦听列表
netstat -rn     查询路由表
UNIX/类UNIX有三种连接：
1.TCP 面向连接
2.UDP 面向无连接
3.socket 通常也称作“套接字”，应用程序通常通过“套接字”相网络发出请求或者应答网络请求
```


#### nmap 端口扫描工具  

```txt
# 扫描目标ip的1-65535端口
[root@vagrant-centos65 ~]# nmap -p1-65535 192.168.1.6  

# 扫描网段中所有已激活的主机的端口，ip地址和物理地址
[root@vagrant-centos65 ~]# nmap -PS 192.168.1.0/24   
 
nmap -sO 192.168.1.19 确定目标机支持哪些IP协议 (TCP，ICMP，IGMP等):   特别慢?
nmap -O 172.16.85.14 扫描目标主机的操作系统  ?

# 全面扫描，主要是获取软件的版本号，在修复软件版本的时候需要用这个功能查看软件版本
[root@vagrant-centos65 ~]# nmap -T4 -A -v 192.168.1.13   
```

|服务|端口号|
|----|-------|
|HTTP|80|
|HTTPS|443|
|Telnet|23|
|FTP|21|
|ssh|22|
|SMTP|25|
|POP3|110|
|TOMCAT|8080|
|WIN远程登录|3389|
|mysqlserver|3306|
|nginx|80|

#### 常用指令的安装及使用

#### iostat

​   iostat通过观察设备的活跃时间和他们平均传输率之间的关系来监视系统的输入/输出设备负载。iostat生成的报告可以用于修改系统配置从而更好在物理硬盘间平衡输入/输出的报告。

```txt
安装 iostat
在 redhat / CentOS / Fedora
# yum install sysstat

在 Debian / Ubuntu / Linux Mint
$ sudo apt-get install sysstat
```

```txt
iostat
参数：
-O：只显示 I/O 操作进程
-b：批量显示，无交互，主要用作记录到文件
-n NUM：显示 NUM 次，主要用于非交互式模式
-d SEC：间隔 SEC 秒显示一次
-p PID：监控的进程 PID
-u USER：监控的进程用户

iotop 找出使用 I/O 最高的应用程序
iotop 常用快捷键：
左右箭头：改变排序方式，默认是按 I/O 排序
r：改变排序顺序
O：只显示有 I/O 输出的进程
p:进程 V 线程的显示方式的切换
a：显示累计使用量
q:退出
```

读取 iostat 信息

```shell
[root@vagrant-centos65 ~]# iostat
Linux 2.6.32-431.3.1.el6.x86_64 (vagrant-centos65.vagrantup.com)        03/04/2017      _x86_64_        (1 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.31    0.09    0.25    0.27    0.00   99.08

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               0.64        25.60        12.93     334738     169064
sdb               0.04         0.33         0.00       4264          0
```

第一部分包含了 CPU 报告

* %user：显示了在执行用户（应用）层时的 CPU 利用率
* %nice：显示在以 nice 优先级运行用户层的 CPU 利用率
* %system：显示在执行系统（内核）层时的 CPU 利用率
* %iowait：显示 CPU 在 I/O 请求挂起时空闲时间的百分比
* %steal：显示了当 hypervisor 正服务于另一个虚拟处理器时无意识地等待 CPU 所占用的时间百分比
* %idle：CPU 在 I/O 没有挂起请求时空闲时间的百分比

第二部分包含设备利用率报告

* Device：列出的 /dev 目录下的设备/分区名称
* tps：显示每秒传输给设备的数量。更高的 tps 意味着处理器更忙
* Blk_read/s：每秒从设备上读取的块的数量（KB,MB）
* Blk_wrtn/s：每秒写入设备上的块的数量（KB,MB）
* Blk_read：显示所有已读的块
* Blk_wrtn：显示所有写入的块

以 KB 或 MB捕捉 iostat

​   默认上，iostat 以 B 为单位衡量 I/O 系统。为了更便于阅读，我们可以 iostat 将报告转成以 KB 或者 MB为单位。只需要加入 -k 参数老创建以 KB 为单位，-m参数来创建以 MB 为单位。如下

```shell
[root@vagrant-centos65 ~]# iostat -k
Linux 2.6.32-431.3.1.el6.x86_64 (vagrant-centos65.vagrantup.com)        03/04/2017      _x86_64_        (1 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          30.23    0.00   12.59    0.14    0.00   57.04

Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda               0.40         9.64         8.16     166381     140880
sdb               0.03         0.12         0.00       2132          0
```

```SHELL
[root@vagrant-centos65 ~]# iostat -m
Linux 2.6.32-431.3.1.el6.x86_64 (vagrant-centos65.vagrantup.com)        03/04/2017      _x86_64_        (1 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          30.17    0.00   12.56    0.14    0.00   57.13

Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
sda               0.41         0.01         0.01        162        140
sdb               0.03         0.00         0.00          2          0
```

要扩展报告，我们可以在 iostat 后面跟上 -x选项

```shell
[root@vagrant-centos65 ~]# iostat -x
Linux 2.6.32-431.3.1.el6.x86_64 (vagrant-centos65.vagrantup.com)        03/04/2017      _x86_64_        (1 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          30.03    0.00   12.51    0.14    0.00   57.32

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
sda               0.10     1.90    0.24    0.17    19.15    16.53    88.02     0.01   22.21    8.59   41.45   5.55   0.23
sdb               0.00     0.00    0.03    0.00     0.25     0.00     8.49     0.00    1.24    1.24    0.00   1.23   0.00
```

iostat 的一些参数说明：

```txt
iostat -c 1 10         # 获取 CPU 状态
$iostat -d -k 1 10     # 查看 TPS 和吞吐量
iostat -d -x -k 1 10   # 查看设备使用率（%util）、响应时间（await）
```



### rz / sz     

​   rz、sz 是 Linux/Unix 同 Windows 进行 Zmodem 文件传输的命令行工具。优点：不再开一个sftp工具登入上去上传下载文件。

​   rz：运行该命令会弹出一个文件选择窗口，从本地选择文件上传到Linux服务器
​       安装命令

​   sz：将选定的文件发送（send）到本地机器

​   

* 编译安装

  root 账户登录后，依次执行以下命令：

```shell
cd /tmp
wget http://www.ohse.de/uwe/releases/lrzsz-0.12.20.tar.gz
tar zxvf lrzsz-0.12.20.tar.gz && cd lrzsz-0.12.20
./configure && make && make install
```

​   上面安装过程默认把 lsz 和 lrz 安装到了 `/usr/local/bin/`目录下，现在我们不能直接使用，下面创建软链接，并命名为 rz/sz

```shell
cd /usr/bin
ln -s /usr/local/bin/lrz rz
ln -s /usr/local/bin/lsz sz
```

* yum 安装

  root 账户登入后执行以下命令：

  ```shell
  yum install -y lrzsz
  ```

使用方法：

​   sz 命令发送文件到本地：

```shell
# sz filename
```

​   rz 命令本地上传到服务器：

```shell
# rz
```

​   执行命令后，在弹出框中选择要上传的文件即可

SecureCRT设置默认路径：
Options -> Session Options -> Terminal -> Xmodem/Zmodem ->Directories

Xshell设置默认路径：
右键会话 -> 属性 -> ZMODEM -> 接收文件夹

注意：SecureCRT可以方便的上传下载文件，而Xshell没有菜单选择








#### 查看流量(网卡流量用于检查应用程序使用流量情况)  
iftop 查看网卡流量使用 不能查询具体的应用程序使用了多少流量  
nethogs 查看进程使用了具体的流量 可以查出程序的PID  
用法 nethogs eth0(如果外网流量大就填外网，如果内网流量大就填内网)  
通过pid使用 ps axu 和lsof查出进程 以及程序文件里面什么问题造成的  
#### 查看磁盘读写  
yum -y install sysstat
iostat -x 1 10 查看当前磁盘读写 只能查看全局不能查看具体的程序使用了多少IO  
iotop 找出使用io最高的应用程序
du -hs /opt  查看目录大小

凌晨三点 有台机器的读写非常高  导致业务部正常
找出读写最高的进程出来 (pid)

查看IO占用情况 dd if=/dev/zero of=/test.dbf bs=8k count=300000  
-o：只显示有io操作的进程  
-b：批量显示，无交互，主要用作记录到文件。  
-n NUM：显示NUM次，主要用于非交互式模式。  
-d SEC：间隔SEC秒显示一次。  
-p PID：监控的进程pid。  
-u USER：监控的进程用户。  
iotop常用快捷键： 左右箭头：改变排序方式，默认是按IO排序。  
r：改变排序顺序。  
o：只显示有IO输出的进程。  
p：进程\/线程的显示方式的切换。  
a：显示累积使用量。  
q：退出  
ps -ef |主进程给找出来  

#### ss 能够快速的显示活动状态的套接字信息  
和netstat的功能一模一样，  
但是当你服务器的socket连接数量非常大的时候，使用netstat就是浪费你的生命 ss最大的优势就是他比netstat快很多  
常用命令  
显示ICP连接 ss -t -a  
显示sockets 摘要 ss -s  
列出所有打开的网络连接端口 ss -l  
查看进程使用的socket ss -pl  
找出套接字/端口应用程序 ss -pl|grep 3306  
显示所有的UDP sockets ss -u -a  
查看由多少个用户通过TCP或者其他的协议连接我的服务器  

#### lsof 查看当前被使用的文件  
lsof功能一般结合ps 工具一起使用可以查询正在执行的文件和脚本  

```shell
[root@vagrant-centos65 ~]# ss -h
Usage: ss [ OPTIONS ]
       ss [ OPTIONS ] [ FILTER ]
   -h, --help           this message
   -V, --version        output version information
   -n, --numeric        don't resolve service names
   -r, --resolve       resolve host names
   -a, --all            display all sockets
   -l, --listening      display listening sockets
   -o, --options       show timer information
   -e, --extended      show detailed socket information
   -m, --memory        show socket memory usage
   -p, --processes      show process using socket
   -i, --info           show internal TCP information
   -s, --summary        show socket usage summary

   -4, --ipv4          display only IP version 4 sockets
   -6, --ipv6          display only IP version 6 sockets
   -0, --packet display PACKET sockets
   -t, --tcp            display only TCP sockets
   -u, --udp            display only UDP sockets
   -d, --dccp           display only DCCP sockets
   -w, --raw            display only RAW sockets
   -x, --unix           display only Unix domain sockets
   -f, --family=FAMILY display sockets of type FAMILY

   -A, --query=QUERY, --socket=QUERY
       QUERY := {all|inet|tcp|udp|raw|unix|packet|netlink}[,QUERY]

   -D, --diag=FILE      Dump raw information about TCP sockets to FILE
   -F, --filter=FILE   read filter information from FILE
       FILTER := [ state TCP-STATE ] [ EXPRESSION ]
```

常用的`ss`命令

```txt
ss -l 显示本地打开的所有端口
ss -pl 显示每个进程具体打开的socket
ss -t -a 显示所有tcp socket
ss -u -a 显示所有的UDP socekt
ss -s 列出当前socket详细信息
ss -o state established '( dport = :http or sport = :http )'  列出所有http连接中的连接
ss src ADDRESS_PATTERN    使用IP地址筛选
    src：表示来源       ADDRESS_PATTERN：表示地址规则

ss dport OP PORT     端口筛选
  OP:是运算符
  PORT：表示端口
  dport：表示过滤目标端口、相反的有sport
  OP运算符如下：
  <= or le : 小于等于 
  >= or ge : 大于等于
  == or eq : 等于
  != or ne : 不等于端口
  < or lt : 小于这个端口 > or gt : 大于端口
```

#### lsof

​   `lsof`（list open files）是一个列出当前系统打开文件的工具。在[Linux](http://lib.csdn.net/base/linux)环境下，任何事物都以文件的形式存在，通过文件不仅仅可以访问常规数据，还可以访问网络连接和硬件。所以，`lsof`的功能很强大。一般 root 用户才能执行`lsof `命令，普通用户可以看见`/usr/sbin/lsof`命令，但是普通用户执行会显示“permission denied”。因此通过`lsof`工具能够查看这个列表对系统监测以及排错将是很有帮助的。

```shell
# yum -y install losf
```

​   在终端下输入`lsof`即可显示系统打开的文件，因为`lsof`需要访问核心内存和各种文件的身份，来运行它才能够充分地发挥其功能。即需要 root 权限

```shell
[root@vagrant-centos65 ~]# lsof
用法：
lsof abc.txt      显示开启文件abc.txt的进程
lsof directory    查找谁在使用文件目录系统
lsof -i:22        查找22端口被哪个进程占用
lsof -c abc       显示abc进程现在打开的文件
lsof -g gid       显示归属gid的进程情况
lsof -p 12        看进程为12的进程打开了哪些文件
lsof -u username  查看用户打开了哪些文件
lsof -i @192.168.1.111    查看远程已打开的网络连接（连接到192.168.1.111）
```

#### 总结：

​   1.当发现有程序或脚本占用 cpu 或内存比较高时，可以输入命令 `top` 来动态的查看 CPU 的占用情况，还可以用 `free -m` 命令查看内存使用情况，若为不正常的程序，可以用   `ps aux` 命令来找到脚本的路径，必须与研发部门沟通后，寻求是否能强杀，若能强杀，则用 `kill PID` 来强杀。其中老师上课讲了两个比较重要的命令：

* `ps -auxf | sort -nr -k 4 | head -10`        找出消耗内存最多的前10名进程

* `ps -auxf | sort -nr -k 3 | head -10`        找出使用CPU最多的前10名进程

  ​

  2.当出现 I/O 比较高时，可有 iostat 命令来查看，详细参数见上文内容

  ​

  3.当网络流量异常时，监控网卡流量可以用 `iftop` 命令，还可以用`nethogs eth0`查看进程使用的具体流量情况

  ​

  4.`ss`命令快速的显示活动状态的套接字

#### 获取本机的IP 

方法一：

```shell
[root@vagrant-centos65 ~]# ifconfig eth0 |grep Bcast |cut -d ":" -f2|cut -d " " -f1
192.168.191.2
[root@vagrant-centos65 ~]# ifconfig |grep Bcast |awk -F'[ :]+' '{print $4}'
192.168.191.2
```

方法二：

```shell
[root@vagrant-centos65 ~]# ifconfig |grep "inet addr:" |grep -v "127.0.0.1" |cut -d: -f2 |awk '{print $1}'
192.168.191.2
[root@vagrant-centos65 ~]# ifconfig -a |grep inet |grep -v 127.0.0.1 |grep -v inet6|awk '{print $2}' |tr -d "addr:"
192.168.191.2
[root@vagrant-centos65 ~]# ifconfig eth0 | grep "inet addr" | awk -F: '{print $2}' | awk '{print $1}'
192.168.191.2
```

#### Vim 编辑器

将 vi 替换为 vim 

```shell
[root@vagrant-centos65 ~]# echo 'alias vi=vim' >>/etc/profile
[root@vagrant-centos65 ~]# tail -1 /etc/profile
alias vi=vim
[root@vagrant-centos65 ~]# source /etc/profile
```

* vim 路径等配置知识

```txt
.viminfo                         用户使用 vim 的操作历史
.vimrc                           当前用户 vim 的配置文件
/etc/vimrc                       系统全局 vim 的配置文件
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













