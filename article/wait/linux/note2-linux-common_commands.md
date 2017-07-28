
# 常用指令
### Data：2017-06-10 by Author：ly
---
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