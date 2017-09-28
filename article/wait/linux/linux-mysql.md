
【-----未整理-----】：
【Linux基础一】
创建用户
useradd taka  创建普通用户taka
passwd taka   设置taka用户的密码

root 用户
visudo

username ALL=(ALL)  ALL    #username是普通用户名

普通用户下
sudo yum install man
sudo yum install vim

命令提示符
[用户@主机名 ~]#
[root@bogon ~]#
root 是Linux管理员
bogon 主机名
~ 家目录
# 超级用户的提示符
  普通用户的提示符是$

家目录 管理员的/root
其他用户的家目录在/home/目录下，例如user1的家目录 /home/user1/

pwd 当前目录
hostname 主机名
whoami 当前用户

cd 命令 跳转目录
常见用法：
cd 绝对路径
cd 相对路径
cd .. 回到上一级目录
cd / 跳到根目录
cd ~ 回到家目录
cd   回到家目录
cd . 当前目录
cd - 回到上一次目录

ls 查看当前目录中的内容
ll 详细列出当前目录中的内容

~家目录
/根目录  从逻辑上说系统中的所有一切都隶属于它
/bin		--存放所有用户都能执行的命令（二制文件）
/boot		--存放启动文件/内核的相关文件，一般独立成为一个分区。
/dev		--存放物理设备的目录
/etc		--存放配置文件
/home		--用户的家目录
/lib		--32位库文件
类似windows里的.dll
 ldd /bin/ls	--查看ls命令要调用哪些库，
 如果里面任意一个库不能使用，则ls命令无法使用
/lib64		--64位库文件
/lost+found	--分区修复时找回来的文件会存放在这里,
                  存放一些系统不正常关机的的文件残片
/media		--专门用于挂载的目录
/misc		--autofs备用文件夹
/mnt		--专门用于挂载的目录
/opt		--用于存放第三方软件可选目录
/proc		--当前内核的映射，一个虚拟的文件系统
/root		--管理root的家目录
/sbin		--管理员才能够执行的命令  root
/selinux	--selinux安全策略相关的文件
/sys		--内核在内存中的映像文件
/tmp		--临时目录，建议独立划成分区
/usr		--用于存放第三方软件
/var		--存放日志或者频繁修改的文件

mkdir(他建目录)
mkdir /a/		--新建一级目录
mkdir -p /c/d	--新建多级不存在目录
rmdir：删除空目录 
       #rmdir dir1 
       #rmdir -p a/b/c

touch filename 创建文件或修改文件时间

rm 删除文件或目录
rm -i 删除前提示用户进行确认
rm -r 删除指定目录及目录下的所有文件
rm -f 强制删除，没有提示确认

cat 查看文件内容
例如查看系统网络配置文件
cat /etc/sysconfig/network-scripts/ifcfg-eth0

more less



ls		--查看当前目录包含哪里些内容
ls ./		--查看当前目录包含哪里些内容
ls ../		--查看上层目录包含哪里些内容
ls -a 		--查看当前目录中所有的文件，包括以点开头的隐藏文件
ls -l		--详细方式列出目录中的内容
ls -al /	--以长格式列出目录中所有的内容，包括隐藏文件

b      块文件也叫设备文件也叫特殊文件
c      字符文件
d      目录文件
p      管道文件
f(-)   普通文件／文本文件
l      链接文件
s(socket)      unix/类unix套接字

clear 清屏
Ctrl+ L

shutdown 关机
shutdown -h now
reboot 重启系统

【linux第二节】
1.查看帮助
help -- 简单帮助
   command(out)  --help
   help command(build_in)

type 命令(type ls；   type pwd)
内部命令：help 内部命令
外部命令：外部命令 --help

例如：  
help pwd
ls --help

man 命令

less命令
使用技巧:

直接上下键到跳行
下一行： e
上一行： y
下一页： 空格键 或 f 或 z
上一页： b 或 w
/string ： 向下搜寻string这个字符串
？string : 向上搜寻string这个字符串
n,N  ：n 继续下一个搜寻，N进行反向搜寻
帮助信息：h----以上快捷方式都可查到
退出 ： q 


2.查找命令
命令搜索：
whereis 搜索命令的位置和帮助文档的位置
which 搜索位置和命令的别名


文件搜索：
find 
命令格式：
find [-path] -options [-print -exec]
sudo find / -name file1
path :要查找的目录，默认是当前目录
option:
-name 按文件名的某种规则的查找-----------find -name '*1'
      注意：要用字符串形式
-type 按文件类型查找（目录为d，文件为f）
-size 按文件大小查找


通配符：
*匹配任意内容
?匹配任意一个字符
[]匹配任意一个中括号内的字符

locate 
在数据库中按文件名搜索，搜索数据更快
搜索的数据库 /var/lib/mlocate/mlocate.db
先安装：
sudo yum install mlocate

初始化：
sudo updatedb

su root 切换用户------然后visudo进入编辑sudo
ctrl + d 退出root用户


字符串搜索命令：
grep ----------不要和echo混起来
在文件中搜索符合条件的字符串，包含匹配，包含字符串中的行
可使用正则表达式来匹配的内容。

命令格式：
grep [选项] 字符串 文件名

例：
grep -n root /etc/passwd 


常用选项：
-n 显示行号
-i 忽略大小写
-v 排除指定字符串


3.管道符 | 

输入流 输出流 

标准输出
echo 

输出重定向 
>   将内容写入一个文件中，如果这个文件存在则会删掉原来的内容
>>  将内容写入一个文件的末尾

例：
echo 12345 > file.txt
cat /etc/passwd >> file.txt

cat file.txt | grep root

4.压缩解压

linux标准压缩工具gzip bzip2

.gz格式压缩
gzip 源文件
压缩为.gz格式的压缩文件，源文件会消失

gzip -c 源文件 > 压缩文件
压缩为.gz格式，使用了-c，并使用输出重定向，源文件保留

