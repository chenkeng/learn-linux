# Centos一些常用操作命令

1. 文件处理命令：ls
    * 功能描述：显示目录文件
    * 命令英文原意：list
    * 命令所在路径：/bin/ls
    * 执行权限：所有用户
    * 语法：
        ls  选项[-ald]  [文件或目录]   
        --|--
         -a  |  显示所有文件，包括隐藏文件
         -l  |  详细信息显示
         -d  |  查看目录属性
        * $ ls –a > dir.txt ← 将ls –a命令执行结果输出到dir.txt文件。
        * $ ls –a >> dir.txt ← 将ls –a命令执行结果附加到dir.txt文件之后。  

2.  文件处理命令：cd
  - 功能描述：切换目录
  - 命令英文原意：change directory
  - 命令所在路径：shell内置命令
  - 执行权限：所有用户
  - 语法：cd [目录]
      * 范例：  $ cd  / 切换到根目录
      * $ cd    。。 回到上一级目录    

3. 文件处理命令：pwd
   * 功能描述：显示当前所在的工作目录
   * 命令英文原意：print working directory
   * 命令所在路径：/bin/pwd
   * 执行权限：所有用户
   * 语法：pwd
        * 范例：  $ pwd
        * /etc/rc5.d

4. 文件处理命令：touch
  * 功能描述：创建空文件
  * 命令名称：touch
  * 命令所在路径：/bin/touch
  * 执行权限：所有用户
  * 语法：touch  [文件名]
      * 范例：$ touch newfile


5. 文件处理命令：mkdir
功能描述：创建新目录
命令英文原意：make directories
命令所在路径：/bin/mkdir
执行权限：所有用户
语法：mkdir  [目录名]
范例：$ mkdir newdir
文件处理命令：cp
功能描述：复制文件或目录

6. 命令英文原意：copy
命令所在路径：/bin/cp
执行权限：所有用户
语法：    cp  -R  [源文件或目录] [目的目录]
              -R      复制目录
范例：    $ cp  file1 file2  dir1
              将文件file1、file2复制到目录dir1
$ cp  -R dir1 dir2
              将dir1下的所有文件及子目录复制到dir2

7. 文件处理命令：mv
功能描述：移动文件、更名
命令英文原意：move
命令所在路径：/bin/mv
执行权限：所有用户
语法：mv  [源文件或目录]  [目的目录]
范例：    $ mv  file1 file3
              将当前目录下文件file1更名为file3
$ mv  file2  dir2
将文件file2移动到目录dir2下

8. 文件处理命令：rm
功能描述：删除文件
命令英文原意：remove
命令所在路径：/bin/rm
执行权限：所有用户
语法：rm  -r   [文件或目录]
                -r        删除目录
范例：    $ rm file3
              删除文件file3
              $ rm -r dir1
              删除目录dir1
9. 文件处理命令：cat

功能描述：显示文件内容
命令英文原意：concatenate and display files
命令所在路径：/bin/cat
执行权限：所有用户
语法：cat [文件名]
范例：    $ cat  /etc/issue
              $ cat  /etc/services
              $ cat preface.txt 　more
              逐页显示preface.txt的内容;
              $ cat preface.txt >> outline.txt
              将preface.txt 附加到outline.txt文件之后;
              cat new.txt info.txt >readme.txt
              将new.txt和info.txt合并成readme.txt文件;

10. 文件处理命令：more
命令所在路径：/bin/more
执行权限：所有用户
语法：more  [文件名]
       (空格) 或f           显示下一页
       (Enter)           显示下一行
q或Q            退出
11. 文件处理指令：head

功能描述：查看文件的前几行
指令所在路径：/bin/head
执行权限：All User
语法：    head  -num  [文件名]
              -num  显示文件的前num行
范例：$ head  -20  /etc/services

12. 文件处理指令：tail

功能描述：查看文件的后几行
指令所在路径：/bin/tail

执行权限：All User

