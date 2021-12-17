# Linux
网址推荐：https://www.linuxcool.com/

## 一
#### 1、主要介绍
```bash
- 1970年（Unix元年，时间戳） Unix诞生
- Linux的开发作者，Linux之父，李纳斯·托瓦兹。
- Linux是开源（开放源代码。）的操作系统。
- copyleft: 代表无版权。copyright: 则代表有版权。
- opensource free: 源代码开放、软件谁都可以使用、谁都可以传播、谁都可以二次开发，使用GPL协议保护
- GPL: 通用版权许可证协议，如果软件被打上GPL，那么任何人都可以对这个软件进行修改，但是修改完之后必须将源码发布出来，以便更好的传承下去。(那Linux中的软件百分之80都是GPL提供)
- Linux内核使用GPL协议发布，内核也是开源，有了内核的加入，整个GNU的系统更加的完善。其实Linux完整叫法应该叫GNU/Linux，GNU的软件加上Linux内核。
```
- 系统特点
```bash
- 开放性（开源）、多用户、多任务、良好的用户界面、优异的性能与稳定性
多用户多任务：
单任务：一个任务，允许用户同时进行的操作任务数量；
多用户：多个用户，在登录计算机（操作系统），允许同时登录多个用户进行操作；
多任务：多个任务，允许用户同时进行多个操作任务；
Windows属于：单用户、多任务。
Linux属于：多用户、多任务。
```
- Linux分支
```bash
- Linux其实都是指的是发行版(Distribution version)就是使用Linux内核加上各种GNU的库文件、应用程序，构造而成的操作系统。
- Linux发行版介绍RHEL/Centos/Ubuntu/Suse
- Redhat 1993年，将Linux的内核进行编译安装相应软件进行发行。
- CentOS 社区企业级操作系统, 改与Redhat, 完全开源。
- Ubuntu 社区维护， 现在主要做手机系统和电脑桌面系统。
```

---
#### 2、虚拟软件
- 虚拟化技术
```bash
虚拟化技术:kvm，vmware，openstack，docker，k8s
```

#### 3 bash shell

```bash
命令解释器，就是一个软件，执行就是bash，可以输入命令，做交互，exit是退出

使用Shell实现对Linux系统的大部分管理，例如:
1.文件管理(文件创建，移动，复制，删除，编辑…)
2.权限管理(不同用户不通权限)
3.用户管理（创建，删除….）
4.磁盘管理（挂载）
5.网络管理
6.软件管理
```

- 提示符
```bash
[root@fanghao ~]#
# root：当前用户
# @ ：没有意义
#fanghao：主机名
# ~：家目录
# #:表示超级用户
[lqz@fanghao ~]$ 
```

- shell 基本语法
```bash
#  命令  选项  参数   三部分组成
ls -a  /temp      
ls --all
# 以下三个一样
ls -l -a
ls -la
ls -al

#ls 常见选项
-a  #查看目录下的所有文件，包括隐藏文件
-l  #以长格式的方式显示文件的详细内容
-h  #以人性化的方式显示内容，配合-l使用
-d  #只列出目录名，不列出目录以下的内容
-t  #按修改时间进行排序
-i  #显示文件的inode(该文件在该分区的一个编号)

tab，命令补全

```
- ifconfig 在centos7 中没有，需要安装
yum insatll net-tools -y


- 命令快捷键
```bash
Ctrl + a    #光标跳转至正在输入的命令行的首部
Ctrl + e    #光标跳转至正在输入的命令行的尾部
Ctrl + c    #终止前台运行的程序   ##################
Ctrl + d    #在shell中，ctrl-d表示推出当前shell。
Ctrl + z    #将任务暂停，挂至后台
Ctrl + l    #清屏，和clear命令等效。  ##############
Ctrl + k    #删除从光标到行末的所有字符
Ctrl + u    #删除从光标到行首的所有字符
Ctrl + r    #搜索历史命令, 利用关键字，Tab建选中,只能找到最近的一条
Ctrl + w    #按单词或空格进行向前删除
Ctrl + 左右建 #按单词或空格进行向前向后跳

#在命令行前加面加 "#" 则该命令不会被执行
```
#### 4 history
- -w 保存命令历史到历史文件
- -c 清空命令历史记录, 不会情况文件
- -d 删除命令历史的第 N 条行
```bash
# history查看历史命令
# !数字   快速执行数字那一行
# !yum    快速执行最近一条yum命令


# history -d 70  把历史记录的第70行删除
# history -c   清空所有记录（连到人家服务器，操作完了，执行一下）
# history -w   可以把 历史记录写到用户家路径的.bash_history文件中
```

#### 5 命令别名
```bash
 1 设置别名
 	alias www='ls /'  只在当前bashshell中生效
 2 永久生效（全局，局部）,
	echo "alias wk='ifconfig'" >> /etc/bashrc
 3 取消别名
 	unalias wk  
 4 如果写到配置文件中，取消的话unalias wk+去配置文件删除
 5 内置的别名：在环境变量的配置文件中放着
	alias ls
 6 /bin/ls -al /root   # ls 内置了别名
 
 7 获取帮助 -help
 
 8 man命令
 
```
- 命令大全
- http://man.linuxde.net/
- http://linux.51yip.com/


## 二 文件管理

- 目录介绍
```bash
1 linux 是单根 / 根路径，windows是多根
2 bin和sbin：bin普通用户命令，超级用户命令  都是usr下的文件夹软链接到根路径
3 home 、root：home普通用户的家路径，home下的用户名的文件夹
	-用户一登录系统，是在自己的家路径 jack--》/home/jack
	
/bin， 普通用户使用的命令 /bin/ls, /bin/date
/sbin，管理员使用的命令 /sbin/service,poweroff,useradd…
/home，普通用户的家目录, 默认为/home/username
/root，超级管理员root的家目录, 普通用户无权操作
```