gzip -r 目录
压缩目录下所有的子文件，但是不能压缩目录

.gz格式解压缩
gzip -d 压缩文件
gunzip 压缩文件


.bz2格式压缩
bzip2 源文件
压缩为.bz2格式，不保留源文件
bzip2 -k 源文件
压缩之后保留源文件

注：bzip2命令不能压缩目录

.bz2格式解压缩
bzip2 -d 压缩文件
bunzip2 压缩文件
解压缩，-k 保留压缩文件

打包命令 tar 

命令格式
tar -cvf 打包文件名 源文件

-c 打包
-v 显示过程
-f 指定打包后的文件名

解打包命令

命令格式
tar -xvf 打包文件名
-x 解包

.tar.gz 压缩格式
先打包再压缩
命令格式：
tar -zcvf 压缩包名.tar.gz  源文件
解压缩：
tar -zxvf 压缩包名.tar.gz

.tar.bz2压缩格式
tar -jcvf 压缩包名.tar.bz2 源文件
解压缩：
tar -jxvf 压缩包名.tar.bz2

压缩打包多个文件
例：
tar -zcvf /tmp/shishi.tar.gz file1 file2 file3

对于文件的后缀名，在linux上是不用后缀名来区分文件格式的，
后缀名只是给我们自己看

5.vi编辑器

vim 
yum install vim  安装vim
工作模式：
命令模式
输入模式
末行模式

模式之间切换，
多次按ESC可以进入命令模式
在命令模式下，按 i或o或a进入输入模式
在命令模式下，按shift+; ，末行出现:冒号则进入末行模式
按ESC回到命令模式


进入与退出：
vi filename 进入
当打开一个文件时处于命令模式

在末行模式下输入q退出文件
wq 保存退出
q! 不保存退出

移动光标
命令模式和编辑模式下都可以用上下左右键（或者h,j,k,l）

输入文本
在命令模式下
按 i 从光标所在位置前面开始插入资料
按 a 从光标所在位置后面开始输入资料
按 o 在光标所在行下方新增一行并进入输入模式
进入输入模式后，在最后一行会出现--INSERT--的字样

复制与粘贴
在命令模式下
yy 复制整行内容到vi缓冲区
yw 复制当前光标到单词尾内容到vi缓冲区
y$ 复制当前光标到行尾的内容到vi缓冲区
y^ 复制当前光标到行首的内容到vi缓冲区

p 读取vi缓冲区的内容，并粘贴到光标当前的位置

删除与修改
命令模式下
dd 删除光标所在行
x  删除光标所在字符
u  撤销上一次操作

保存文档
:q  结束编辑不保存退出，如果有修改不会退出
:q! 放弃所做的更改强制退出
:w  保存更改
:wq 保存更改并退出