语法：    tail          -num  [文件名]

              -num       显示文件的后num行

-f            动态显示文件内容

范例：$ tail  -30  /etc/services
13. 文件处理命令：ln

功能描述：产生链接文件
命令英文原意：link
命令所在路径：/bin/ln
执行权限：所有用户
语法：    ln  -s  [源文件]  [目标文件]
              -s  创建软链接
范例：    $ ln -s  /etc/issue  /issue.soft
              创建文件/etc/issue的软链接/issue.soft
              $ ln  /etc/issue  /issue.hard
              创建文件/etc/issue的硬链接/issue.hard

14. 权限管理命令：chmod

功能描述：改变文件或目录权限
命令英文原意：change the permissions mode of a file
命令所在路径：/bin/chmod
执行权限：所有用户
语法：chmod  [{ugo}{+-=}{rwx}] [文件或目录]
[mode=421 ]  [文件或目录]
范例：    $ chmod  g+w  file1
              赋予文件file1所属组写权限
              $ chmod  777  dir1
              设定目录dir1为所有用户具有全部权限
代表字符
权限
对文件的含义
对目录的含义
r
读权限
可以查看文件内容
可以列出目录中的内容
w
写权限
可以修改文件内容
可以在目录中创建、删除文件
x
执行权限
可以执行文件
可以进入目录

15. 权限管理命令：chown

功能描述：改变文件或目录的所有者



命令英文原意：change file ownership

命令所在路径：/bin/chown

执行权限：所有用户

语法：chown  [用户] [文件或目录]

范例：    $ chown  nobody  file1

              改变文件file1的所有者为nobody





权限管理命令：chgrp

功能描述：改变文件或目录的所属组



命令英文原意：change file group ownership

命令所在路径：/bin/chgrp

执行权限：所有用户

语法：chgrp  [用户组]  [文件或目录]

范例：    $ chgrp adm file1

              改变文件file1的所属组为adm





权限管理命令：umask

功能描述：显示、设置文件的缺省权限



命令所在路径：/bin/umask

执行权限：所有用户

语法：    umask [-S]

              -S   以rwx形式显示新建文件或目录缺省权限

范例：    $ umask

              $ umask -S





文件搜索命令：which

功能描述：显示系统命令所在目录



命令所在路径：/usr/bin/which

执行权限：所有用户

语法：which  [命令名称]

范例：$ which ls





文件搜索命令：find

功能描述：查找文件或目录



命令所在路径：/usr/bin/find

执行权限：所有用户

语法：find [搜索路径]  [搜寻关键字]

范例：    $ find  /etc  -name  init

在目录/etc中查找文件init

$ find  /  -size  +204800

在根目录下查找大于100MB的文件

$ find  /  -user  sam

在根目录下查找所有者为sam的文件

              $ find  /etc  -ctime  -1

              在/etc下查找24小时内被修改过属性的文件和目录

$ find  /etc -size  +163840 -a -size  -204800

              在/etc下查找大于80MB小于100MB的文件

              $ find /etc -name inittab -exec ls -l {} \;

              在/etc下查找inittab文件并显示其详细信息





文件搜索指令：locate

功能描述：寻找文件或目录



指令英文原义：list files in databases

指令所在路径：/usr/bin/locate

执行权限：All User

语法：locate [搜索关键字]

范例：    $ locate file

              列出所有跟file相关的文件





文件搜索指令：updatedb

功能描述：建立整个系统目录文件的数据库



指令英文原义：update the slocate database

指令所在路径：/usr/bin/updatedb

执行权限：root

语法：updatedb

范例：# updatedb





文件搜索命令：grep

功能描述：在文件中搜寻字串匹配的行并输出



命令所在路径：/bin/grep

执行权限：所有用户

语法：grep  [指定字串] [源文件]