- 目录之usr
```bash
/usr，相当于C:Windows
/usr/local，软件安装的目录，相当于C:Program
/usr/bin/，普通用户使用的应用程序(重要)
/usr/sbin，管理员使用的应用程序(重要)
/usr/lib，库文件Glibc 32bit
/usr/lib64，库文件Glibc 64bit

# 1 
df -h #df -h查看系统中文件的使用情况
Size 分割区总容量
Used 已使用的大小
Avail 剩下的大小
Use% 使用的百分比
Mounted on 路径地址
# 2
du -sh * 查看当前目录下各个文件及目录占用空间大小
du -sh /usr/
# 3 标准是实现自动化的基础
不通主机的相同的软件，都放在相同路径下，便于管理，实现自动化
现在一般安装的软件，不放在/usr/local下了

# 4 总共有一千来个命令
ls /usr/bin/ | wc -l
ls /usr/sbin/ | wc -l
# 5 查看命令依赖那些库文件
ldd /bin/ls
```
- /boot 存放的系统启动相关的文件，例如:kernel，grub(引导装载程序)
```bash

ls /boot
# linux内核
# 启动机器时可以选择的启动模式

```
- /etc 配置文件目录 
```bash
/etc，极其重要，后续所有服务的配置都在这个目录中
/etc/sysconfig/network-script/ifcfg-，网络配置文件
/etc/hostname，系统主机名配置文件,主机名很重要，有些特殊服务要依赖主机名，没有主机名会报错起不来；修改了要重启：reboot
/etc/resolv.conf，dns客户端配置文件,域名解析服务器，一般我们不配置，因为网卡的配置好了，会覆盖掉它，网卡的优先级高
/etc/hosts，本地域名解析配置文件，域名解析，先找自己的hosts，再去域名解析

# 1
/etc/hosts 对应windows C:windows/system32/drivers/etc/hosts,黑客钓鱼网站
# 2 测试修改（忽略 ） 
yum install httpd -y
systemctl stop firewalld
echo "fanghao NB" >/var/www/html/index.html
systemctl start httpd
```
- 可变的目录与临时目录
```bash
/var，存放一些变化文件，比如/var/log/下的日志文件,登陆日志
/var/tmp，进程产生的临时文件
/tmp，系统临时目录(类似于公共厕所)，谁都可以使用

# 1 查看登陆日志
cat /var/log/secure #查看登陆时间
# 2 进程产生的临时文件（360清理垃圾，就是会清理）
```
- 设备目录文件
```bash
/dev，存放设备文件，比如硬盘，硬盘分区，光驱，等等
/dev/sd 硬盘设备
/dev/null，黑洞设备，只进不出。类似于垃圾回收站
/dev/random，生成随机数的设备
/dev/zero，能远远不断的产生数据，类似于取款机，随时随地取钱


# 1 sda sdb sdc sda1 sdb4
linux中磁盘文件叫sd，第一个硬盘叫a，第二个叫b，sda1表示第一个磁盘的第一个分区，sdb4：第二个硬盘的第四个分区（服务可以插很多硬盘）
# 2 /dev/null 
ls >/dev/null
# 3 /dev/random 生成随机数
echo $RANDOM
echo lqz_$RANDOM
批量创建随机用户，批量设置密码
# 4 源源不断取数据
dd if=/dev/zero of=/opt/test.txt bs=1M count=1024
'''
dd：用指定大小的块拷贝一个文件，并在拷贝的同时进行指定的转换。
if=文件名：输入文件名，缺省为标准输入。即指定源文件。< if=input file >
of=文件名：输出文件名，缺省为标准输出。即指定目的文件。< of=output file >
 bs=bytes：同时设置读入/输出的块大小为bytes个字节。
 count=blocks：仅拷贝blocks个块，块大小等于ibs指定的字节数。
'''

ll /opt/test.txt
ll -h /opt/test.txt
```

- 虚拟的文件系统(如对应的进程停止则/proc下对应目录则会被删除)

```bash
/proc，反映系统当前进程的实时状态 :process
PS：类似于小汽车的仪表板，能够看到汽车是否有故障，或者是否缺油了。

# 介绍
ls /proc # 可以看到很多id号，pid号，进程号，唯一
ls 进程id号的文件夹
如果进程被关闭，id号的文件夹就没了
id号每次启动都不唯一，只有一个进程唯一，systemd 是进程号1的进程，所有进程都是基于它派生出来的

```
- 其他
```pyhton
#1 media:提供设备的挂载点，媒体文件
# linux 新增了盘符，需要手动挂载
# 把光盘里的数据，挂载到media目录
mount  /dev/cdrom /media/
# 2 mnt：提供设备的挂载点（同上）
# 3 opt：第三方工具，第三方软件默认安装的(mysql...)
# run :下有pid，log结尾的文件
ls /run
cat sshd.pid  # 进程运行的pid号,放在文件中
ps aux |grep sshd
# .lock文件的作用,锁机制
# 假设现在执行
yum install tree
# 再开一个窗口执行相同命令
yum install tree
'''
Another app is currently holding the yum lock; waiting for it to exit...
  The other application is: yum
    Memory :  71 M RSS (470 MB VSZ)
    Started: Tue Aug 18 00:26:31 2020 - 00:24 ago
    State  : Sleeping, pid: 6191
'''
cat /run/yum.pid
```

- 路径

```bash
1 . ..  相对路径，. 是当前，..是上一级
2 坑：带斜杠和不带斜杠
    cd /usr # 根路径下的usr
    cd usr  # 当前路径下的usr
3 执行当前路径下的某个文件
	./xx linux
    xx   windows
4 ~当前用户的家路径：root   /root   jack  /home/jack
5 当前路径
	pwd
```

- 创建/复制/移动/删除
```bash

1.文件创建命令touch
	# touch file	#无则创建,有则修改时间
	# touch file2 file3
	# touch /home/od/file4 file5
	# touch file{a,b,c}	#{}集合，等价 touch a b c
	# touch file{1..10}
	# touch file{a..z}
	
2.目录创建命令mkdir
# 选项：-v 显示详细信息  -p 递归创建目录
    # mkdir dir1
    # mkdir /home/od/dir1 /home/od/dir2
    # mkdir -v /home/od/{dir3,dir4} 
    # mkdir -pv /home/od/dir5/dir6
    # mkdir -pv /home/{od/{diu,but},boy}

3.以树状显示目录结构命令tree
# 选项: -L: 显示目录树的层级
    # tree /home/od/    #显示当前目录下的结构

4.cp复制
#选项： 
    -v:详细显示命令执行的操作 
    -r: 递归处理目录与子目录 
    -p: 保留源文件或目录的属性
    # cp file /tmp/file_copy
    # cp name /tmp/name         #不修改名称
    # cp file /tmp/             #不修改名称
    # cp -p file /tmp/file_p    #-p保持原文件或目录的属性
    # cp -r  /etc/ /tmp/        #复制目录需要使用-r参数, 递归复制
    # cp -rv /etc/hosts /etc/hostname /tmp  #拷贝多个文件至一个目录
   	# cp -rv /etc/{hosts,hosts.bak}
	# cp -rv /etc/hosts{,-org}
	
5.mv移动

# mv file file1             #原地移动算改名
# mv file1 /tmp/            #移动文件至tmp目录
# mv /tmp/file1 ./          #移动tmp目录的文件至当前目录
# mv dir/ /tmp/             #移动目录至/tmp目录下
# touch file{1..3}
# mv file1 file2 file3 /opt/    #移动多个文件或至同一个目录
# mkdir dir{1..3}
# mv dir1/ dir2/ dir3/ /opt     #移动多个目录至同一个目录

6.rm删除

#选项：-r: 递归 -f: 强制删除 -v: 详细过程
# rm  file.txt      #删除文件, 默认rm存在alias别名，rm -i所以会提醒是否删除文件
# rm -f file.txt    #删除文件, 不提醒
# rm -r dir/        #递归删除目录，会提示
# rm -rf dir/       #强制删除目录,不提醒(慎用)
#1.rm删除示例
# mkdir /home/dir10
# touch /home/dir10/{file2,file3,.file4}
# rm -f /home/dir10/  //不包括隐藏文件 
# ls /home/dir10/ -a
. .. .file4
#2.rm删除示例2
# touch file{1..10}
# touch {1..10}.pdf
# rm -rf file 
# rm -rf .pdf
```

- 查看文件内容(cat tac less more head tail tailf grep …)

```bash
1.cat
    # cat pass      #正常查看文件方式
    # cat -n pass   #-n显示文件有多少行
    # cat -A pass   #查看文件的特殊符号,比如文件中存在tab键
    # tac pass      #倒序查看文件
    
    # 文件就会写入ads 和 adf 两行
    cat >> test2.txt <<EOF
    ads
    adf
    EOF

2.less、more
    # less /etc/services    #使用光标上下翻动，空格进行翻页，q退出
    # more /etc/services    #使用回车上下翻动，空格进行翻页，q退出(有百分比)

3.head 查看头部内容，默认前十行
    # head pass     #查看头部内容，默认前十行
    # head -n5 pass #查看头部5行，使用-n指定
    # ps aux | head -5 # 只看头部5个进程

4.tail查看文件尾部，默认10行
    # tail pass  # 查看文件尾部，默认10行
    # tail -20 /var/log/secure  # 查看文件尾部20行
    # tail -f /var/log/messages #-f动态查看文件尾部的变化
    # tailf /var/log/messages   #查看文件尾部的变化
    # ps aux | tail -2

5.grep过滤文件内容
    # grep "^root" pass     #匹配以root开头的行
    # grep "bash$" pass     #匹配以bash结尾的行
    # grep -i "ftp" pass    #忽略大小写匹配
    # grep  -Ei "sync$|ftp" pass    #匹配文件中包含sync结尾或ftp字符串
    # grep -n -A 2 "Failed" /var/log/secure #匹配/var/log/secure文件中Failed字符串,并打印它的下2行
    # grep -n -B 2 "Failed" /var/log/secure #匹配/var/log/secure文件中Failed字符串,并打印它的上2行
    # grep -n -C 2 "Failed" /var/log/secure #匹配/var/log/secure文件中Failed字符串,并打印它的上下2行

# 上翻，下翻
control+b：下翻
control+f：上翻
```

