ls

​    不带参数就显示当前目录下的所有文件

​    程序可以加参数

​    -l 显示详细信息

​    -h 人性化显示文件尺寸

​    -a 显示所有文件， 以 . 开头的文件是隐藏文件

​    还可以带一个目录当参数，这样就会显示这个目录

下面两个是等价的

ls -l -h

ls -lh



cd

​    cd Desktop

​    改变当前目录

​    . 代表当前目录



​    .. 代表上级目录

​    cd 不带参数就回到默认的家目录

​    每个用户都有一个家目录，默认在 /home/用户名

​    root 用户的家目录是 /root

cp

​    复制出一个文件，用法如下

​    cp a.txt b.txt

​    复制 a.txt 并把新文件取名为 b.txt

​    复制目录要加上 -r 参数

​    cp -r a b

mkdir

​    创建一个目录

​    -p 可以一次性创建多层目录

​    mkdir -p a/b/c

rmdir

​    只能用来删除一个空目录

rm

​    这个命令直接删除东西，很危险，一般不要用

​    删除文件或者目录

​    -f 强制删除

​    -r 用来删除目录

mv

​    移动文件或者文件夹

​    也可以用来改名

​    mv a.txt b.txt

​    mv b.txt ../

​    mv b.txt ../gua.txt

​    可以用 mv xx /tmp 的方式来将文件放入临时文件夹

​    （/tmp是操作系统提供的临时文件夹，重启会删除里面的所有文件）





权限操作

sudo

​    用管理员帐户执行程序

​    比如安装程序或者修改一些系统配置都需要管理员权限

su

​    switch user， 切换用户

​    su gua

​    su root



文件权限    文件类型 用户 用户组 文件大小  修改日期     文件名

-rw-rw-r--  1       gua gua     10      11/09 20:28 b.gua

drwxrwxr-x  2       gua gua     4096    11/09 20:28 tmp

文件类型    是否可读  是否可写  是否可执行

d           r       w           x

\-           r       w           x

三组 rwx 分表代表 所属用户|同组用户|其他用户

rwx 可以用数字表示为 421

于是乎

r-- 就是 4

rw- 就是 6

rwx 就是 7

r-x 就是 5



history

​    查看历史命令

grep

​    查找

这两个一般配合使用

​    history | grep touch



ps

​    查看进程, 一般用下面的用法

​    ps ax

ps ax | grep python

​    查看带 python 字符串的进程

netstat -antp

查看监听



kill 和 killall 杀进程

​    kill [pid]

​    kill -9 [pid]

​    kill -15 [pid]

​    killall 是用进程名字来杀进程





软件安装

====

apt-get install 软件名

比如下面

apt-get install python3



vim 修改命令

=====

vim 某文件名

:w：将编辑的数据写入到硬盘中。

:q：离开vi.后面加！为强制离开。

:wq：保存后离开。:wq!为强制保存后离开。