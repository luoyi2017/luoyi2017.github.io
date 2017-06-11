# 脚本常用命令
### Data：2017-06-10 by Author：ly
---

如果在工作中遇到故障怎么处理
* CPU被占满了怎么处理
* 内存被占满了怎么处理
* 带宽被占满了怎么处理
* 磁盘被占满了怎么办 两种情况 第一种有大文件占磁盘空间,磁盘空间不足    一个是有程序在疯狂的读写磁盘 导致其他程序打不开 


##  实用的命令  
###  小命令  
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
  
### top 以动态的方式查看进程状态  
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


###  netstat 查看本机开放的端口  

​	`netstat`命令英语显示各种网络相关信息，如网络连接、路由表接口状态（Interface  Statistics），masquerade连接，多播成员（Multicast Memberships）等等。

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


### nmap 端口扫描工具  

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

### 常用指令的安装及使用

#### iostat

​	iostat通过观察设备的活跃时间和他们平均传输率之间的关系来监视系统的输入/输出设备负载。iostat生成的报告可以用于修改系统配置从而更好在物理硬盘间平衡输入/输出的报告。

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

​	默认上，iostat 以 B 为单位衡量 I/O 系统。为了更便于阅读，我们可以 iostat 将报告转成以 KB 或者 MB为单位。只需要加入 -k 参数老创建以 KB 为单位，-m参数来创建以 MB 为单位。如下

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

​	rz、sz 是 Linux/Unix 同 Windows 进行 Zmodem 文件传输的命令行工具。优点：不再开一个sftp工具登入上去上传下载文件。

​	rz：运行该命令会弹出一个文件选择窗口，从本地选择文件上传到Linux服务器
​		安装命令

​	sz：将选定的文件发送（send）到本地机器

​	

* 编译安装

  root 账户登录后，依次执行以下命令：

```shell
cd /tmp
wget http://www.ohse.de/uwe/releases/lrzsz-0.12.20.tar.gz
tar zxvf lrzsz-0.12.20.tar.gz && cd lrzsz-0.12.20
./configure && make && make install
```

​	上面安装过程默认把 lsz 和 lrz 安装到了 `/usr/local/bin/`目录下，现在我们不能直接使用，下面创建软链接，并命名为 rz/sz

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

​	sz 命令发送文件到本地：

```shell
# sz filename
```

​	rz 命令本地上传到服务器：

```shell
# rz
```

​	执行命令后，在弹出框中选择要上传的文件即可

SecureCRT设置默认路径：
Options -> Session Options -> Terminal -> Xmodem/Zmodem ->Directories

Xshell设置默认路径：
右键会话 -> 属性 -> ZMODEM -> 接收文件夹

注意：SecureCRT可以方便的上传下载文件，而Xshell没有菜单选择








### 查看流量(网卡流量用于检查应用程序使用流量情况)  
iftop 查看网卡流量使用 不能查询具体的应用程序使用了多少流量  
nethogs 查看进程使用了具体的流量 可以查出程序的PID  
用法 nethogs eth0(如果外网流量大就填外网，如果内网流量大就填内网)  
通过pid使用 ps axu 和lsof查出进程 以及程序文件里面什么问题造成的  
### 查看磁盘读写  
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

### ss 能够快速的显示活动状态的套接字信息  
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
###lsof 查看当前被使用的文件  
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

### lsof

​	`lsof`（list open files）是一个列出当前系统打开文件的工具。在[Linux](http://lib.csdn.net/base/linux)环境下，任何事物都以文件的形式存在，通过文件不仅仅可以访问常规数据，还可以访问网络连接和硬件。所以，`lsof`的功能很强大。一般 root 用户才能执行`lsof `命令，普通用户可以看见`/usr/sbin/lsof`命令，但是普通用户执行会显示“permission denied”。因此通过`lsof`工具能够查看这个列表对系统监测以及排错将是很有帮助的。

```shell
# yum -y install losf
```

​	在终端下输入`lsof`即可显示系统打开的文件，因为`lsof`需要访问核心内存和各种文件的身份，来运行它才能够充分地发挥其功能。即需要 root 权限

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

### 总结：

​	1.当发现有程序或脚本占用 cpu 或内存比较高时，可以输入命令 `top` 来动态的查看 CPU 的占用情况，还可以用 `free -m` 命令查看内存使用情况，若为不正常的程序，可以用   `ps aux` 命令来找到脚本的路径，必须与研发部门沟通后，寻求是否能强杀，若能强杀，则用 `kill PID` 来强杀。其中老师上课讲了两个比较重要的命令：

* `ps -auxf | sort -nr -k 4 | head -10`        找出消耗内存最多的前10名进程

* `ps -auxf | sort -nr -k 3 | head -10`        找出使用CPU最多的前10名进程

  ​

  2.当出现 I/O 比较高时，可有 iostat 命令来查看，详细参数见上文内容

  ​

  3.当网络流量异常时，监控网卡流量可以用 `iftop` 命令，还可以用`nethogs eth0`查看进程使用的具体流量情况

  ​

  4.`ss`命令快速的显示活动状态的套接字

### 获取本机的IP 

老师提供的方法：

```shell
[root@vagrant-centos65 ~]# ifconfig eth0 |grep Bcast |cut -d ":" -f2|cut -d " " -f1
192.168.191.2
[root@vagrant-centos65 ~]# ifconfig |grep Bcast |awk -F'[ :]+' '{print $4}'
192.168.191.2
```

其它方法：

```shell
[root@vagrant-centos65 ~]# ifconfig |grep "inet addr:" |grep -v "127.0.0.1" |cut -d: -f2 |awk '{print $1}'
192.168.191.2
[root@vagrant-centos65 ~]# ifconfig -a |grep inet |grep -v 127.0.0.1 |grep -v inet6|awk '{print $2}' |tr -d "addr:"
192.168.191.2
[root@vagrant-centos65 ~]# ifconfig eth0 | grep "inet addr" | awk -F: '{print $2}' | awk '{print $1}'
192.168.191.2
```