- 联网下载文件(wget、curl)、文件上传与下载(rz、sz)
```bash
- 联网下载文件(wget、curl)
yum install wget -y
#选项: -O: 指定下载地址
	# wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

# crul：连通性,浏览网络上资源，-o保存到本地
#选项: -o: 指定下载地址
	# curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
# 你的django：127.0.0.1:8080端口，先在本地curl一下，看看能不能通，可能是防火墙，阿里云的安全组
	curl -o /home/a.png https:72743-20190.png

- 文件上传与下载(rz、sz)
# yum install lrzsz -y  #不安装软件则无法执行该命令

# rz            #只能上传文件文件上传(不能大于4g)
# sz /path/file #只能下载文件
```
- 文件或命令查找(locate、which、whereis、find)

```bash
- 文件查找
    # locate /etc/sh       #搜索etc目录下所有以sh开头的文件
    # locate -i /etc/sh    #搜索etc目录下，所有以sh开头的文件，忽略大小写

- 命令查找
    # which ls  #查找ls命令的绝对路径
    # whereis ls       //查找命令的路径、帮助手册、等
    # whereis -b ls    //仅显示命令所在的路径，仅看二进制
    # 对于内核相关的一些命令，用which whereis 是无法查询到的，需要使用type采查询
    # find . -name "*.log" -ls  在当前目录查找以.log结尾的文件，并显示详细信息。 
    # find /root/ -perm 600   查找/root/目录下权限为600的文件 
    # find . -type f -name "*.log"  查找当目录，以.log结尾的普通文件 
    # find . -type d | sort   查找当前所有目录并排序 find . -size +100M  查找当前目录大于100M的文件
    # type -a ls        #查看命令的绝对路径(包括别名)
    # type -a for

```

- 字符处理命令(sort、uniq、cut、sed、awk、wc、)
```bash
- sort 排序，sort [OPTION]... [FILE]...
# -r：倒序 -n：按数字排序 -t：指定分隔符(默认空格) -k：指定第几列, 指定几列几字符（指定1,1  3.1,3.3）
    cat >> file.txt <<EOF
    b:3
    c:2
    d:1
    f:11
    EOF
# 结果并不是按照数字排序，而是按字母排序。
    sort file.txt
    b:3
    c:2
    d:1
    f:11
# 可以使用-t指定分隔符, 使用-k指定需要排序的列。
# -t 指定分隔符，-k指定列，按第二列排序
    sort -t ":" -k2 file.txt
    d:1
    f:11 #第二行为什么是11？不应该按照顺序排列？
    c:2
    b:3
# 按照排序的方式, 只会看到第一个字符,11的第一个字符是1, 按照字符来排序确实比2小。 
# 如果想要按照数字的方式进行排序, 需要使用 -n参数，按数字排序。
    sort -t ":" -n -k2 file.txt
    d:1
    c:2
    b:3
    f:11

- uniq 去重，连续挨着的才能去，所以要跟sort连用
#选项：-c  计算重复的行
    cat >>file2.txt <<EOF
    abc
    123
    abc
    123
    EOF
#uniq需要和sort一起使用, 先使用sort排序, 让重复内容连续在一起
    cat file.txt |sort
    123
    123
    abc
    abc
# 使用uniq去除相邻重复的行
    cat file.txt |sort|uniq
    123
    abc
#-c参数能统计出文件中每行内容重复的次数
    cat file.txt |sort|uniq -c
      2 123
      2 abc
      
- cut截取字段：cut OPTION... [FILE]...
#选项：-d 指定分隔符 -f 数字,取第几列 –f3,10,三列和6列 -c 按字符取(空格也算)
	echo "Im fanghao, is QQ 1027343248" >file.txt   
#过滤出文件里 fanghao以及1027343248

#实现上述题目几种思路
    cut -d " " -f2,5 file.txt	#把字符串按“ ” 分割，取出第2和第5个

- awk 取列
	awk '{print $2,$5}' file.txt
# -F 指定分隔符
	awk '{print $2,$5}' file.txt | awk -F "," '{print $1,$2}'

- sed 替换 sed 's###g'
# sed 's###g' 固定写法
# sed 's#,##g'  把逗号替换成空
	cut -d " " -f2,5 file.txt | sed 's#,##g'

- wc统计行号wc [OPTION]... [FILE]...
#选项：-l显示文件行数 -c显示文件字节 -w显示文件单词

# wc -l /etc/fstab      #统计/etc/fstab文件有多少行
# wc -l /etc/services   #统计/etc/services 文件行号
# ls |wc -l             #统计当前路径下有多少文件和文件夹

#扩展方法
# grep -n "." /etc/services  | tail -1
# awk '{print NR $0}' /etc/services | tail -1
# cat -n /etc/services  | tail -1  
```

- 文件属性文件类型

```bash
ls -l
-rw-r--r-- 1 root root 29 11月 21 22:43 file.txt
分别是权限，硬链接数，属主，属组，大小，修改时间，文件名

- 文件类型，通过file来查看详细的类型
    -   #普通文件(文本, 二进制, 压缩, 图片, 日志等) 
    d   #目录文件

    b   #设备文件(块设备)存储设备硬盘 /dev/sda1, /dev/sda2
    c   #设备文件(字符设备)，终端 /dev/tty1, /dev/zero
    s   #套接字文件, 进程间通信(socket)
    p   #管道文件
    l   #链接文件
```
- 系统链接文件
Linux的文件分成两个部分：用户数据 (user data) 与元数据 (metadata)。
用户数据，即文件数据块 (data block)，数据块是记录文件真实内容的地方，我们将其称为Block
元数据，即文件的附加属性，如文件大小、创建时间、所有者等信息。我们称其为Inode
在Linux中，inode是文件元数据的一部分但其并不包含文件名，inode号即索引节点号）
文件名仅是为了方便人们的记忆和使用，系统或程序通过 inode 号寻找正确的文件数据块。
```bash
1 软链接和硬链接：软链接新建inode，硬链接指向同一个inode
2 软链接---》快捷方式
	- ln -s a.png /home/jack/a.png
	- 一般咱们对可执行文件建立软链接（删除不会删除原来）
    - 软链接目录： 
    	redis-3.2.1---->编译安装
        redis-3.2.1/bin  路径配到环境变量
        软件升级
        redis-4.2.1
        
        
        -建立软链接redis---》redis-3.2.1
        redis/bin  路径配到环境变量
        软件升级
        redis软链接到---》redis-4.2.1
    - 用处：
    	- redis-server:1 redis的bin路径加入到环境变量 2 软件连接到/bin
        - 软件升级：给目录建立软链接，实现软件的平滑升级
3 硬链接
ln  /root/file /tmp/file_hard  （了解）
```
```bash
硬链接与软链接区别
1)ln命令创建硬链接，ln -s命令创建软链接。
2)目录不能创建硬链接，并且硬链接不可以跨越分区系统。
3)目录软链接特别常用,并且软链接支持跨越分区系统。
4)硬链接文件与源文件的inode相同，软链接文件与源文件inode不同。
5)删除软链接文件，对源文件及硬链接文件无任何影响。
6)删除文件的硬链接文件，对源文件及链接文件无任何影响。
7)删除链接文件的源文件，对硬链接无影响，会导致软链接失效。
8)删除源文件及其硬链接文件，整个文件会被真正的删除。
```



