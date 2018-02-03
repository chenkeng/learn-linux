>  centos 6.5 搭建FTP 服务器 
1. 2种方式安装 vsftpd
    * chkconfig --list来查看是是否已经安装了vsftpd 服务
    * yum install -y vsftpd
    * 需要将vsftpd.rpm 包下载到本地  rpm -ih vsftpd.rpm   

*以下第二步不一定需要*   

2. 关闭iptables
    * 查看防火墙状态：/etc/init.d/iptables status
    * 关闭：service iptables stop  或者 /etc/init.d/iptables stop
    * 每次开机自动关闭:
    * chkconfig --level 35 iptables off

3. 启动服务命令：
    * service vsftpd start  启动服务
    * 查看ftp服务状态：service vsftpd status
    * 关闭ftp服务：service vsftpd stop
    * service vsftpd restart 有改动需要重启的情况下  

4. 修改配置文件(一般配置这几个就可以,vsftpd.conf中不包含的配置项可能需要自己创建)  
    * vi /etc/vsftpd/vsftpd.conf
    * anonymous_enable=YES 匿名用户是否开启 YES or NO
    * ascii_upload_enable=YES #允许使用ASCII模式上传
    * ascii_download_enable=YES #设定支持ASCII模式的上传和下载功能。
    * *pam_service_name=vsftpd* #PAM认证文件名。PAM将根据/etc/pam.d/vsftpd进行认证
    * userlist_enable=YES
    * userlist_deny=NO
    * local_root=/home/ftp_dir  此处为定义FTP服务器的文件存放目录
    * tcp_wrappers=YES
    * use_localtime=YES   

> 其他配置作用解释                       
   
    * local_enable=YES #设定本地用户可以访问。注：如使用虚拟宿主用户，在该项目设定为NO的情况下所有虚拟用户将无法访问。
    * chroot_list_enable=YES #使用户不能离开主目录
    * xferlog_file=/var/log/vsftpd.log #设定vsftpd的服务日志保存路径。注意，该文件默认不存在。必须要手动touch出来
    * guest_enable=YES #设定启用虚拟用户功能。
    * guest_username=ftp #指定虚拟用户的宿主用户。centos 里面已经有内置的ftp用户了（注：此用户在chroot_list_file=/etc/vsftpd/chroot_list文件里所指定的用户）-RHEL/CentOS中已经有内置的ftp用户了
    * user_config_dir=/etc/vsftpd/vuser_conf #设定虚拟用户个人vsftp的RHEL/CentOS FTP服务文件存放路径。存放虚拟用户个性的CentOS FTP服务文件(配置文件名=虚拟用户名)    

> 创建chroot list，将ftp用户加入其中：   

    * touch /etc/vsftpd/chroot_list
    * echo ftp>> /etc/vsftpd/chroot_list  #指定虚拟用户的宿主用户

5. 添加用户
    * useradd superhan -s /sbin/nologin  # 增加superhan 的用户
    * passwd 密码  # 设置superhan用户的密码

6. 编辑user_list文件，允许 XX 用户访问FTP
    * vi /etc/vsftpd/user_list
    * 根据需要是否允许以下用户访问/禁用 FTP 

7.  共享目录权限配置，启动服务（以上设置的ftp文件存放目录,此处用的superhan用户举例）
    * chown -R superhan /home/ftp_dir
    * chmod -R 755 /home/ftp_dir 

8. 重启服务
    * service vsftpd start 启动服务
    * chkconfig vsftpd on  开机启动

9. 客户端用户登录(输入用户名和密码)
    * 浏览器输入  ftp://127.0.0.1
    * windows 用户资源管理器输入 ftp://127.0.0.1 

10. [参考文章:https://jingyan.baidu.com/article/425e69e6db71a7be15fc16e9.html](https://jingyan.baidu.com/article/425e69e6db71a7be15fc16e9.html)
