## 一些常用命令：
```
shutdown -h now    现在马上关机
shutdown -r now    现在重新启动
reboot             现在重新启动
su -               如果当前是普通用户，则输入这条命令切换到管理员用户(root)，如果要切换到其他用户则敲入  su - 用户名         如:　　su - superhan
logout             从当前用户注销(如果是在图形界面的终端的话，则是输入  exit  命令来退出当前用户)
cd                 切换目录[如：cd / 表示切换到linux的根目录！！(/)表示根目录]
pwd                显示用户当前在哪个路径下的命令 (这个命令用的特别多，在命令行里如果不知道当前所处文件夹，可以输入该命令 pwd
```
## 创建用户、删除用户的用户管理命令：
```
useradd      用户名    [添加一个用户] 如：useradd superhan
passwd       用户名    [给指定的用户名修改密码] 如：passwd superhan
userdel      用户名    [删除一个用户，但是该用户在home文件下的子文件夹会保留] 如：userdel superhan
userdel -r   用户名    [删除一个用户，并且删除连同该用户在home文件夹下的子文件夹] 如：userdel -r superhan
```
## 其他命令
```
ls                     [列出文件和目录] 如：ls /home (列出home下面的所有文件和目录)
ls -l                  [列出的文件和目录以长列表显示] 如：ls -l /home
ls -a                  [列出隐藏的文件和目录] 如：ls -a /home
mkdir                  [建立目录] 如：mkdir superhan
rmdir                  [删除空目录] 如：rmdir superhan(只能删除空目录，如果该目录下还有其它文件则该命令无效)
touch                  [建立空文件] 如：touch Test.js
cp                     [复制命令] 如：cp /home/Test.js / (将home路径下的Test.js文件复制到根目录下)
cp -r dir1 dir2        [-r表示递归，将dir1代表的文件夹及里面的文件复制到dir2路径那里] 
如：cp -r /home/superhan /(将home下的superhan文件夹复制到根目录下)

mv                     [移动文件和改文件名] 如：mv /home/Test.js /(表示将home下的Test.js文件移动到根目录下) 
mv /Test.js /Hello.js(表示将Test.js文件名改成Hello.js)
rm                     [删除文件和目录] 如：rm /Test.js (将根目录下的Test.js删除)[注：如果该文件是个文件夹则删除不了]
rm -rf *               [(-r表示递归、f表示强制删除)删除所有内容，包括目录和文件夹] 如：rm -rf /home/superhan(强制删除home下的superhan文件夹)。*一定要注意 rm -rf / home 不要手快有空格*

ln                     [建立符号链接，类似于windows中的快捷方式(需root权限或相应用户权限)]
ln -s 源目标 目的目标    如：ln -s /etc/inittab /inittab(这样就会在根目录下建立一个inittab链接，该链接指向了etc目录下的inittab文件)

more                   [显示文件内容，带分页]
less                   [显示文件内容，带分页] 如果我们的一个文件里面有很多内容，就可以使用more命令给其分页 
如：more /etc/prelink.conf (给etc下面的prelink.conf文件内容进行分页显示)

|                      [管道命令] [这个命令在linux系统中用的很多] ( | 这个命令的作用就是将 | 前面的那个命令的结果交给 | 后面的那个命令来处理)
如：ls /etc | more (|前面那个命令是显示出etc文件夹下的所有文件及目录，|后面那个命令就是以分页形式显示，
所以这个命令的意思就是 以分页来显示出etc目录下的所有文件和目录)

grep                   [在文本中查询内容] 这条命令用的非常多 如：grep "superhan" /home/Test.txt (在Test.txt文件中查询出包含有superhan的那行文本信息)
 如果需要显示出所查文本所在行数则使用： grep -n "sueprhan" /home/Test.txt(查询出Test.txt文件中superhan该信息所在行数以及改行所有文本)
find                   [搜索文件及目录] 如：find /home -name Test.js (在home文件夹下或者home中所有的子文件夹下查找名字为Test.js的文件)

重定向命令[> 、>>、<]
如：ls -l /etc> a.txt (将etc下面的列表信息写入到a.txt文件中[覆写]，如果之前不存在a.txt文件，则创建a.txt文件然后将信息写进去，
如果存在a.txt文件，则会覆盖掉之前的信息)
ls -al /etc>> aa.txt (将etc下面的列表信息追加到aa.txt文件信息后面)
从文件中输入信息 aaa < bbb

```

## 查看修改 命令
```
cat、vi(cat命令只能查看文件，vi命令既可以查看文件又可以修改文件，对于一些关键文件我们一般使用cat命令查看)
如：cat /etc/profile (只是查看该文件里的内容)　　　　vi /etc/profile (查看、并且可以修改该文件里的内容)
```