## 文件编辑vim/vi
vi和vim都是文本编辑器，只不过vim是vi的增强版，比vi多了语法高亮显示，其他编辑功能几乎无差，所以使用vi还是vim取决个人习惯。

```bash
1.普通模式: 主要是控制光标移动，可对文本进行复制、粘贴、删除等工作。
使用vim filename 编辑一个文件时，一进入该文件就是普通模式了。
在这个模式下，可以进行光标移动、复制、删除、粘贴操作。

2.编辑模式: 主要进行文本内容编辑和修改
从普通模式进入编辑模式，只需你按一个键即可（i, I, a, A, o, O）
当进入编辑模式时，会在屏幕的最下一行会出现 “INSERT”标记
从编辑模式回到普通模式只需要按键盘左上方的 ESC 键即可。

3.末行模式: 主要用于保存或退出文本。
在普通模式下，输入 “:” 或者 “/“ 即可进入命令模式。
在命令该模式下，可进行的操作有，显示行号、搜索、替换、保存、退出。

小结: vim编辑打开文件整体流程如下:
1.默认打开文件处于普通模式
2.从普通模式切换至编辑模式需要使用a、i、o
3.编辑模式修改完毕后需要先使用ECS返回普通模式
4.在普通模式输入”:”或”/“进入命令模式，可实现文件的保存与退出。
PS: 在vim中，无法直接从编辑模式切换到命令模式。
```

```bash
# yum install vim -y
# 普通模式、编辑模式、命令模式
# 普通模式：
    #1.命令光标跳转
    G       #光标跳转至末端
    gg      #光标跳转至顶端
    Ngg     #光标跳转至当前文件内的N行
    $       #光标跳转至当前光标所在行的尾部
    ^或者0     #光标跳转至当前光标所在行的首部
    #2.文件内容较多
    ctrl+f  #往下翻页(行比较多)
    ctrl+b  #往上翻页
    #3.复制与粘贴
    yy      #复制当前光标所在的行
    5yy     #复制当前光标以及光标向下4行
    p(小写)   #粘贴至当前光标下一行   
    P(大写)   #粘贴至当前光标上一行
    #4.删除、剪贴、撤销  
    dd      #删除当前光标所在的行   
    4dd     #删除当前光标所在的行以及往下的3行
    dG      #删除当前光标以后的所有行
    D       #删除当前光标及光标以后的内容  
    x       #删除当前光标标记往后的字符
    X       #删除当前光标标记往前的字符
    dd & p  #剪贴、先删除dd(number dd)，后粘贴p
    u       #撤销上一次的操作
    #5.替换
    r       #替换当前光标标记的单个字符
    R       #进入REPLACE模式, 连续替换，ESC结束

# 编辑模式
    i   #进入编辑模式，光标不做任何操作
    a   #进入编辑模式，将当前光标往后一位
    o   #进入编辑模式，并在当前光标下添加一行空白内容
    I   #进入编辑模式，并且光标会跳转至本行的头部
    A   #进入编辑模式，将光标移动至本行的尾部
    O   #进入编辑模式，并在当前光标上添加一行空白内容

# 命令模式：
	-不能从编辑模式直接进，只能先到普通模式按 :  进入命令，退出命令模式esc
     -w  表示保存
     -q   退出
     -！  强制退出
     -修改了文件后保存：  wq    wq！
     -修改了不想保存退出： q     q！
     -:set nu 显示行号
     -:set nonu 不显示行号
     -/字符串    搜索这个字符串
     -:%s#sbin#test#g #替换整个文本文件中包含sbin的替换为test
```
- vim拓展
```bash

1.环境变量临时生效
    :set nu             #显示行号
    :set ic             #忽略大小写, 在搜索的时候有用
    :set ai             #自动缩进
    :set list           #显示制表符(空行、tab键)
    :set no[nu|ic|ai…]  #取消临时设定的变量
2.环境变量永久生效。~/.vimrc 个人环境变量(优先级高) /etc/vimrc 全局环境变量

# vim  ~/.vimrc #当下次再打开文件自动显示行号并忽略大小写
    set nu
    set ic

#如果个人vim环境没有配置, 则使用全局vim环境变量配置。
#如果个人vim环境和全局环境变量产生冲突, 优先使用个人vim环境变量。
3.如何同时编辑多个文件
    vim -o file1 file2  #水平分割
    vim -O file1 file2  #垂直分割

	#ctrl+ww 文件间切换
4.相同文件之间差异对比，通常用于对比修改前后差异
    # diff      #文件对比   
    # vimdiff   #以vim方式打开两个文件对比，高亮显示不同的内容
5.如果VIM非正常退出 （ctrl+z）挂起或强制退出终端没关闭VIM后
#假设打开filename文件被以外关闭，需要删除同文件名的.swp文件即可解决
	# rm -f .filename.swp
```

