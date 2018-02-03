* 安装 CentOS  
1. 下载CentOS 官网：https://www.centos.org/download/
2. DVD ISO：标准安装版，一般下载这个就可以了（推荐）
3. Everything ISO：对完整版安装盘的软件进行补充，集成所有软件。（包含- –CentOS7的一套完整的软件包，可以用来安装系统或者填充本地镜像）
4. Minimal ISO：迷你版，小巧、安装快速、自带的软件少

* 修改语言
1. 系统默认语言是英文，CentOS 右上角设置有一个语言选择框

* 联网
1. 进入目录：  /etc/sysconfig/network-scripts/
2. vim ifcfg-eno16777736
3. 将最后一行的 ONBOOT=no 改为ONBOOT= yes ，最后输入: wq ，保存并退出。
4. 果发现不能上网，则需要重启网络服务，输入以下命令：service network restart

* 常用的 Yum 命令
1. 显示已经安装的软件包 yum list installed
2. 查找可以安装的软件包 （以 tomcat 为例） yum list tomcat
3. 安装软件包 （以 tomcat 为例） yum install tomcat
4. 卸载软件包 （以 tomcat 为例） yum remove tomcat
5. 列出软件包的依赖 （以 tomcat 为例） yum deplist tomcat
6. -y 来应答所有的 yes  如 yum -y install tomcat
7. info 显示软件包的描述信息和概要信息  yum info tomcat
8. 升级软件包 yum update
9. 升级某一个软件包 ，以升级 tomcat 为例  yum update tomcat
10. 检查可更新的程序  yum check-update  
11. Yum 可视化图形界面 Yumex   yum install yumex

* ssh 远程连接
1. centos系统查看本机IP地址  ifconfig -a
2. centos 查询上网公网IP  curl ifconfig.me
3. 远程连接 ssh chenchaohan@14.116.189.89

* 常用命令
1. clear 清屏   ctrl+l
2. 进入 centos home 目录，不管当前在哪个目录，都可以执行这个操作  cd ~/Desktop
3. rm 删除文件   删除home目录下的test目录 rm /home/test
4. -r是递归的删除参数表中的目录及其子目录。 目录将被清空并且删除。 当删除目录包含的具有写保护的文件时用户通常是被提示的。 rm -r /home/test
5. -rf : f 是不提示用户，删除目录下的所有文件。请注意检查路径，输成别的目录就悲剧了。 rm -rf /home/test
6. rmdir 删除空文件夹   rmdir abc  
7. mv 移动文件
    * 移动 file1.txt 文件到 newdir 目录  mv file1.txt newdir
    * 移动多个文件到 newdir 目录 mv file1.txt file2.txt newdir

8. cp 复制文件
    * cp file1 file2
    * pwd 显示文件路径
    * u 切换到用户模式  su root

9. vim 打开文本
    *  命令行模式（command mode）控制屏幕光标的移动，字符、字或行的删除，移动复制某区段及进入Insert mode下，或者到 last line mode。
    *  插入模式（Insert mode）只有在Insert mode下，才可以做文字输入，按「ESC」键可回到命令行模式。
    * 底行模式（last line mode）将文件保存或退出vi，也可以设置编辑环境，如寻找字符串、列出行号……等。
    - 命令行模式 —> 插入模式 ：按 i 键
    - 插入模式 —> 命令行模式 ： 按 esc 键
    - 命令行模式 —> 底行模式 ：按 Shift + 冒号 键

10. vim 退出
    * wq： 保存文件并退出vi
    * wq!： 强制保存文件，并退出vi
    * q：不保存文件，退出vi
    * q! ：不保存强制退出
    * w： 保存文件但不退出vi
    * w!： 强制保存，不退出vi
    * e!： 放弃所有修改，从上次保存文件开始再编辑