范例：# grep  ftp  /etc/services

              $ grep text *.conf

              ←搜索当前目录中扩展名为.conf且包含“text”字符串得文件。

              $ grep:amd.conf:    ←拒绝不符权限得操作

              $ grep:diskcheck.conf: ←拒绝不符权限得操作

              $ grep:grub.conf    ←拒绝不符权限得操作

              $ grep –s text *.conf   ←拒绝不符权限的操作之类的错误信息





帮助命令：man

功能描述：获得帮助信息



命令英文原意：manual

命令所在路径：/usr/bin/man

执行权限：所有用户

语法：man  [命令或配置文件]

范例：    $ man ls

              查看ls命令的帮助信息

              $ man services

              查看配置文件services的帮助信息





帮助指令：info

功能描述：获得帮助信息



指令英文原义：information

指令所在路径：/usr/bin/info

执行权限：All User

语法：info  [任何关键字]

范例：    $ info ls

              查看ls指令的帮助信息





帮助指令：whatis

功能描述：获得索引的简短说明信息



指令名称：whatis  apropos  makewhatis

指令英文原义：search the whatis database for strings

指令所在路径：/usr/bin/whatis apropos



              /usr/sbin/makewhatis

执行权限：All User，All User，root

语法：whatis apropos [任何关键字]

范例：    $ whatis ls

              $ apropos fstab              相当于man -k

              # makewhatis

              建立whatis和apropos搜索使用的数据库，当使用这两个命令发生错误时，就是whatis database 没有建立





压缩解压命令：gzip

功能描述：压缩文件



命令所在路径：/bin/gzip

执行权限：所有用户

语法：gzip  选项[文件]

压缩后文件格式：.gz





压缩解压命令：gunzip

功能描述：解压缩.gz的压缩文件



命令所在路径：/bin/gunzip

执行权限：所有用户

语法：gunzip  选项[压缩文件]

范例：$ gunzip file1.gz





压缩解压命令：tar

功能描述：打包目录



命令所在路径：/bin/tar

执行权限：所有用户

语法：tar  选项[cvf]  [目录]

              -c  产生.tar打包文件

              -v  显示详细信息

-f     指定压缩后的文件名

-z    打包同时压缩

压缩后文件格式：.tar.gz

范例：    $ tar  -zcvf   dir1.tar.gz  dir1

              将目录dir1压缩成一个打包并压缩的文件



tar命令解压缩语法：

-x    解包.tar文件

-v    显示详细信息

-f     指定解压文件

-z    解压缩

范例：$ tar  -zxvf  dir1.tar.gz





压缩解压命令：zip

功能描述：压缩文件或目录



命令所在路径：/usr/bin/zip

执行权限：所有用户

语法：    zip  选项[-r]  [压缩后文件名称]  [文件或目录]

              -r     压缩目录

压缩后文件格式：.zip

范例：    $ zip  services.zip  /etc/services

              压缩文件

              $ zip  -r  test.zip  /test

              压缩目录





压缩解压命令：unzip

功能描述：解压.zip的压缩文件



命令所在路径：/usr/bin/unzip

执行权限：所有用户

语法：unzip  [压缩文件]

范例：$ unzip test.zip





压缩解压命令：bzip2

功能描述：解压缩



命令所在路径：/usr/bin/bzip2

执行权限：所有用户

语法：    bzip2  选项[-k] [文件]

              -k   产生压缩文件后保留原文件

功能描述：压缩文件

压缩后文件格式：.bz2

范例：$ bzip2 -k file1

命令所在路径：/usr/bin/bunzip2

执行权限：所有用户

语法：bunzip2  选项[-k] [压缩文件]

                            -k   解压缩后保留原文件

范例：$ bunzip2  -k file1.bz2





网络通信指令：write

功能描述：向另外一个用户发信息，以Ctrl+D作为结束



指令所在路径：/usr/bin/write

执行权限：All User

语法：write  <用户名>

范例：   $ write  webmaster





网络通信指令：wall

功能描述：向所有用户广播信息



指令所在路径：/usr/bin/wall

执行权限：All User