##　用户管理
```bash
#1 id  查看当前用户信息
uid=0(root) gid=0(root) groups=0(root)
#2 用户信息保存在 cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
#3 密码存放路径 cat /etc/shadow
#4 约定不同用户的uid属于某个范围（了解）
```
- 用户相关命令
```bash
1.新增用户
使用useradd命令，注意: adduser命令软链接指向useradd命令
#选项
    # -u 指定要创建用户的UID,不允许冲突
    # -g 指定要创建用户默认组
    # -G 指定要创建用户附加组,逗号隔开可添加多个附加组
    # -d 指定要创建用户家目录
    # -s 指定要创建用户的bash shell  /bin/bash   /sbin/nologin
    # -c 指定要创建用户注释信息
    # -M 给创建的用户不创建家目录
    # -r 创建系统账户，默认无家目录

#1.创建bgx用户，UID5001,基本组students，附加组sa 注释信息:2019 new student,登陆shell:/bin/bash
    groupadd sa
    groupadd students
    useradd -u 5001 -g students -G sa -c "2019 new student" -s /bin/bash bgx

#2.创建mysql系统用户，-M不建立用户家目录 -s指定nologin使其用户无法登陆系统
    useradd mysql -M -s /sbin/nologin
    useradd -r dba -s /sbin/nologin
# 3 
useradd od -u 7777 -G sa -d /tmp/od -s /sbin/nologin
grep "7777" /etc/passwd
# 4 SELinux
    getenforce # 查看
    setenforce 0 # 临时关闭
    cat /etc/selinux/config
    SELINUX=disabled
2.修改用户信息
使用usermod命令修改用户信息
    #选项
    # -u 指定要修改用户的UID
    # -g 指定要修改用户基本组
    # -G 指定要修改用户附加组，使用逗号隔开多个附加组, 覆盖原有的附加组，-aG追加
    # -d 指定要修改用户家目录 -md 旧家搬新家
    # -s 指定要修改用户的bash shell
    # -c 指定要修改用户注释信息
    # -l 指定要修改用户的登陆名
    # -L 指定要锁定的用户
    # -U 指定要解锁的用户

#1.检查此前创建的用户信息
grep "bgx" /etc/passwd
bgx:x:5001:503:2019 new student:/home/bgx:/bin/bash

#2.修改bgx用户uid、gid，附加组  -a表示追加
groupadd -g 5008 network_sa
groupadd -g 5009 devops
usermod -u 6001 -g5008 -a -G 5009 bgx

#3.修改bgx用户的注释信息, 用户家目录, 登录shell, 登录名 -l：改名字，-md，把环境也带过去
usermod -c "2019 new student" -md /bgx -s /bin/sh -l change_bgx bgx

#检查是否修改成功
grep "bgx" /etc/passwd
bgx_lqz:x:6001:5008:2019 new student:/bgx:/bin/sh
id change_bgx
uid=6001(change_bgx) gid=5008(network_sa) groups=5008(network_sa),503(sa),5009(devops)
ll -d /bgx
drwx------. 2 bgx_lqz network_sa 4096 2014-09-23 00:13 /bgx

#4.锁定用户[扩展]
echo "123" |passwd --stdin change_bgx
usermod -L change_bgx  #锁定后会无法登陆系统

#5.解锁用户[扩展]
usermod -U change_bgx
3.删除账户
使用userdel命令删除账户
#选项 -r 删除用户同时删除它的家目录
#1.删除user1用户，但不删除用户家目录和 mail spool
userdel user1
ls /var/spool/mail/
#2.-r参数可以连同用户家目录一起删除(慎用)
userdel -r user1

```
- 其他
```bash
1) 使用finger命名查询用户信息以及登录信息(yum install finger)，示例: finger UserName
2) 使用chfn命令修改用户信息(其实是修改注释)，示例: chfn UserName
3) 使用chsh命令修改用户登录Bash Shell，示例: chsh UserName
4) 使用who(当前有哪些用户登录了)、whoami、w检查用户登陆情况

```
- 设置、修改密码
1.普通用户只允许变更自己的密码，无法修改其他人密码，并且密码长度必须8位字符
2.管理员用户允许修改任何人的密码，无论密码长度多长或多短。
```bash
改密码
	-passwd root
	
```
- 拓展知识
```bash
拓展知识
1.useradd创建用户时，系统会以/etc/login.defs、/etc/defaults/useradd两个配置文件作为参照物，如果在创建用户时指定了参数则会覆盖/etc/login.defs、/etc/defaults/useradd文件默认配置，如未指定则使用默认。
grep -Ev "^#|^$" /etc/login.defs
cat /etc/login.defs
MAIL_DIR    /var/spool/mail  # 定义了邮件路径放在哪
PASS_MAX_DAYS   99999        # 密码过期时间
PASS_MIN_DAYS   0            # 密码最少0天
PASS_MIN_LEN    5            # 密码长度
PASS_WARN_AGE   7            # 7天提醒
UID_MIN                  1000
UID_MAX                 60000
SYS_UID_MIN               201
SYS_UID_MAX               999
GID_MIN                  1000
GID_MAX                 60000
SYS_GID_MIN               201
SYS_GID_MAX               999
CREATE_HOME yes             # 是否创建home
UMASK           077
USERGROUPS_ENAB yes         # 用户不指定组，默认创建一个同名组
ENCRYPT_METHOD SHA512       # 密码加密算法

cat /etc/default/useradd
GROUP=100
HOME=/home      #把用户的家目录建在/home中。
INACTIVE=-1     #是否启用账号过期停权,-1表示不启用。
EXPIRE=         #账号终止日期,不设置表示不启用。
SHELL=/bin/bash #新用户默认所有的shell类型。
SKEL=/etc/skel  #配置新用户家目录的默认文件存放路径。
CREATE_MAIL_SPOOL=yes   #创建mail文件。
2.当使用useradd创建用户时，创建的用户家目录下会存在 .bash_ 环境变量相关的文件，这些环境变量文件默认从/etc/skel目录中拷贝。这个默认拷贝环境变量位置是由/etc/defaults/useradd配置文件中定义的。

#故障案例，在当前用户家目录执行了rm -rf .，下次登录系统时出现-bash-4.1$，如何解决！
-bash-4.1$ cp -a /etc/skel/.bash ./
-bash-4.1$ exit
[root@bgx ~]#   #重新连接即可恢复
```
- 组
```bash
#组增删改
	-groupadd no_gid   新增组
    -groupmod -g 1111 student  改组id号
    -groupmod student -n new_student  改组名字
    -groupdel new_student   删除组（组下没有人，把人删除，再删）
```
- su身份切换和 sudo提权
```bash
1.Linux Shell主要分为如下几类
交互式shell，等待用户输入执行的命令(终端操作,需要不断提示)
非交互式shell，执行shell脚本, 脚本执行结束后shell自动退出
登陆shell，需要输入用户名和密码才能进入Shell，日常接触的最多的一种
非登陆shell，不需要输入用户和密码就能进入Shell,比如运行bash会开启一个新的会话窗口

2.bash shell配置文件介绍(文件主要保存用户的工作环境)
个人配置文件：~/.bash_profile ~/.bashrc 。

全局配置文件：/etc/profile /etc/profile.d/*.sh /etc/bashrc
profile类文件, 设定环境变量, 登陆前运行的脚本和命令。bashrc 类文件, 设定本地变量, 定义命令别名
PS: 如果全局配置和个人配置产生冲突，以个人配置为准。

3.登陆系统后，环境变量配置文件的应用顺序是?
登录式shell配置文件执行顺序: /etc/profile->/etc/profile.d/.sh->/.bash_profile->/.bashrc->/etc/bashrc
非登陆式shell配置文件执行顺序: ~/.bashrc->/etc/bashrc->/etc/profile.d/.sh
PS: 验证使用echo在每行添加一个输出即可

4.说了这么多预备知识，那这些和su命令切换用户有什么关系?
su - username属于登陆式shell，su username属于非登陆式shell，区别在于加载的环境变量不一样。
su username 属于非登陆式shell

普通用户su -可以直接切换至root用户，但需要输入root用户的密码。
超级管理员root用户使用su - username切换普通用户不需要输入任何密码。
```
```bash
su 和sudo
1.su切换用户，使用普通用户登录，然后使用su命令切换到root。优点:简单 缺点:需要知道root密码
2.sudo提权，当需要使用root权限时进行提权，而无需切换至root用户，优点:安全、方便 缺点:复杂
	-su 切换用户
    	-su - jack：打开新的shell，会加载自己的环境变量
        -su jack：不打开新的shell，不会加载它的环境变量
    -sudo 普通用户可以有一些超级用户的权限，不需要输入密码
    	usermod jack -G wheel  # 把jack用户加入到了wheel组
        -你这个用户没有权限，你尝试 sudo mkdir ll试一下，不行，超级管理员没有给你配这个权限
        

	一般正常配置sudo方式
	#visudo => vim /etc/sudoers
#1.用户名  2.主机名=(角色名）       4.命令名
bgx       ALL=(ALL)         /usr/bin/yum,/usr/sbin/useradd   #允许使用sudo执行命令
oldboy   ALL=(ALL)          NOPASSWD:/bin/cp, /bin/rm   #NOPASSWD不需要使用密码

visudo -c # 检查刚刚编辑的是否有错误
sudo -l  # 对主机有哪些权限
```

## 权限

- 在Linux系统中，针对文件定义了三种身份，分别是属主(owner)、属组(group)、其他人(others)，每一种身份又对应三种权限，分别是可读(readable)、可写(writable)、可执行(excutable)。
- 每个文件都有一个9位基本权限位，比如: rwxr-xr-x其中每三位字符为一组，分别表示属主权限位，属组权限位，匿名权限位。
- linux中基本权限位则是使用这9位字符来表示，主要控制文件属主(User)、属组(Group)、其他用户(Other)