补充：
touch bb/{f1,f2}.txt
touch {x,y,z}{1,2
touch {x,y,z}mn{1,2}
ll -h

进入vi之后默认是命令模式，按i进入编辑模式
编辑完成后点esc
如果要保存退出输入:wq
不保存退出输入:q!
上面两个命令中的冒号也要一起输入

ctrl+d 退出root用户

tar -zxvf ff1.tar.gz -C aa

【linux第三节】
查看别名alias 

定义别名：
alias rm='rm -i'

unalias rm取消别名

永久定义别名

vi ~/.bashrc
alias rm='rm -i'
用户可以定义属于自己的别名

vi编辑器

vim 
yum install vim  安装vim

vim 代码高亮显示
选项 >> 回话选项 >> 仿真  选择 Xterm     ANSI颜色，使用颜色方案两个选项都勾上。


工作模式：

命令模式
输入模式
末行模式

模式之间切换，
多次按ESC可以进入命令模式
在命令模式下，按 i或o或a进入输入模式
在命令模式下，按shift+; ，末行出现:冒号则进入末行模式
按ESC回到命令模式


进入与退出：
vi filename 进入
当打开一个文件时处于命令模式

在末行模式下输入q退出文件
wq 保存退出
q! 不保存退出

移动光标
命令模式和编辑模式下都可以用上下左右键（或者h,j,k,l）

输入文本
在命令模式下
按 i 从光标所在位置前面开始插入资料
按 a 从光标所在位置后面开始输入资料
按 o 在光标所在行下方新增一行并进入输入模式
进入输入模式后，在最后一行会出现--INSERT--的字样

复制与粘贴
在命令模式下
yy 复制整行内容到vi缓冲区
yw 复制当前光标到单词尾内容到vi缓冲区
y$ 复制当前光标到行尾的内容到vi缓冲区
y^ 复制当前光标到行首的内容到vi缓冲区

p 读取vi缓冲区的内容，并粘贴到光标下一行

删除与修改
命令模式下
dd 删除光标所在行
x  删除光标所在字符
u  撤销上一次操作
ctrl + r 

保存文档
:q  结束编辑不保存退出，如果有修改不会退出
:q! 放弃所做的更改强制退出
:w  保存更改
:wq 保存更改并退出

安装nano 编辑器

sudo yum install nano

进程管理：

查看所有进程
ps

ps aux

-a 显示一个终端所有进程
-u 显示进程的归属用户及内存使用情况
-x 显示没有控制终端的进程

ps 输出：

USER: 启动进程的用户
PID: 进程的ID号
%CPU: 进程占用的CPU百分比
%MEM: 进程占用的物理内存百分比
VSN: 进程使用的虚拟内存总量，单位KB
TTY: 终端ID 
STAT: 进程状态
START: 启动进程的时间
TIME: 进程消耗CPU的时间
COMMAND: 产生此进程的命令名

STAT常见状态：
R 运行， S 睡眠，T 停止，s 包含子进程，+ 位于后台

top 命令  q退出

选项：
-d 设置更新的时间间隔
-n 显示更新的次数，然后退出

top命令的交互模式当中可以执行的命令
h  显示交互模式的帮助
P  以CPU使用率排序，由大到小
M  按内存占有大小排序，由大到小
N  以进程ID大小排序，由大到小
q  退出top程序

Linux 的进程分为前台进程和后台进程
前台进程占用终端窗口

Ctrl + Z 让正在前台执行的进程暂停

jobs 获取当前的后台作业号

fg 将进程从后台调到前台执行
bg 将进程放到后台执行


例子：
[taka@tk-centos ~]$ cat shishi.py
#!/usr/bin/env python

import time
n = 0
while True:
    with open('ff.txt','a') as f1:
        f1.write(str(n)+'\n')
    n += 1
    time.sleep(2)

放在后台执行 python shishi.py &

杀死进程
kill -9 进程id





python的安装

python -V   查询本机python系统

sudo yum install epel-release
sudo yum install python34

【第四节】
传输文件的软件
sudo yum install lrzsz

rz 从windows上传到linux
sz 发送linux上的文件到windows

上传下载的目录
CRT上 选项 >> 会话选项 >> X/Y/Zmodem 


（sftp可传大文件）

#!/usr/bin/env python

[taka@tk-centos ~]$ ll
总用量 4
-rw-rw-r--. 1 taka taka   0 5月  17 12:49 ff
-rw-rw-r--. 1 taka taka 107 5月  17 12:54 ff.py

文件权限
-rw-rw-r--

r只读，w写，x是可执行

第1位为文件的类型
后面9位每3位为一组
第1组是u所有者的权限
第2组是g所属组的权限
第3组是o其他人的权限

修改权限
chmod 命令
u所有者,g所属组,o其他人
例：
chmod u+x ff.py

可以通过符号更改权限外，也可以通过数字来更改
r 对应数字 4
w 对应数字 2
x 对应数字 1

例：
chmod 755 ff.py

linux上的mysql安装

查看已经安装的mysql文件
rpm -qa | grep mysql

查看可以按的RPM包
yum list | grep ^mysql

安装mysql开发包及mysql服务端
sudo yum install mysql-devel mysql-server

启动mysql：
sudo service mysqld start
会出现非常多的信息，目的是对mysql数据库进行初始化操作


查看mysql服务是否开机自启动
chkconfig --list | grep mysqld

如果没有启动，可以通过下面语句来启动：
sudo chkconfig mysqld on

#通过命令给root账号设置密码为root
(注意：这个root账号是mysql的root账号，非Linux的root账号)
mysqladmin -u root password 'root'

通过 mysql -u root -p 命令来登录我们的mysql数据库了

进入mysql后
查看编码集
SHOW VARIABLES LIKE '%char%';

查看校对集
SHOW VARIABLES LIKE '%colla%';


改配置文件：

查看服务的状态
service mysqld status
关闭服务
sudo service mysqld stop


进入文件
sudo vi /etc/my.cnf

# 客户端：
[client]
default-character-set=utf8
# 服务端
[mysqld]
character-set-server=utf8
collation-server=utf8_general_ci

【第五节】

进入MySQL 

mysql -uroot -p
输入密码

mysql目录结构

bin 存放可执行文件
docs 文档
include 存放包含的头文件
lib 存放库文件
share 错误消息和字符集文件

data 存放数据文件

MySQL的配置文件
win上面 my.ini
linux上面 /etc/my.cnf

判断是否在哪个数据库里:
SELECT DATABASE();

mysql> SELECT DATABASE();
+------------+
| DATABASE() |
+------------+
| NULL       |
+------------+
1 row in set (0.00 sec)

mysql>

查看有哪些数据库：
SHOW DATABASES;


创建数据库    
CREATE  {DATABASE | SCHEMA} [IF NOT EXISTS] db_name
IF NOT EXISTS：如果不存在则，即如果存在不会出现报错信息

mysql> CREATE DATABASE `mydb`;
Query OK, 1 row affected (0.00 sec)

删除数据库
DROP {DATABASE | SCHEMA} [IF EXISTS] dbname;



打开数据库
USE 数据库名称

查看数据表列表
SHOW TABLES [FROM db_name]
SHOW TABLES FROM `mysql`;

创建数据表
CREATE TABLE [IF NOT EXISTS] table_name(
   column_name data_type,
)

mysql> CREATE TABLE `my_tb1`(
    -> `id` INT,
    -> `name` VARCHAR(20)
    -> );
Query OK, 0 rows affected (0.02 sec)


数据类型：
INT 
VARCHAR

MySQL 语句的规范
关键字与函数名称全部大写
数据库名称、表名称、字段名称全部小写，用反引号括起来
SQL语句必须以分号结尾

查看表的创建
 SHOW CREATE TABLE tb_name;(\G)

查看数据表结构
DESCRIBE tb_name;
SHOW COLUMNS FROM `my_tb1`;效果等同于DESCRIBE

删除表 ： DROP TABLE `my_table`;


修改数据表结构

添加单列

ALTER TABLE tb1_name ADD [COLUNM] col_name column_definition [FIRST|AFTER col-name]
注：column_definition为类型，即INT这些

例子：
mysql> ALTER TABLE `my_tb1`
    -> ADD `age` INT
    -> ;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> ALTER TABLE `my_tb1`
    -> ADD `number` INT FIRST
    -> ;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

添加多列
ALTER TABLE tbl_name ADD [COLUMN]
(col_name column_definition,...)

mysql> ALTER TABLE `my_tb1`
    -> ADD ( `a` INT,
    ->       `b` INT,
    ->       `c` INT)
    -> ;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> ALTER TABLE `my_tb1`
    -> ADD `x` INT AFTER `age`
    -> ;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

删除数据表
删除列
ALTER TABLE tbl_name DROP [COLUMN] col_name ;

mysql> ALTER TABLE `my_tb1`
    -> DROP `x`
    -> ;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql>

mysql> ALTER TABLE `my_tb1`
    -> DROP `a`,
    -> DROP `b`
    -> ;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

向数据表中输入数据
INSERT

INSERT [INTO] tb1_name [(col_name,..)] VALUES(val,...)


记录查找

SELECT * FROM tb1;


创建一个管理员用户taka账号，密码为 taka：
CREATE USER 'taka'@'%'IDENTIFIED BY 'taka';

给这个用户授予所有远程访问，这个用户主要用于管理整个数据库，备份，还原等操作。
GRANT ALL ON *.* TO 'taka'@'%';

使授权立即生效：
FLUSH PRIVILEGES;

====================================

linux:
退出mysql：可用\q


win7:
查下navicat

【第六节】
约束类型包括
NOT NULL (非空约束)
PRIMARY KEY(主键约束)
UNIQUE KEY (唯一约束)
DEFAULT （默认约束）
FOREING KEY （外键约束）

表结构的操作：
ALTER TABLE `tbname`

增加 ：ADD
删除 ：DROP 
修改 ：MODIFY

NULL  字段值可以为空
NOT NULL 字段值不能为空

NOT NULL (非空约束)

mysql> CREATE DATABASE `test`;
mysql> USE `test`;
Database changed
mysql> SHOW TABLES;
Empty set (0.00 sec)

mysql> CREATE TABLE `tb1`(
    -> `t_id` INT,
    -> `name` VARCHAR(20)
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> ALTER TABLE `tb1`
    -> ADD `age` INT NOT NULL
    -> ;

mysql> INSERT INTO `tb1`
    -> VALUES(3,'cc',20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO `tb1`
    -> VALUES(NULL,NULL,19);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO `tb1`
    -> VALUES(5,NULL,NULL);
ERROR 1048 (23000): Column 'age' cannot be null
mysql>
UNIQUE KEY (唯一约束)
保证记录的唯一性
唯一约束的字段可以为空值（NULL）
每张数据表可以存在多个唯一约束

添加唯一约束
ALTER TABLE tbl_name ADD [CONSTRAINT[symbol]]
UNIQUE [INDEX|KEY] [index_name] [index_type]
(index_col_name)

删除唯一约束
ALTERT TABLE tbl_name DROP {INDEX|KEY} index_name

mysql> CREATE TABLE `tb2`(
    -> `id` INT UNIQUE KEY,
    -> `name` VARCHAR(20) NOT NULL
    -> );

mysql> ALTER TABLE `tb2`
    -> MODIFY `id` INT NOT NULL UNIQUE KEY,
    -> ADD UNIQUE KEY(`name`)
    -> ;



PRIMARY KEY(主键约束)

主键保证记录的唯一性
主键自动为NOT NULL
每张数据表只能存在一个主键
NOT NULL + UNIQUE KEY

一个UNIQUE KEY 又是一个NOT NULL的时候，那么它被当做PRIMARY KEY 主键
当一张表里没有一个主键的时候，第一个出现的非空且为唯一的列被视为有主键。

mysql> CREATE TABLE `tb3`(
    -> `id` INT PRIMARY KEY,
    -> `name` VARCHAR(20) NOT NULL UNIQUE KEY
    -> );

mysql> ALTER TABLE `tb3`
    -> DROP PRIMARY KEY
    -> ;

mysql> ALTER TABLE `tb3`
    -> DROP KEY `name`
    -> ;


添加主键约束
ALTER TABLE tbl_name ADD [CONSTRAINT[sysbol]]
PRIMARY KEY [index_type] (index_col_name)


删除主键约束
ALTER TABLE tbl_name DROP PRIMARY KEY


AUTO_INCREMENT 
自动变好，且必须与主键组合使用
默认情况下，起始值为1，每次的增量为1
当插入记录时，如果为AUTO_INCREMENT数据列明确指定了一个数值，
则会出现两种情况，

情况一，如果插入的值与已有的编号重复，则会出现出错信息，
    因为AUTO_INCREMENT数据列的值必须是唯一的；
情况二，如果插入的值大于已编号的值，则会把该插入到数据列中，
    并使在下一个编号将从这个新值开始递增。也就是说，可以跳过一些编号。
    如果自增序列的最大值被删除了，则在插入新记录时，该值被重用。

mysql> ALTER TABLE `tb3`
    -> MODIFY `id` INT PRIMARY KEY AUTO_INCREMENT
    -> ;

mysql> INSERT INTO `tb3`(`name`)
    -> VALUES('aa'),
    ->       ('bb')
    -> ;
mysql> INSERT INTO `tb3`(`name`,`id`)
    -> VALUES ('cc',2);
ERROR 1062 (23000): Duplicate entry '2' for key 'PRIMARY'
mysql> INSERT INTO `tb3`(`name`,`id`)
    -> VALUES ('cc',5);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO `tb3`(`name`)
    -> VALUES ('dd')
    -> ;
初始值设置：

DEFAULT （默认约束）
插入记录时，如果没有明确为字段赋值，则自动赋予默认值


添加/删除默认约束
ALTER TABLE tbl_name ALTER [COLUMN] col_name
{SET DEFAULT literal | DROP DEFAULT}

mysql> CREATE TABLE `tb4`(
    -> `id` INT PRIMARY KEY AUTO_INCREMENT,
    -> `name` VARCHAR(20) NOT NULL
    -> )AUTO_INCREMENT=10
    -> ;

mysql> INSERT INTO `tb4`(`name`)
    -> VALUES('aa'),
    ->       ('bb')
    -> ;


mysql> ALTER TABLE `tb4`
    -> ADD `age` INT NOT NULL DEFAULT 18
    -> ;

mysql> ALTER TABLE `tb4`
    -> ALTER `name` SET DEFAULT 'xx'
    -> ;


FOREING KEY （外键约束）
外键约束要求数据表的存储引擎只能为InnoDB

查看当前mysql服务器支持的存储引擎
SHOW ENGINES \G

编辑数据表的默认存储引擎

MySQL配置文件  ->/etc/my.cnf

[mysqld]
default-storage-engine=INNODB

改完配置文件要重启服务

sudo service mysqld restart


写错时用\c

ALTER TABLE `tb4` ENGINE = INNODB;

【源码包安装python3.6】
编译安装
python官网只为Linux提供了源码，因此我下载?python3.6.1的源码压缩包
第一步，CentOS装好openssl静态库
键入以下命令：	yum install -y openssl-static
	若未装该静态库会导致python3自带的pip3安装失败
第二步，编译python3源码
0. CentOS安装GCC	yum install -y gcc
	yum groupinstall "Development tools"
	yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel
1. 先解压python3的源码包	wget http://python.org/ftp/python/3.6.1/Python-3.6.1.tar.xz
	tar xf Python-3.6.1.tar.xz
2. 配置安装路径	cd Python-3.6.1      //进入python3源码解压后的文件夹
 ./configure --prefix=/usr/local/python3  //默认配置文件并设置安装路径
3. 编译python3源码	make
4. 安装	make install
	最终若无错误提示，说明安装成功
5. 添加文件链接	安装后键入命令?python3?提示不存在该命令，这是因为我们自定义了安装目录，因此需要添加文件链接，命令如下：
	ln -s /usr/local/python3/bin/python3 /usr/bin/python3
6. 测试	键入命令：
	python3 -V
	会输出python3版本信息，说明python3安装完成



如果已经安装好了python34
sudo yum remove python34

【关于vi的补课内容】
给VIP会员的福利课
关于 vi 的常用操作 和 常见问题
vi是linux命令行下的最著名的编辑器之一，Vim常被称作“程序员的编辑器”，其功能如此强大以致许多人认为它就是个完整的IDE，
不过现在实际使用的都是vim，它是vi的改进版本，所以现在的vi基本上就是vim了。代码补完、编译及错误跳转等方便编程的功能特别丰富，在程序员中被广泛使用。
和Emacs并列成为类Unix系统用户最喜欢的编辑器
1.常见操作：
	1.移动：
	h j k l   分别是向  前/左  下  上  后/右
	gg  到第一行
	GG  到最后一行
	- + 上  下
	^ 非空格行首
	0 $  开始  末尾
	w e b  词首 词尾  词首 
	()  句子移动
	{}  段落移动
	H  顶部
	M  中间
	L  最后
	%  括号移动
	
	^F	 向下移动一屏
	^B	 向上移动一屏
	n^F	 向下移动n屏
	^D	 向下移动半屏
	^U	 向上移动半屏
	^E	 向屏幕顶端多滚动一行
	^L	 向屏幕底端多滚动一行
	
	显示行号：     :set number
	关闭行号：     :set nonumber
	nG 、   :n	 跳转到第n行
	1G 、 gg  、 :1	 跳转到编辑缓冲区的第一行
	G   、  :$	 跳转到编辑缓冲区最后一行
	 ``（两个反引号）
	 ‘’(两个单引号）

	2.编辑
	vi +[num] file          打开文件，并将光标置于第n行首
	vi + file               打开文件，并将光标置于最后一行首
	vi +/pattern file       打开文件，并将光标置于第一个与pattern匹配的字符串
	vi -r file                 （-r 即recover，恢复）
	vi -R file         　　  以只读模式启动vi    view file  
	
	3.插入
	i	 在当前光标位置前插入数据
	a	 在当前光标位置后插入数据
	I	 在当前行开头处插入数据
	A	 在当前行末尾处插入数据
	o	 在当前行下面出入一行
	O	 在当前行上面插入一行
	
	4.删除
	x	 删除当前光标处的字符
	X	 删除光标左边的字符
	D	 删除从当前光标到本行末尾的字符
	J	 删除两行之间的换行符 (亦可用于合并两行）
	dd	 删除当前行
	nx                  删除多个字符（n为删除的字符个数）
	dw                  删除1个单词
	d10w               删除10个单词
	d10W              删除10个单词，忽略标点符号
	db                   向后删除一个单词
	d2）                删除两个句子
	d5}                  删除5个段落
	dG 或 :.,$d        删除当前行到编辑缓冲区末尾的所有行
	dgg 或 d1G 或:1,.d       删除当前行到编辑缓冲区开头的所有行
	d^                   删除至该行的开始处
	df x                 删除至当前行中x所在的位置
	
	5.查找
	向前搜索： /
	向后搜索： ？
	n              重复上一条/或？命令，搜索方向相同
	N              重复上一条/或？命令，搜索方向相反
	*命令 : 将光标定位于字符串，按下*键，vi将会取当前光标所在的字符串并将它作用目标字符串进行搜索。
	#命令: 与*相反
	%:搜索与当前花括号、圆括号、方括号成对的符号
	
	6.替换
	r：精确替换一个字符（不进入输入模式）
	R：替换多个字符（以覆盖方式替换）。（先将光标移动到希望开始替换的位置，然后输入R。切换到输入模式，随后键入的每个字符都将替换当前行上的一个字符。）
	s：允许使用多个字符替换一个单个的字符（以插入方式替换）
	C：允许替换从当前光标位置到本行末尾的所有字符
	S 或 cc：以插入方式替换当前整行
	
	:s/pattern/replace/      　　   替换当前行
	s/pattern/replace/g              替换当前行所有
	:lines/pattern/raplace/          替换指定行
	:%s/pattern/replace/            替换所有行
	
	7.复制
	yw	 接出一个单词
	yb	 向后接出一个单词
	yy	 接出一行
	y$	 接出从当前字符到本行末尾的的文本
	y0	 接出从当前字符到这一行开头之间的文本
	
	:x,ycoz
	:x,ymz
	x，y，z都是行号。x，y是源行，z是目标行号。
	源行x,y被复制或移动，插入到z行的下面
	:m删除原始行，:co不删除原始行
	
	8.命令补全
	命令补全：Tab
	关键字补全：^N ^P

2.配置和要注意的问题	
	9.显示和设置
	显示所有选项的值： :set all
	显示一个选项的值： :set option?
	设置行号显示与否：             简写 :set nu  / :set no nu
	设置自动缩进：            简写 :set ai / :set no ai
	set list  行号
	set fileencoding   编码
	
	10.文件的保存的问题：
		.swp swo

	11.块操作
	ctrl + v  v	

	12.常见的带ctrl的操作
	ctrl + s   	终止终端显示
	ctrl + q	撤销终止终端显示
	ctrl + p	补全
	
	13.其他命令
	vimdiff
	
	14.Vim  配置问题/etc/vimrc
	1.设置缩进长度，设置缩进长度为4	set tabstop=4
		set softtabstop=4
	2.设置缩进空格长度	set shiftwidth=4
	3.设置自动缩进，每次缩进和上一行一样	set autoindent
	4.设置高亮	syntax on
	5.设置space代替tab	set expandtab
	
	14.分屏命令
	vsp 竖屏打开 
	ctrl+w+l/h  左右移动
	ctrl+w+j/k  上下移动
	

【外键及表关系】

一个学生属于某一个学院
一个学院有很多学生

外键 一对多

一个学生可以选多门课程
一个课程有很多学生

多对多
外键+主键

mysql> CREATE TABLE `department`(
    -> `id` INT PRIMARY KEY AUTO_INCREMENT,
    -> `name` VARCHAR(20) NOT NULL,
    -> `c_num` INT
    -> );

mysql> CREATE TABLE `student`(
    -> `s_id` INT PRIMARY KEY AUTO_INCREMENT,
    -> `name` VARCHAR(15) NOT NULL,
    -> `dept_id` INT,
    -> FOREIGN KEY (`dept_id`) REFERENCES `department`(`id`)
    -> );


mysql> CREATE TABLE `course`(
    -> `c_id` INT PRIMARY KEY AUTO_INCREMENT,
    -> `name` VARCHAR(20) NOT NULL,
    -> `dept_id` INT,
    -> FOREIGN KEY (`dept_id`) REFERENCES `department`(`id`)
    -> );

mysql> CREATE TABLE `stu_course`(
    -> `s_id` INT,
    -> `c_id` INT,
    -> PRIMARY KEY(`s_id`,`c_id`),
    -> FOREIGN KEY (`s_id`) REFERENCES `student`(`s_id`),
    -> FOREIGN KEY (`c_id`) REFERENCES `course`(`c_id`)
    -> );


约束类型包括
NOT NULL (非空约束)
PRIMARY KEY(主键约束)
UNIQUE KEY (唯一约束)
DEFAULT （默认约束）
FOREING KEY （外键约束）

外键约束
FOREIGN KEY
保持数据一致性，完整性
实现一对一或一对多关系

外键约束的要求：
数据表的存储引擎只能为InnoDB
外键列和参照列数据类型一致
外键必须关联到键上面去


一对一
一对多
多对多


操作数据：

插入数据：
方法一：
INSERT [INTO] table_name [(column_name,...)] 
{VALUES|VALUE} ({expr|DEFAULT},...),(...),...;

若省略列名称则所有列要依次赋值

对于自动编号的字段，插入“NULL”或“DEFAULT”系统将自动依次递增编号；

对于有默认值的字段，可以插入“DEFAULT”表示使用默认值；



方法二：
INSERT [INTO] tbl_name SET col_name={expr|DEFAULT},...;


更新记录（单表更新）
UPDATE  tb_name 
SET col_name1={expr1|DEFAULT}[,col_name2={expr2|DEFAULT}]...
[WHERE where_condition];

UPDATE `user` SET `age`=`age`+3;


删除记录

DELETE FROM tbl_name [WHERE where_conditon]; 

不添加WHERE则会删除全部记录

插入数据用VALUES法可一次输入多条数据，用SET一次只能一条数据；

【查询与事务】
查询：

SHOW TABLES;
先往表中插入足够数据，来支持我们后面的查询

先查询这些表中是否有数据，有的话先全部删掉
DELETE FROM `tb_name`;

在学院表中插入数据：
mysql> INSERT INTO `department`(`name`)
    -> VALUES('计算机'),
    ->       ('外国语'),
    ->       ('艺术'),
    ->       ('汉语言')
    -> ;
Query OK, 4 rows affected (0.19 sec)
Records: 4  Duplicates: 0  Warnings: 0

在学生表中插入数据：

mysql> INSERT INTO `student`(`name`,`dept_id`)
    -> VALUES('小明',1),
    ->       ('小红',3),
    ->       ('小花',3),
    ->       ('小新',4),
    ->       ('aa',1),
    ->       ('bb',3),
    ->       ('cc',3),
    ->       ('dd',4),
    ->       ('ee',4);

修改表名：
mysql> ALTER TABLE `user` RENAME TO `us`;
Query OK, 0 rows affected (0.01 sec)


删除外键
mysql> ALTER TABLE `course`
    -> DROP FOREIGN KEY `course_ibfk_1`;
删除列：
mysql> ALTER TABLE `course`
    -> DROP `dept_id`;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

往课程表中插入数据：
mysql> INSERT INTO `course`(`name`)
    -> VALUES('数学'),
    ->        ('英语'),
    ->        ('语文'),
    ->        ('物理');
Query OK, 4 rows affected (0.13 sec)
Records: 4  Duplicates: 0  Warnings: 0

往选修表中插入数据
mysql> INSERT INTO `stu_course`
    -> VALUES(1,1),
    ->       (1,3),
    ->       (1,4),
    ->       (2,4),
    ->       (4,3),
    ->       (4,4);
Query OK, 6 rows affected (0.13 sec)
Records: 6  Duplicates: 0  Warnings: 0

查询所有记录
SELECT * FROM `tb_name` 

查询选中列记录
SELECT col_name1,col_name2 FROM tb_name;      

 查询指定条件下的记录
SELECT col_name FROM `tb_name` WHERE 条件

查询后重新取列名
例如
SELECT `name` AS `姓名`, `dept_id` AS `学院编号` FROM `student`;

GROUP BY 分组查询 查询结果分组 ASC升序(默认)   DESC降序

SELECT `dept_id`,count(`dept_id`) FROM `student` GROUP BY `dept_id`;

SELECT `dept_id` AS `学院编号`,count(`dept_id`) AS `学生个数`
 FROM `student` GROUP BY `dept_id`;

对学生选修表进行分组查询:

查询各个学生报名的课程数
SELECT `s_id`,count(1) FROM `stu_course` GROUP BY `s_id`;

查询各课程的学生个数
SELECT `c_id`,count(1) FROM `stu_course` GROUP BY `c_id`;

HAVING分组条件(作用类似where)
HAVING 后的字段必须是SELECT后出现过的
mysql> SELECT `gender`,count(`gender`) FROM `stu_details` GROUP BY `gender` HAVING `gender`='f';

ORDER BY 排序 ASC升序(默认)   DESC降序
 SELECT * FROM `stu_course` ORDER BY `t_id` DESC;
 SELECT * FROM `student` ORDER BY `dept_id`;

LIMIT 限制返回的数量
SELECT * FROM `student` LIMIT 2
SELECT * FROM `student` LIMIT 2,2  
#前面一个2表示第3行（从0开始，0表示第一行），后一个2表示只显示2行；
SELECT * FROM `student` ORDER BY `s_id` DESC LIMIT 2,2;

子查询：

出现在其他SQL语句内的SELECT字句。

子查询（Subquery）
1)嵌套在查询内部
2)必须始终出现在圆括号内
3)可以包含多个关键字或条件

创建详细的学生信息表
mysql> CREATE TABLE `stu_details`(
    -> `id` INT,
    -> `age` INT,
    -> `gender` CHAR(1),#CHAR定长
    -> FOREIGN KEY(`id`) REFERENCES `student`(`s_id`)
    -> );
Query OK, 0 rows affected (0.63 sec)

插入数据到详细学生表中

mysql> INSERT INTO `stu_details`
    -> VALUES(1,18,'m'),
    ->       (3,25,'f'),
    ->       (4,20,'m'),
    ->       (5,30,'m'),
    ->       (2,19,'f'),
    ->       (6,24,'f');
Query OK, 6 rows affected (0.17 sec)
Records: 6  Duplicates: 0  Warnings: 0

求最大年龄
SELECT MAX(`age`) FROM `stu_details`;

求最小年龄
SELECT MIN(`age`) FROM `stu_details`;

求和
SELECT SUM(`age`) FROM `stu_details`;

求平均年龄
SELECT AVG(`age`) FROM `stu_details`;

平均年龄四舍五入只取整数部分
SELECT ROUND(AVG(`age`)) FROM `stu_details`;

平均年龄四舍五入保留指定多位小数
SELECT ROUND(AVG(`age`),2) FROM `stu_details`;
SELECT ROUND(AVG(`age`)) FROM `stu_details`;

查找出大于平均年龄的数据
SELECT * FROM `stu_details`  WHERE `age`>23;

将平均数的SQL语句作为子查询放入上一条语句中
SELECT * FROM `stu_details`  
WHERE `age`>(SELECT AVG(`age`) FROM `stu_details`);

修改列名：
mysql> ALTER TABLE `department`
    -> CHANGE `id` `dept_id` INT AUTO_INCREMENT;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0


内连接： 
[INNER| CROSS] JOIN

无条件内连接：
无条件内连接，又名交叉连接/笛卡尔连接
第一张表种的每一向会和另一张表的每一项依次组合

例：
SELECT * FROM `student` INNER JOIN `department`;

有条件内连接
在无条件的内连接基础上，加上一个ON子句
当连接的时候，筛选出那些有实际意义的记录行来进行拼接

在写条件时注意两张表的列名是否一样，
如果时一样的则要在前面加上表名，tb_name.colname这种形式存在
例：
mysql> SELECT * FROM `student` JOIN `department`
    -> ON `dept_id`=`d_id`;

mysql> SELECT * FROM `student` INNER JOIN `department`
    -> ON `student`.`dept_id`=`department`.`dept_id`;

mysql> SELECT * FROM `student` AS `s` INNER JOIN `department` AS `d`
    -> ON `s`.`dept_id`=`d`.`dept_id`;


有条件的外连接：
{ LEFT| RIGHT } [OUTER] JOIN

左外连接：
两张表做连接的时候，在连接条件不匹配的时候
留下左表中的数据，而右表中的数据以NULL填充

右外连接
对两张表做连接的时候，在连接条件不匹配的时候
留下右表中的数据，而左表中的数据以NULL填充

当我们插入一个学生的数据，但学生不属于任何学院时
如果要查看所有学生的数据就要用到外连接

mysql> INSERT INTO `student`(`name`,`dept_id`)
    -> VALUE('xx',NULL);
Query OK, 1 row affected (0.06 sec)


mysql> SELECT * FROM `student` LEFT JOIN `department`
    -> ON `dept_id`=`d_id`;

mysql> SELECT * FROM `student` RIGHT JOIN `department`
    -> ON `dept_id`=`d_id`;


UNION 联合

两个单独的查询凭借拼接在一起
两个查询并不要求列类型一致，只要求列数相同就可以了

mysql> (SELECT `name`,`dept_id` FROM `student`)
    ->  UNION (SELECT * FROM `department`);


事务：

为了保证数据库记录的更新从一个一致性状态变更为另一个一致性状态
使用事务来处理是非常必要。


mysql> CREATE TABLE `account`(
    -> `id` INT PRIMARY KEY AUTO_INCREMENT,
    -> `name` VARCHAR(20) NOT NULL,
    -> `balance` INT
    -> );
Query OK, 0 rows affected (0.52 sec)

mysql> INSERT INTO `account`(`name`,`balance`)
    ->  VALUES('shangdian',10000),
    ->        ('xiaoming',2000)
    -> ;
Query OK, 2 rows affected (0.09 sec)
Records: 2  Duplicates: 0  Warnings: 0


MySQL中，事务操作包括4个：
START TRANSACTION：开始一个新的事务
COMMIT：提交当前事务，做出永久改变
ROLLBACK：回滚当前事务，放弃修改


先把数据还原回去，再使用事务处理
mysql> UPDATE `account`
    -> SET `balance`= `balance`+50
    -> WHERE `name` ='xiaoming'
    -> ;
Query OK, 1 row affected (0.12 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> UPDATE `account`
    -> SET `balance`= `balance`-50
    -> WHERE `name` ='xiaoming'
    -> ;
Query OK, 1 row affected (0.04 sec)
Rows matched: 1  Changed: 1  Warnings: 0

这时我们直接关闭客户端，然后重新进去MySQL
再去数据库中查看account表中的数据

SELECT * FROM `account`

然后我重新开始一个事务：

mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> UPDATE `account`
    -> SET `balance`=`balance`-50
    -> WHERE `name`='xiaoming'
    -> ;
Query OK, 1 row affected (0.02 sec)
Rows matched: 1  Changed: 1  Warnings: 0

使用ROLLBACK;使数据的修改不生效，回到事务前的状态：
mysql> ROLLBACK;
Query OK, 0 rows affected (0.06 sec)

mysql> SELECT * FROM `account`;

做一次正确的操作：
mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> UPDATE `account`
    -> SET `balance`=`balance`-50
    -> WHERE `name`='xiaoming'
    -> ;
Query OK, 1 row affected (0.03 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> UPDATE `account`
    -> SET `balance`=`balance`+50
    ->
    -> WHERE `name`='shangdian'
    -> ;
Query OK, 1 row affected (0.00 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM `account`;

mysql> COMMIT;
Query OK, 0 rows affected (0.07 sec)

当COMMIT后，数据修改成功，ROLLBACK也没法回到之前了。

mysql> ROLLBACK;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM `account`;


【mysql补充】
使用LIKE 来匹配，%表示任意个数的任意字符

SELECT * FROM `student` WHERE `name` LIKE '小%';

mysql 支持正则 REGEXP


ALTER TABLE 

MODIFY 修改
ADD  增加
DROP 删除


mysql 

非空 NOT NULL
DEFAULT 默认
AUTO_INCREMENT  (必须与主键一起使用)
 
UNIQUE KEY  唯一
添加
mysql> ALTER TABLE `tb1`
    -> ADD UNIQUE KEY(`id`);
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0


PRIMARY KEY 主键 （在一张表中只能有一个主键）
添加主键 
mysql> ALTER TABLE `tb1`
    -> ADD PRIMARY KEY(`id`);
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

删除主键：
mysql> ALTER TABLE `tb1`
    -> DROP PRIMARY KEY;
Query OK, 0 rows affected (0.03 sec)
Records: 0  Duplicates: 0  Warnings: 0

删除唯一键：
mysql> ALTER TABLE `tb1`
    -> DROP KEY `id`;
Query OK, 0 rows affected (0.32 sec)
Records: 0  Duplicates: 0  Warnings: 0


想要把id这一列设置为自增长：
mysql> ALTER TABLE `tb1`
    -> MODIFY `id` INT PRIMARY KEY AUTO_INCREMENT;
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

添加外键：
mysql> ALTER TABLE `tb2`
    -> ADD CONSTRAINT `tb2_1_fk` FOREIGN KEY(`s_id`) REFERENCES `tb1`(`id`);

删除外键：
mysql> ALTER TABLE `tb2`
    -> DROP FOREIGN KEY `tb2_1_fk`;
Query OK, 0 rows affected (0.01 sec)
Records: 0  Duplicates: 0  Warnings: 0

删除普通键：
mysql> ALTER TABLE `department`
    -> DROP COLUMN `c_num`;（或者直接DROP `c_num`;？）

修改列名：
mysql> ALTER TABLE `department`
    -> CHANGE `id` `dept_id` INT AUTO_INCREMENT;

修改表名：
mysql> ALTER TABLE `user` RENAME TO `us`;

【json】

JSON的用处，用来在语言中间传输数据或信息。

Python 中的JSON

假如，我要传送一个字典出去，需要解决两个主要问题：
    怎么表达这个字典成一个字符串
    怎么把一个字符串，读回一个字典

因此，我们需要一个标准化的，字符串表达方式，例如JSON
​有点类似于，编码与解码。

基本接口
1.dumps(python对象)
通常是，字典，元祖，列表，字符串，数字
返回的是一个，JSON字符串

2. loads(string)
读取一个JSON字符串，如果满足格式标准，那么就会返回出如下四种之一
字典，列表，字符串，数字

3. dump(obj, file)
dumps + open + write
 
例：
import json
​
the_dict = {
	'a':123,
	'b':456
}
with open('json.txt', 'w') as f:
    json.dump(the_dict, f)

4. load(file)
loads + open + read
 
with open('json.txt','r') as f:
    print json.load(f)


JSON基本类型

1.对象（对应了Python的字典）
长相和Python的字典没区别

2.数组（对应了Python列表）
基本上和Python列表没区别
如果，把元祖导出，也会变成数组，但是再倒回来就变成了列表

3.字符串（对应Python字符串）
必须要要用双引号包围。其他和Python字符串类似。