语法：wall  [message]  [文件名]

范例：   $ wall  Happy New Year!





网络通信命令：ping

功能描述：测试网络连通性



命令所在路径：/usr/sbin/ping

执行权限：root

语法：ping  选项  IP地址

范例：  #  ping 192.168.1.1





网络通信命令：ifconfig

功能描述：查看网络设置信息



命令所在路径：/usr/sbin/ifconfig

执行权限：root

语法：ifconfig  选项[-a]  [网卡设备标识]

                            -a    显示所有网卡信息

范例：# ifconfig  -a





系统关机命令：shutdown

功能描述：关机



命令所在路径：/usr/sbin/shutdown

执行权限：root

语法：shutdown

范例：# shutdown -h now





系统关机命令：reboot

功能描述：重启系统



命令所在路径：/usr/sbin/reboot

执行权限：root

语法：reboot

范例：# reboot





加载光盘命令：mount     umount: 卸载光盘命令

功能描述：加载光盘及软盘



命令所在路径：/usr/sbin/reboot

注意：    若要允许一般用户也能加载光盘或软盘，请修改/ect/fstab/设置文件

              /dev/cdrom/mut/cdrom udf,iso9660 noauto,owner,kudzu,ro,user

              ←若要让一般用户也加载光盘，请在此处加上“，user”项目。

范例：    # mount   /dev/cdrom  /mut/cdrom   ←加载光盘

              # umount  /mnt/cdrom         ←光盘卸载





删除调度工作任务：crontab

范例：    $ crontab –r ←删除任务调度中的工作

              $ crontab  -1 ←再查看一次任务调度中的工作





用户使用过的历史命令：history











一．用户组管理

1.       添加用户组

groupadd

2.       删除用户组

groupdel

3.       修改用户组

groupmod

4.       切换用户组

newgrp <groupname>

如果一个用户同时属于多个用户组，可以用 newgrp 命令切换至目的组，以便能够拥有该组的权限。

5.       查看所有组

所有组其实就是 /etc/group 文件的内容做一些过滤。

cat /etc/group | awk -F: '{print $1}'

6.       查看用户所在组

groups <username>

 二．用户管理

 1. 添加用户

useradd <username> -d <path> -m -g –G –p

常用的就是上面几个参数，意思分别为：

-d ：指定用户主目录。如果此目录不存在，同时使用 -m 就会创建此目录。

-m ：创建用户主目录

-g ：用户所属组 ID

-G ：用户所属组名

-p ：登录密码。注意这个登录密码不是明文，是指加密后的密码。



useradd testuser –m –G mygroup

将会创建一个 testuser 的用户，并自动创建 /home/testuser 的用户主目录，并将用户添加至 mygroup 组中。

2. 删除用户

userdel –f –r <username>

-r ：删除用户主目录以及邮箱中的邮件

-f ：强行删除文件，即使属主不是该用户

3. 修改用户

usermod <username> -d <path> -m -g –G –p

参数意思与 useradd 大致相同



4. 用户密码

passwd <username>        ：修改密码

passwd –d <username> ：命令将用户的密码删除，即下次登录无须密码。

passwd –l <username>   ：锁定用户，使其无法登录



三．文件属主管理



1. 更改属主

chown –R <username>.<groupname> file

-R ：表示递归更改

chown –R testuser.newgroup testpath

上面的命令将 testpath 路径下的所有文件的拥有者都改为 testuser ，拥有组都改为 newgroup 。



2. 设置文件掩码

umask [a1 a2 a3 ]

用户可以使用 umask 命令设置文件默认的生成掩码。默认的生成掩码告诉系统创建一个文件或目录不应该赋予哪些权限。如果用户将 umask 命令放在环境文件 .bash_profile 中，就可以控制所有新建的文件和目录的访问权限。



a1 表示的是不允许属主的权限， a2 表示的是不允许同组人的权限， a3 代表不允许其他人的权限。