```bash
字母				含义		对应权限
r(read)			读取权限		4
w(write)		写入权限		2
x(execute)		执行权限		1
-(没有权限)	 	没有权限		 0

使用方式1
	touch file                    #创建文件
    chmod a=rwx file              #给所有人添加读写执行权限
    chmod a=-rwx file             #取消所有的权限
    chmod u=rwx,g=rw,o=- file     #属主读写执行，属组读写，其他人无权限
    chmod ug=rwx,o=r file         #属主属组读写执行，其他人读权限
    ll file
    -rwxrw-r-- 1 root root 0 Apr 13 03:29 file

使用方式2
#选项:  -R递归修改
    touch file
    chmod 600 file
    ll file
    -rw------- 1 root root 0 Apr 13 03:29 file

#针对目录设定权限
    mkdir dir
    chmod 777 dir/    #修改目录允许所有人访问
    chmod -R 755 dir/ #修改目录及子目录权限
    ll -d dir/
    drwxr-xr-x 2 root root 6 Apr 13 03:34 dir/
```
```bash
总结rwx对文件的影响
    读取权限（r）具有读取阅读文件内容权限
    1.只能使用查看类命令cat、head、tail、less、more

    写入权限（w）具有新增、修改文件内容的权限
    1.使用vim编辑会提示权限拒绝, 但可强制保存,会覆盖文件的所有内容
    2.使用echo命令重定向的方式可以往文件内写入数据,>>可以进行追加
    3.不能删除文件,因为删除文件看的不是文件的属性,需要看上级目录是否有w的权限

    执行权限（x）具有执行文件的权限
    1.执行权限什么用都没有
    2.如果普通用户需要执行文件,需要配合r权限

总结rwx对目录的影响
    读取权限（r），如果目录只有r权限: 具有浏览目录及子目录权限
    1.可以使用ls命令浏览目录及子目录， 但同时也会提示权限拒绝
    2.使用ls -l命令浏览目录及子目录，文件属性会带问号，并且只能看到文件名
    总结: 目录只有r权限，仅仅只能浏览内的文件名，无其他操作权限

    写入权限（w），如果目录只有w权限: 具有增加、删除或修改目录内文件名权限(需要x权限配合)
    PS: 如果目录有w权限, 可以在目录内创建文件, 删除文件(跟文件本身权限无关)
    不能进入目录、不能复制目录、不能删除目录、不能移动目录

    执行权限（x），如果目录只有x权限
    1.只能进入目录
    2.不能浏览、复制、移动、删除
```
```bash
Linux权限总结与注意事项
    文件r权限, 只给用户查看,无其他操作
    文件rw权限, 可以查看和编辑文件内容
    文件rx权限, 允许查看和执行文件、但不能修改文件—–>PASS
    文件rwx权限, 能读,能写,能执行,但不能删除,因为删除需要看上级目录的权限有没有w—–>PASS
    目录rx权限, 允许浏览目录内文件以及子目录、并允许在目录内新建文件, 不允许创建、删除文件和目录
    目录wx权限, 能进入目录,能删除内容,能写入内容,但就是无法使用ls cat这样的命令—–>PASS
    目录rw权限, 能看,能写,但无法进入目录—–>PASS
    PS: 文件的 x权限小心给予，目录的 w权限小心给予。
    PS: 文件通常设定的权限是644,目录设定的权限是755
    PS: 控制目录权限755, 如果有普通用户需要操作目录里面的文件，在来看文件的权限
```
- 属主和属组
可以使用chown、chgrp命令实现。chown能设置属主和属组，chgrp仅能设置属组。
```bash
#chown 更改属主以及属组 -R：递归修改
#准备环境，创建文件和目录
	mkdir dir/test1 && touch dir/file
#示例1: 修改所属主为bin
	chown bin dir/
#示例2: 修改所属组为adm
	chown .adm dir/
#示例3: 递归修改目录及目录下的所有文件属主和属组
	chown -R root.root dir/
```

- 特殊权限
chatrr 只有 root 用户可以使用，用来修改文件系统的权限属性，建立凌驾于 rwx 基础权限之上的授权。
chatrr 命令格式：[root@bgx ~]# chattr [+-=] [选项] 文件或目录名
```bash
#选项: + 增加权限 -减少权限 =等于某个权限
# a：让文件或目录仅可追加内容
# i：不得任意更动文件或目录

#1.创建文件并设置属性
    touch file_a file_i
    lsattr file_a file_i
---------------- file_a
---------------- file_i

#2.使用chattr设置属性，lsattr查看权限限制
    chattr +a file_a
    chattr +i file_i
    lsattr file_a file_i
-----a---------- file_a
----i----------- file_i

#3.a权限，无法写入和删除文件，但可以追加数据，适合/etc/passwd这样的文件
	echo "aa" > file_a
bash: file_a: Operation not permitted
	rm -f file_a
rm: cannot remove ‘file_a’: Operation not permitted
	echo "aa" >> file_a

#5.i权限, 无法写入，无法删除，适合不需要更改的重要文件加锁
	echo "i" > file_i
bash: file_i: Permission denied
	echo "i" >> file_i
bash: file_i: Permission denied
	rm -f  file_i
rm: cannot remove ‘file_i’: Operation not permitted

#6.解除限制
    chattr -a file100 
    chattr -i file200
```

## 输入和输出

- 标准输入与输出
```bash
当运行一个程序时通常会自动打开三个标准文件，分别是标准输入、标准输出、错误输出

名称				文件描述符		作用
标准输入（STDIN）		0		默认是键盘，也可以是文件或其他命令的输出。
标准输出（STDOUT）	1		默认输出到屏幕。
错误输出（STDERR）	2		默认输出到屏幕。
文件名称（filename）	3+	
进程将从标准输入中得到数据，将正常输出打印至屏幕终端，将错误的输出信息也打印至屏幕终端。
PS: 进程是使用文件描述符(file descriptors)来管理打开的文件
```
- 输出重定向
```bash
输出重定向，改变输出内容的位置。输出重定向有如下几种方式，如表格所示
类型				操作符					用途
标准覆盖输出重定向	>		将程序输出的正确结果输出到指定的文件中,会覆盖文件原有的内容
标准追加输出重定向	>>		将程序输出的正确结果以追加的方式输出到指定文件，不会覆盖原有文件
错误覆盖输出重定向	2>		将程序的错误结果输出到执行的文件中，会覆盖文件原有的内容
错误追加输出重定向	2>>		将程序输出的错误结果以追加的方式输出到指定文件，不会覆盖原有文件
标准输入重定向		 <<			将命令中接收输入的途径由默认的键盘更改为指定的文件或命令
```



- 查找补充 find

