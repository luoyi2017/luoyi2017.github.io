# linux基本命令

### Data：2017-06-07 by Author：ly
---
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