umask 022        ：   表示设置不允许同组用户和其他用户有写的权限。

umask              ：   显示当前的默认生成掩码。



CentOS最基本的20个常用命令

1. man 对你熟悉或不熟悉的命令提供帮助解释
eg:man ls 就可以查看ls相关的用法
注：按q键或者ctrl+c退出，在linux下可以使用ctrl+c终止当前程序运行。

2. ls 查看目录或者文件的属*，列举出任一目录下面的文件
eg: ls /usr/man
ls -l

a.d表示目录(directory)，如果是一个"-"表示是文件，如果是l则表示是一个连接文件(link)
b.表示文件或者目录许可权限.分别用可读(r)，可写(w)，可运行(x)。

3. cp 拷贝文件
eg: cp filename1 filename2 //把filename1拷贝成filename2
cp 1.c netseek/2.c //将1.c拷到netseek目录下命名为2.c

4. rm 删除文件和目录
eg: rm 1.c //将1.c这个文件删除

5. mv 移走目录或者改文件名
eg: mv filename1 filename2 //将filename1 改名为filename2
mv qib.tgz ../qib.tgz //移到上一级目录

6. cd 改变当前目录 pwd 查看当前所在目录完整路径
eg: pwd //查看当前所在目录路径
cd netseek //进入netseek这个目录
cd //退出当前目录

7. cat，more命令
将某个文件的内容显示出来。两个命令所不同的是:cat把文件内容一直打印出来，而 more则分屏显示
eg; cat>1.c //就可以把代码粘帖到1.c文件里，按ctrl+d 保存代码。
cat 1.c 或more 1.c //都可以查看里面的内容。
gcc -o 1 1.c //将1.c编译成.exe文件，我们可以用此命编译出代码。

8.chmod 命令 权限修改 用法：chmod 一位8进制数 filename。
eg: chmod u+x filenmame //只想给自己运行，别人只能读
//u表示文件主人， g 表示文件文件所在组。 o 表示其他人 ;r 表可读，w 表可写，x 表可以运行
chmod g+x filename //同组的人来执行

9. clear，date命令
clear:清屏，相当与DOS下的cls;date:显示当前时间。

10. mount 加载一个硬件设备
用法:mount [参数] 要加载的设备 载入点
eg: mount /dev/cdrom
cd /mnt/cdrom //进入光盘目录

11. su 在不退出登陆的情况下，切换到另外一个人的身份
用法: su -l 用户名(如果用户名缺省，则切换到root状态)
eg:su -l netseek (切换到netseek这个用户，将提示输入密码)

12.whoami，whereis，which，id
//whoami:确认自己身份
//whereis:查询命令所在目录以及帮助文档所在目录
//which:查询该命令所在目录(类似whereis)
//id:打印出自己的UID以及GID。(UID:用户身份唯一标识。GID:用户组身份唯一标识。每一个用户只能有一个唯一的UID和 GID)
eg: whoami //显示你自已登陆的用户名
whereis bin 显示bin所在的目录，将显示为：/usr/local/bin
which bin

