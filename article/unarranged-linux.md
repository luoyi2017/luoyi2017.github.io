* bash 环境中一些特殊符号总结

|  符号  |                 内容                 |
| :--: | :--------------------------------: |
|  #   | 批注符号，最常用在 script 当中，视为说明。气候的数据均不执行 |
|  \   |      转义字符，将“特殊字符或通配符”还原成一般字符       |
|  \|  |        管道（pipe），分隔两个管道命令的界定        |
|  ;   |   连续命令执行分隔符，连续性命令的界定（注意：与管道符不同）    |
|  ~   |              用户的主文件夹               |
|  $   |       使用变量前导符，即变量之前需要加的变量替代值       |
|  &   |    作业控制（job control），将命令变成背景下工作    |
|  !   |       逻辑运算意义上的 “非” （not）的意思        |
|  /   |            目录符号，路径分隔的符号            |
| >,>> |      数据流重定向，输出导向，分别是“替换”和“累加”      |
| <,<< |            数据流重定向，输入导向             |
| '  ' |           单引号，不具有变量替换的功能           |
|  ""  |             具有变量置换的功能              |
|  ``  |     两个" ` "中间为可以执行的命令，也可使用$()      |
| (  ) |         在中间为子 shell 的起始与结束         |
| {  } |             在中间为命令块的组合             |

注意：设置文件名时尽量不要用到上述的字符。

### Shell script



* 选取命令cut，grep

```shell
[root@vagrant-centos65 ~]# cut -d'分隔字符' -f fields
[root@vagrant-centos65 ~]# cut -c 字符范围
参数：
-d：后面接分隔字符，与 -f 一起使用
-f：依据 -d 分隔字符将一段信息切割成为数段，用 -f 去除第几段的意思
-c：以字符（characters）的单位取出固定字符区间
```

```shell
[root@vagrant-centos65 ~]# grep [-acinv] [--color=auto] '查找字符串' filename
参数：
-a：将 binary 文件以 text 文件的方式查找数据
-c：计算找到 '查找字符串' 的次数
-i：忽略大小写的不同，所以大小写视为相同
-n：顺便输出行号
-v：反向选择，即显示出 '查找字符串' 内容的那一行
--color=auto：可以将找到的关键字部分加上颜色显示
```

* 排序命令： sort，wc，uniq

```SHELL
[root@vagrant-centos65 ~]# sort [-fbMnrtuk] [file or stdin]
参数：
-f：忽略大小写的差异，例如 A 与 a 视为编码相同
-b：忽略最前面的空格符部分
-M：以月份的名字来排序，例如 JAN, DEC 等的排序方法
-n：使用 “纯数字” 进行排序（默认是以文字类型来排序）
-r：反向排序；
-u：就是 uniq，相同的数据中，仅出现一行代表
-t：分隔符，默认是用 [Tab] 键来分隔
-k：以那个区间（field）来进行排序的意思
```

```shell
[root@vagrant-centos65 ~]# uniq [-ic]
参数：
-i：忽略大小写字符的不同
-c：进行计数
```

```shell
[root@vagrant-centos65 ~]# wc [-lwm]
参数：
-l：仅列出多少行
-w：仅列出多少字（英文单字）
-m：多少字符
```

* 双向重定向：tee

```shell
[root@vagrant-centos65 ~]# tee [-a] file
参数：
-a：以累加（append）的方式，将数据加入 file 当中
```

* 字符转换命令：tr，col，join，paste，expand

```shell
[root@vagrant-centos65 ~]# tr [-ds] SET1 ...
参数：
-d：删除信息当中 SET1 这个字符串
-s：替换掉重复的字符
```

```shell
[root@vagrant-centos65 ~]# col [-xb]
参数：
-x：将 tab 键转换成对等的空格键
-b：在文字内有反斜杠（/）时，仅保留反斜杠最后接的那个字符
```

```shell
[root@vagrant-centos65 ~]# join [-ti12] file1 file2
参数：
-t：join 默认以空格符分隔数据，并且对比 “第一字段”的数据，如果两个文件的内容相同，则将两条数据连成一行，且第一份字段放在第一个
-i：忽略大小写的差异
-1：数字1:。代表第一个文件要用哪个字段来分析的意思
-2：代表第二个文件要用哪个字段来分析的意思
注意：在使用 join 之前，所需要处理的文件应该要实现经过排序 （sort）处理，否则有些对比的项目会被略过
```