```bash
1.find名称查找

    #1.创建文件
        touch /etc/sysconfig/network-scripts/{ifcfg-eth1,IFCFG-ETH1}
    #2.查找/etc目录下包含ifcfg-eth0名称的文件
        find /etc -name "ifcfg-eth1"
    #3.-i 忽略大小写
        find /etc -iname "ifcfg-eth1"
    #查找/etc目录下包含ifcfg-eth名称所有文件
        find /etc/ -name "ifcfg-eth*"
        find /etc -iname "ifcfg-eth*"
2.find大小查找
    #1.查找大于5M的文件
    	find /etc -size +5M
    #2.查找等于5M的文件
    	find /etc -size 5M
    #3.查找小于5M的文件
    	find /etc -size -5M
3.find类型查找
	# f 文件
		find /dev -type f
	# d 目录
		find /dev -type d
	# l 链接
	    find /dev -type l
	# b 块设备
		find /dev -type b
    # c 字符设备
    	find /dev -type c
    # s 套接字
    	find /dev -type s
    # p 管道文件
    	find /dev -type p
4.find时间查找
    #1.创建测试文件(后期shell会讲)
    	for i in {01..28};do date -s  201904$i && touch file-$i;done
    #2.查找7天以前的文件(不会打印当天的文件)
    	find ./ -iname "file-*" -mtime +7
    #3.查找最近7天的文件，不建议使用(会打印当天的文件)
    	find ./ -iname "file-*" -mtime -7
    #4.查找第7天文件(不会打印当天的文件)
    	find ./ -iname "file-*" -mtime 7
    #5.本地文件保留最近7天的备份文件, 备份服务器保留3个月的备份文件(实际使用方案)
        find /backup/ -iname "*.bak" -mtime +7 -delete
        find /backup/ -iname "*.bak" -mtime +90 -delete
5.find用户查找
    #查找属主是jack
        find /home -user jack
    #查找属组是admin
    	find /home -group admin
    #查找属主是jack, 属组是admin
    	find /home -user jack -group admin
    #查找属主是jack, 并且属组是admin
    	find /home -user jack -a -group admin
    #查找属主是jack, 或者属组是admin
    	find /home -user jack -o -group admin
    #查找没有属主
    	find /home -nouser
    #查找没有属组
    	find /home -nogroup
    #查找没有属主或属组
    	find /home -nouser -o -nogroup
6.find权限查找
    #精切匹配644权限
    	find . -perm 644 -ls
    #包含444权限即可
    	find . -perm -444  -ls
    #查找全局可写(每位权限必须包含w)
    	find . -perm -222 -ls
    #包含set uid
    	find  /usr/sbin -perm -4000 -ls
    #包含set gid
    	find  /usr/sbin -perm -2000 -ls
    #包含sticky
    	find  /usr/sbin -perm -1000 -ls
2.find动作处理，比如查找到一个文件后，需要对文件进行如何处理, find的默认动作是 -print\

动作	含义
-print	打印查找到的内容(默认)
-ls	以长格式显示的方式打印查找到的内容
-delete	删除查找到的文件(仅能删除空目录)
-ok	后面跟自定义 shell 命令(会提示是否操作)
-exec	后面跟自定义 shell 命令(标准写法 -exec ;)

1.find查找后的动作命令示例
    #1.使用-print打印查找到的文件
    	find /etc -name "ifcfg*"
    	find /etc -name "ifcfg*" -print
    #2.使用-ls打印查找到的文件，以长格式显示
    	find /etc -name "ifcfg*" -ls
    #3.使用-delete删除文件，但仅能删除空目录
    	find /etc -name "ifcfg*" -delete
    #4.使用-ok实现文件拷贝，但会提示是否拷贝
    	find /etc -name "ifcfg*" -ok cp -rvf {} /tmp \;
    #5.使用-exec实现文件拷贝和文件删除。
    	find /etc -name "ifcfg*" -exec cp -rvf {} /tmp \;
    	find /etc -name "ifcfg*" -exec rm -f {} \;
2.使用find命令结合xargs
    #xargs将前者命令查找到的文件作为一个整体传递后者命令的输入
    	touch file.txt
    	find . -name "file.txt" |xargs rm -f
    	find . -name "file.txt" |xargs -I {} cp -rvf {} /var/tmp
3.find逻辑运算符
符号	作用
-a	与
-o	或
-not|!	非

    #1.查找当前目录下，属主不是hdfs的所有文件
    	find . -not -user hdfs 
    	find . ! -user hdfs    
    #2.查找当前目录下，属主属于hdfs，且大小大于300字节的文件
    	find . -type f -a -user hdfs -a -size +300c            
    #3.查找当前目录下的属主为hdfs或者以xml结尾的普通文件
    	find . -type f -a \( -user hdfs -o -name '*.xml' \)

```

## 压缩和解压

```bash
Linux下压缩包有哪些常见的类型
    格式				压缩工具
    .zip			zip压缩工具
    .gz				gzip压缩工具，只能压缩文件，会删除原文件(通常配合tar使用)
    .bz2			bzip2压缩工具，只能压缩文件，会删除原文件(通常配合tar使用)
    .tar.gz			先使用tar命令归档打包，然后使用gzip压缩
    .tar.bz2		先使用tar命令归档打包，然后使用bzip压缩
#1  Windows的压缩包与Linux的压缩包能否互通
	windwods：rar，zip  
    linux：tar.gz,zip互通，不支持rar
# 2 gzip (只能压一个文件，不能压文件夹，会把原来的删除)
	-gzip file
    -gzip -d file
    -有什么用？
   	-cd /etc/yum.repos.d/
#3 zip的压缩和解压
	-yum install zip unzip -y
    -zip  filename.zip  filename  # 压单个文件
    -zip -r home.zip /home/   #把home文件夹压缩
    -unzip  home.zip   #解压
    -unzip -l  home.zip # 不解压，看内容
    -unzip home.zip  -d /opt/   # 把当前路径下的home.zip 解压到opt
   
 # 4 tar打包与压缩
         #语法：tar [-zjxcvfpP] filename 
        c   #创建新的归档文件
        x   #对归档文件解包
        t   #列出归档文件里的文件列表
        v   #输出命令的归档或解包的过程
        f   #指定包文件名，多参数f写最后
        z   #使用gzip压缩归档后的文件(.tar.gz)
        j   #使用bzip2压缩归档后的文件(.tar.bz2)
        J   #使用xz压缩归档后的文件(tar.xz)
        C   #指定解压目录位置
        X   #排除多个文件(写入需要排除的文件名称)
        h   #打包软链接
        --hard-dereference  #打包硬链接
        --exclude   #在打包的时候写入需要排除文件或目录
        #常用打包与压缩组合
        czf     #打包tar.gz格式 常用
        cjf     #打包tar.bz格式 不怎么用
        cJf     #打包tar.xz格式 不考虑

        zxf     #解压tar.gz格式
        jxf     #解压tar.bz格式
        xf      #自动选择解压模式
        xvf     #显示解压过程
        tf      #查看压缩包内容
	-tar -czf 文件        ---》tar.gz
    -tar -xf  xx.tar.gz  --->解压xx.tar.gz
  
    tar -xzvf  xx.tar.gz ：解压tar.gz，详细过程列出来
    -tar -czf home.tar.gz dd/ lqz1 lqz2 /home/
    -tar czf etc.tar.gz --exclude=etc/services etc/  # 排除文件
    -tar xf /etc/local.tar.gz  -C /tmp  # -C指定解压到哪个路径
```


## 软件管理，rpm


```bash
#1  红帽的软件安装包（windows的：exe，mis）
#2  mount /dev/cdrom /mnt 把光盘挂在到 /mnt文件夹
#3  Linux中除了rpm安装软件，是否还有安装软件方式
	以下列出了rpm命令进行安装软件的常用参数
        选项				描述
        -i				安装rpm
        -v				显示安装详细信息
        -h				显示安装rpm进度
        –force			强制重新安装
        –nodeps			忽略依赖关系
	
	-源码安装-->官网下源码--》编译安装---》最新
	-rpm包，预先编译打包,安装简单，yum安装，本质就是rmp安装--》稍微老一些
	-二进制包：绿色包
	
	-安装rpm的软件：rpm -ivh tree-1.6.0-10.el7.x86_64.rpm
	-强制安装：rpm -ivh --force /mnt/Packages/tree-1.5.3-3.el6.x86_64.rpm
	 
	-rpm -q ：查看这个软件是否安装********
	-rpm -qa |grep tr  ：列出所有安装的软件
	-rpm -ql :查询指定软件包所安装的目录、文件列表rpm -ql unzip *****
	-rpm -qc unzip:查看这个软件的配置文件位置
	-rpm -qf /etc/pam.d/vsftpd  ：查看配置文件属于哪个软件
	-rpm -qlp trace-cmd-2.6.0-10.el7.x86_64.rpm ：查看该软件包安装后会释放哪些文件
	
	-使用远程地址安装：rpm -ivh https://mirrors.aliyun.com/zabbix/zabbix/3.0/rhel/7/x86_64/zabbix-agent-3.0.8-2.el7.x86_64.rpm
	    
	-rpm -Uivh  升级软件需要用  U
	-rpm -e zabbix-agent

```

