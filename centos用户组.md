## 文件属性控制权限
```
通过查看ls -l命令可以查看文件的详细列表信息(如文件类型、所在组、文件名等)
如：-rwxrw-r-- 1 501 502 100 Mar Test.js
[-rwxrw-r--]各个段的含义
将[-rwxrw-r--]拆分为 [-|rwx|rw-|r--]四段
第一段[-]代表的是文件类型，一般有三种(-代表是文件)、(d代表是文件夹)、(l代表是链接)
[rwx代表的含义]，在linux系统中，r代表用户对该文件或者文件夹拥有可读权限、w代表可写权限、x代表可执行权限
在linux系统中，每个权限都有一个数字来表示，r(可读权限)用数字4表示，w(可写权限)用数字2表示，x(可执行权限)用数字1表示
第二段[rwx]代表的是该文件(或文件夹)的[所有者(谁创建了该文件，谁就是该文件的所有者)]对该文件的访问权限，如该所有者对该文件的权限是可读、可写、可执行
第三段[rw-]代表的是该用户[所在组的其它用户]对该文件的访问权限，如该用户组其它用户对该文件的访问权限是可读、可写
第四段[r--]代表的是[除了该用户所在组的其他组]对该文件的访问权限，如其他组用户对该文件的访问权限是可读
[注：权限都可以用数字来代替，例如 rwx 可用 4+2+1 =7 来表示，rw可用数字6来表示等]
1 501 502 100 Mar Test.js各个字段含义
1：代表的文件个数，如果是文件则是1，若是文件夹，则显示该文件夹下子文件数目
501：代表哪个用户，在每创建一个用户时，都会为该用户创建一个唯一的用户id，501就是指代该用户的id
502：代表该用户所在组，在创建每一个组时，linux也会为该组创建一个唯一的组id，502就是代表该用户所在组的id
100：代表文件的大小
Mar：代表文件创建时间
Test.js：代表文件名
```

## linux系统的用户所在组、文件所有者、文件所在组
```
linux系统的用户所在组、文件所有者、文件所在组
在linux(windows也一样)系统中，每个用户都会有所在组，在哪个组就具有哪个组的权限，一个用户可以加入到多个组
groupadd [添加组]如：groupadd policeman(创建一个警察组)
groupdel [删除组]如：groupdel policeman(删除这个警察组)
查看linux系统中所有组的信息：[cat /etc/group] (查看信息通常用cat命令，而不是用vi)

useradd -g 组名 用户名[添加一个用户，并将该用户添加到指定组] 
如：useradd -g policeman superhan(添加一个superhan用户，并将其添加到policeman组当中)
查看linux系统中所有用户的信息：[cat /etc/passwd]

usermod [改变用户的所在组等(需要root权限)] 
如：usermod -g policeman xiaoming [改变用户所在组](将xiaoming所在组改为policeman)
    usermod -d 目录名 用户名 [改变用户的主目录] 
如：usermod -d / superhan(之前superhan用户的主目录是在/home/superhan，现在将该用户的主目录改为/superhan)

chmod [修改该用户的访问权限(只能是root用户和当前用户可以改)]
如：chmod 764 superhan (修改superhan用户主目录访问权限为764,[7代表该文件夹的所有者对其访问权限是rwx(可读、可写、可执行)，6代表该用户所在组的其他用户对其访问权限是rw(可读、可写)，4代表其他组用户对其访问权限是r(可读)])
    chmod 644 AAA.txt (修改AAA.txt这个文件的访问权限为644,[6代表该文件的所有者对其访问权限是rw(可读、可写)，第二个4代表该用户所在组其他用户对其访问权限是r(可读)，第三个4代表其他组用户对其访问权限是r(可读)])

chown [改变文件的所有者(只能是root权限)]
如：chown xiaofang AAA.txt (修改AAA.txt文件所有者为xiaofang)

chgrp [改变该文件的所在组(只能是root权限)]
如：chgrp murder AAA.txt (修改AAA.txt文件的所在组为murder组)

```