```shell
[root@vagrant-centos65 ~]# paste [-d] file1 file2
参数：
-d：后面可以接分隔字符、默认是以 [tab] 来分隔的
- ：如果 file 部分写成 - ，表示来自 standard input 的数据的意思
```

```shell
[root@vagrant-centos65 ~]# expand [-t] file
参数：
-t：后面可以接数字。一般来说，一个 [tab] 按键可以用 8 个空格键替换，我们也可以自行定义一个 [tab] 按键代表多少个字符
```

* 切割命令：split

```shell
[root@vagrant-centos65 ~]# split [-bl] file PREFIX
参数：
-b：后面可接欲切割成的文件大小，可加单位，例如 b，k，m 等
-l：以行数来进行切割
PREFIX:代表前导符，可作为切割文件的前导文字
```

* sed 工具

```shell
[root@vagrant-centos65 ~]# sed [-nefr] [动作]
参数：
-n：使用安静（silent）模式。在一般 sed 的用法中，所有来自 STDIN 的数据一般都会被列出到屏幕上。但如果加上 -n 参数后，则只有经过 sed 特殊处理的那一行（或者操作）才会被列出来
-e：直接在命令行模式上进行 sed 的动作编辑
-f：直接将 sed 的动作支持写在一个文件内， -f filename 则可以执行 filename 内的 sed 动作
-r：sed 的动作支持的是扩展型正则表达式的语法（默认是基础正则表达式语法）
-i：直接修改读取的文件的内容，而不是由屏幕输出
动作说明：  [n1[,n2]]function
n1, n2:不见得会存在，一般代表选择进行动作的行数，举例说，如果我的动作是需要在 10 到 20 行之间进行的，则“ 10,20[动作行为]”

function 有下面这些参数:
a	：新增，a 的后面可以接字符串，而这些字符串会在新的一行出现（目前的下一行）
c	：替换，c 的后面可以接字符串，这些字符串可以替换 n1，n2之间的行
d	：删除，因为是删除，所以 d 后面通常不接任何参数
i	：插入，i 的后面可以接字符串，而这些字符串会在新的一行出现（目前的上一行）
p	：打印，也就是将某个选择的数据打印出来。通常 p 会与参数 sed -n 一起运行
s	：替换，可以直接进行替换的工作。通常这个 s 的动作可以搭配正则表达式！例如 1,20s/old/new/g 就是。
```

* awk工具

```shell
[root@vagrant-centos65 ~]# awk '条件类型1{动作1} 条件类型2{动作2} ...' filename
```

​	`awk`后面接两个单引号并加上大括号{}来设置想要对数据进行的处理动作。`awk`可以处理后续接的文件，也可以读取来自前个命令的 standard output 。但如前面所说，`awk`主要是处理每一行的字段内的数据，而默认的字段的分隔符为空格键或 [tab] 键。

### 启动Mysql脚本

```shell
#/bin/bash
#init
Port=3306
MysqlUser="root"
MysqlPass="123456"
CmdPath="/application/mysql/bin"

#startup fnction
start()
{
	if [ `netstat -lnt|grep "$Port"|wc -l` -eq 0 ]
		then
			printf "Starting Mysql...\n"
			/bin/sh ${CmdPath}/mysqld_safe --defaults-file=/data/${Port}/my.conf2>&1 > /dev/null &
	else
		printf "Mysql is running...\n"
	fi
}

#stop function
stop()
{
	if [ ! `netstat -lnt|grep "$Port"|wc` -l -eq 0]
		then
			printf "Stopping Mysql...\n"
			${CmdPath}/mysqladmin -u ${MysqlUser} -p${MysqlPass} -s /data/${Port}/mysql.sock shutdown
	else
		printf "Mysql is stopped...\n"
	fi
}

#restart funcation
restart()
{
	printf "Restarting Mysql...\n"
	stop
	sleep 2
	start
}

case "$1" in
start)
	start
	;;
stop)
	stop
	;;
restart)
	restart
	;;
*)
	printf "Usage: $0 {start|stop|restart}\n"
esac
```