- yum仓库，源
```bash
# 1 Yum是RedHat以及CentOS中的软件包管理器。能够通过互联网下载 .rpm 包并且安装，并可以自动处理依赖性关系，无须繁琐地一次次下载、安装
# 2 cd /etc/yum.repos.d/  路径下有xx.repo 文件---》yum源
# 3 换阿里云的源
	wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
        
# 4 配置其他源
	-wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo
	-yum install nginx 
    -yum provides ipconfig  # 通过命令查软件，这个命令属于哪个软件
   	-rpm -qf `which ifconfig` # 查命令属于哪个软件，前提是该软件安装了
```
- 二进制安装

```bash
1 会了yum安装，为什么还要会二进制安装（编译安装）
	-官方不提供yum安装
    -二进制安装是最新的
2 向服务器传递文件的几种方式 
	-scp nginx-1.18.0.tar.gz root@101.133.225.166:/home/jack 
    -sz，rz
    -xftp软件来传
    
    
3 源码安装nginx
	-1 下载
    -2 解压
    -2.1 安装依赖
    	-yum install -y pcre-devel gcc gcc-c++ make zlib-devel openssl-devel
    -3 通过configure 生成配置信息，配置相关的选项，并生成Makefile，软件安装的信息
    	./configure --prefix=/usr/local/nginx
    -4 make 按照Makefile生成的安装软件
    -5 make install：将二进制文件拷贝至对应的目录中
    -6 目录介绍
    	conf ：配置文件都放在这
        html ：静态文件存放路径，index.html
        logs :日志
        sbin ：可执行文件
    -7 命令介绍
        nginx  # 启动
        nginx -s reload # 重新加载，修改配置文件
        nginx -s restart  # 重启
        nginx -s stop # 停止
    -8 在任意路径敲nginx都能执行
    	-建立软链接  ln -s /usr/loacl/nginx/sbin/nginx /sbin/nginx
        -把/usr/loacl/nginx/sbin/路径加入环境变量
        -想使用systemctl 管理(制作系统服务)
```

## 进程管理
- 监控进程状态

查看进程的状态分为: 静态和动态两种方式
```bash
静态
ps -aux常用组合，查看进程 用户、PID、占用cpu百分比、占用内存百分比、状态、执行的命令等
#1  ps -aux 用它，[系统进程]
#2  ps -ef
#3  ps -aux|grep id,进程名字，

```
| 状态 | 描述 |
| -------- | -------- |
| USER |	启动进程的用户|
|PID |	进程运行的ID号|
|%CPU |	进程占用CPU百分比|
|%MEM |	进程占用内存百分比|
|VSZ	| 进程占用虚拟内存大小 (单位KB)|
|RSS	| 进程占用物理内存实际大小 (单位KB)|
|TTY	| 进程是由哪个终端运行启动的tty1、pts/0等 ?表示内核程序与终端|| 无关(远程连接会通过tty打开一个bash：tty)|
|STAT	| 进程运行过程中的状态 man ps （/STATE）|
|START	| 进程的启动时间|
|TIME	| 进程占用 CPU 的总时间(为0表示还没超过秒)|
|COMMAND	| 程序的运行指令，[ 方括号 ] 属于内核态的进程。 没有 [ ] 的是用户态进程。systemctl status 指令|

| STAT基本状态 | 描述 | STAT状态+符号 | 描述 |
| -------- | -------- | -------- | -------- |
|R	| 进程运行	|s	|进程是控制进程， Ss进程的领导者，父进程|
|S	| 可中断睡眠	|<	|进程运行在高优先级上，S<优先级较高的进程|
|T	| 进程被暂停	|N	|进程运行在低优先级上，SN优先级较低的进程|
|D	| 不可中断睡眠	|+	|当前进程运行在前台，R+该表示进程在前台运行（正在io操作，一旦停止，数据丢失）|
|Z	| 僵尸进程	|l	|进程是多线程的，Sl表示进程是以线程方式运行|


```bash
top 动态查看


常见指令
字母	含义
h	查看帮出
1	数字1，显示所有CPU核心的负载
z	以高亮显示数据
b	高亮显示处于R（进行中）状态的进程
M	按内存使用百分比排序输出
P	按CPU使用百分比排序输出
q	退出top

```

- 管理进程状态



|数字编号	|信号含义	|信号翻译|
| -------- | -------- |-------- |
|1	|SIGHUP	|通常用来重新加载配置文件,重新读取一次参数的配置文件 （类似 reload）|
|9	|SIGKILL	|强制杀死进程(有状态的服务(存磁盘的，如mysql)强制停止可能会导致下次起不来)|
|15	|SIGTERM|	终止进程，默认kill使用该信号|
```bash
使用kill -l列出当前系统所支持的信号
# 4 top实时看状态
# 5 kill -l
# 6 kill -9 进程id号 强行关闭
# 7 pkill -9 nginx  关闭nginx所有进程
# 8 killall nginx   关闭nginx所有进程
```

| 任务| 含义 |
| -------- | -------- |
|Tasks: 129 total	|当然进程的总数|
|1 running	|正在运行的进程数|
|128 sleeping	|睡眠的进程数|
|0 stopped	|停止的进程数|
|0 zombie	|僵尸进程数|
|%Cpu(s)	|平均cpu使用率，按1 查看每个cup具体状态|
|0.7 us	|用户进程占用cpu百分比|
|0.7 sys	|内核进程占用百分比|
|0.0 ni	|优先级进程占用cpu的百分比|
|98.7 id	|空闲cup|
|0.0 wa	|CPU等待IO完成的时间，大量的io等待，会变高|
|0.0 hi	|硬中断，占的CPU百分比|
|0.0 si	|软中断，占的CPU百分比|
|0.0 st	|虚拟机占用物理CPU的时间|





```bash

# 通过来管理进程screen
yum install screen -y
创建一个窗口
screen -S myjobs
执行耗时任务，进程
ctrl+a+d  退出当前bashshell但是耗时任务还在后台运行
screen -r myjobs 调到前台执行
screen -list  查看所有任务
```

## 系统服务

```bash
#1  centos6 上启动服务service start network
#2  centos7 启动服务：systemctl start network

#3  cd /usr/lib/systemd/system/

###制作系统服务

#4 vim mynginx.service

[Unit]
Description=my nginx
After=network.target  #在哪个服务启动后启动
[Service]
Type=forking
ExecStart=/usr/local/nginx/sbin/nginx
ExecStop=/usr/local/nginx/sbin/nginx -s stop
ExecRestart=/usr/local/nginx/sbin/nginx -s restart
ExecReload=/usr/local/nginx/sbin/nginx -s reload
[Install]
WantedBy=multi-user.target

# 以后就支持使用 systemctl start mynginx.service

# 查看服务状态：
	systemctl status mynginx.service
    # disabled表示没有开机自启动
    Loaded: loaded (/usr/lib/systemd/system/mynginx.service; disabled; vendor preset: disabled)
# 开机自启动
	systemctl enable mynginx
# 取消开机自启动
systemctl disable mynginx.service
```