13. grep，find
grep:文本内容搜索;find:文件或者目录名以及权限属主等匹配搜索
eg: grep success * 　　 /* 查找当前目录下面所有文件里面含有success字符的文件

14. kill 可以杀死某个正在进行或者已经是dest状态的进程
eg; ps ax

15. passwd 可以设置口令
16. history 用户用过的命令
17. !! 执行最近一次的命令
18. mkdir命令
eg: mkdir netseek //创建netseek这个目录

19. tar 解压命令
eg: tar -zxvf nmap-3.45.tgz //将这个解压到nmap-3.45这个目录里



14. 解压小全
tar -I或者bunzip2命令都可以解压.bz2文件
tar xvfj example.tar.bz2
tar xvfz example.tar.gz
tar xvfz example.tgz
tar xvf example.tar
unzip example.zip

15. 如何配置让哪些服务启动(天外闲云，q1208c)
方法1 运行ntsysv或者setup命令，进入菜单进行配置
方法2 chkconfig --list 显示服务
chkconfig name on/off 打开/关闭“name”服务


16. 查看文件夹大小

du -sh uploadfile

17. 查看磁盘使用情况

df -hl

12. 删除目录下所有文件包括子目录(bjchenxu)
rm -rf 目录名


13. 查看系统信息(bjchenxu)
cat /proc/cpuinfo - CPU (i.e. vendor, Mhz, flags like mmx)
cat /proc/interrupts - 中断
cat /proc/ioports - 设备IO端口
cat /proc/meminfo - 内存信息(i.e. mem used, free, swap size)
cat /proc/partitions - 所有设备的所有分区
cat /proc/pci - PCI设备的信息
cat /proc/swaps - 所有Swap分区的信息
cat /proc/version - Linux的版本号 相当于 uname -r
uname -a - 看系统内核等信息

 =================



15. 如何配置让哪些服务启动
方法1 运行ntsysv或者setup命令，进入菜单进行配置
方法2 chkconfig --list 显示服务
chkconfig name on/off 打开/关闭“name”服务

16. 查看文件夹大小
    * du -sh uploadfile



17. 查看磁盘使用情况
    * df -hl

```js
cat file  // 从第一个字节开始查看文件
tac file // 从最后一行开始反向查看一个文件

head -2 file // 查看一个文件的前2行
tail -3 file // 查看一个文件的最后3行

more file // 查看一个发文件的内容
vi file // 打开并浏览一个文件

// 查找字符串
grep  str file // 在file 中查找 str 字符串 。 匹配所有的
grep ^str file // 在file 中查找以str 开头的行
grep [0-9] file1 // 查找file 中所有包含数字的行
grep str -r /dir/*  // 在dir 目录及其子目录中查找字符串 str
diff file1 file2	// 找出两个文件的不同处
sdiff file1 file2	// 以对比的方式显示两个文件的不同
```

// 压缩 文件

bzip2  read.txt    压缩read.txt文件   read.txt.bz2
bunzip2 read.txt.bz2   解压 read.txt.bz2
gzip read.txt    read.txt.gz
gunzip read.txt.gz   read.txt
gzip -9 read.txt   最大程度压缩read.txt

tar -cvf target.tar file    将file 文件打包成 target.tar
tar -cvf target.tar file  file1  将file 和file1 打包到target.tar文件

zip file.zip  file
zip -r file1.zip file1 dir1   将文件额目录压缩成一个zip格式的压缩包

unzip file.zip   解压file.zip 压缩包
unzip test.zip -d /tmp/   解压文件到/tmp/ 目录



// yum 安装器
yum -y install  [package]  下载并安装一个rpm包
yum localinstall [package.rpm]   安装一个rpm包，使用你自己的软件仓库解决所有依赖关系
yum -y update  更新当前系统中安装的所有rpm包
yum update [package]	更新一个rpm包
yum remove [package]	删除一个rpm包
yum list	列出当前系统中安装的所有包
yum search [package]	在rpm仓库中搜寻软件包
yum clean [package]	清除缓存目录（/var/cache/yum）下的软件包
yum clean headers	删除所有头文件
yum clean all	删除所有缓存的包和头文件


ifconfig eth0	显示一个以太网卡的配置
ifconfig eth0 192.168.1.1 netmask 255.255.255.0	配置网卡的IP地址
ifdown eth0	禁用 ‘eth0’ 网络设备
ifup eth0	启用 ‘eth0’ 网络设备
iwconfig eth1	显示一个无线网卡的配置
iwlist scan	显示无线网络
ip addr show	显示网卡的IP地址

-------------------------------------

* vi file     

操作  |	解析
  -- | --
   i | 进入编辑文本模式
 Esc | 退出编辑文本模式
 :w	| 保存当前修改
 :q	| 不保存退出vi
:wq | 保存当前修改并退出vi
