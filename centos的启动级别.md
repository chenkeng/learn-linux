Linux系统设置系统启动模式的方式可以修改(必须要以root身份登录才能修改)。修改系统启动模式的配置文件是   /etc/inittab。

我们在切换到root用户后，然后 vim /etc/inittab, 就可以修改并查看该配置文件：
```js
[root@linux-node1 ~]# cat /etc/inittab
# inittab is no longer used when using systemd.
#
# ADDING CONFIGURATION HERE WILL HAVE NO EFFECT ON YOUR SYSTEM.
#
# Ctrl-Alt-Delete is handled by /usr/lib/systemd/system/ctrl-alt-del.target
#
# systemd uses 'targets' instead of runlevels. By default, there are two main targets:
#
# multi-user.target: analogous to runlevel 3
# graphical.target: analogous to runlevel 5
#
# To view current default target, run:
# systemctl get-default
#
# To set a default target, run:
# systemctl set-default TARGET.target
#
```
```
# multi-user.target类似于runlevel 3;
# graphical.target类似于runlevel5

#查看默认运行级别的方式为
systemctl get-default

#设置默认运行级别的方式
systemctl set-default TARGET.target
```

### 运行级别对应表

init级别  |	systemctl target
--|--
0	| shutdown.target
1	| emergency.target
2	| rescure.target
3	| multi-user.target
4	| 无
5	| graphical.target
6	| 无

### 设置运行级别

命令格式：
systemctl [command] [unit.target]
参数详解：
command:
get-default :取得当前的target
set-default :设置指定的target为默认的运行级别
isolate :切换到指定的运行级别
unit.target :表中列出的运行级别
systemctl	| 命令 | 说明
--|--|--
systemctl | get-default	| 获得当前的运行级别
systemctl | set-default multi-user.target	| 设置默认的运行级别为mulit-user
systemctl | isolate multi-user.target	| 在不重启的情况下，切换到运行级别mulit-user下
systemctl | isolate graphical.target	| 在不重启的情况下，切换到图形界面下


Linux 7 一下的版本系统启动级别介绍
Linux系统中默认的系统启动一共有7种，分别是：

0：关机(不要设置这个！)
1：单用户(类似于windows操作系统的安全模式)
2：多用户状态没有网络服务     
3：多用户状态由网络服务(在做开发时，通常设置成这个启动级别，直接进入到命令行的界面)
4：系统未使用保留给用户(不要设置这个！)       
5：图形界面(这是linux默认的启动级别，直接进入图形界面)
6：系统重启(不要设置这个！)

下面那句：

id:5:initdefault:   // 设置系统默认的启动级别
就是用来设定系统的默认启动级别，Linux系统中默认是启动级别5，也就是图形界面启动

如果需要修改成默认级别为开发模式，只需要将 5 改成 3 即可

如：

将 id:5:initdefault:  改成   id:3:initdefault:
然后保存退出，重新启动一下系统 输入  reboot 命令即可。

警告：千万不要将启动基本设置为0， 4， 6！！！！！！

这时就会发现进入Linux系统的界面已经变成开发者模式了！

如果我们只是需要在Linux上做开发、部署项目的话，建议一般将系统启动模式设置为 开发模式！


[注]
如果有恶意用户将系统启动级别设置成0、4、6，我们该怎么解决这个问题？

在linux系统启动界面，我们快速按键盘上的 [e] 按钮，然后进入到了grub引导界面(这个根据Linux的版本可能有不同，我的CentOS6.4是需要在启动时按F2进入引导界面，
这个可以根据自己安装的Linux系统在开机时的提示进入引导界面)，
在这个界面中选择第二个选项，然后再按下键盘上的 [e]按钮，在进入修改界面后，在最后输入`[ 1](1前面有空格)`
这样，linux系统在启动时就会以 单用户级别 启动起来(为什么这里不将其设置成3或者5，是因为linux系统
在启动时首先会去检查 /etc/inittab 文件的设定启动级别，如果在这时设置成5或者3，系统还是进不去，只能设置成1)
在设置好以后，按下键盘的[b]按钮，系统就能重新启动，并进入 单用户级别，这样我们就可以按照之前的方法修改
linux系统的启动级别。