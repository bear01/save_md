### Linux基础知识



多用户多任务的操作系统，拥有良好的用户界面

支持多种处理器架构，移植方便

#### 目录结构

/bin: 存放着经常使用的命令

/boot: 启动Linux时使用的一些核心文件以及镜像文件

/dev: （Device）存放Linux外部设备

/etc: 存放所有的系统管理所需的配置文件和子目录

/home: 用户的主目录，在Linux中每个用户都以后自己的目录，一般该目录是以用户的 账号命名

/lib: 存放系统中最基本的动态连接库 ，类似于Windows的dll文件

/opt :给主机额外安装软件所摆放的目录

/root: 系统管理员，超级权限者的用户主目录

/tmp: 存放临时文件

/usr: 很重要的一个目录，用户的很多应用程序都放在这个目录下

/var:存放经常修改的目录， 包括各种日志

在linux系统中，所有文件和目录都会被组织成一个以根节点开始的倒置树状结构





#### 基本命令



cp:复制文件

~~~
cp file1 file2 复制一个文件 
cp dir/* . 复制一个目录下的所有文件到当前工作目录 
cp -a /tmp/dir1 . 复制一个目录到当前工作目录 
cp -a dir1 dir2 复制一个目录 
cp -r dir1 dir2 复制一个目录及子目录
~~~

mv:移动文件

rm:删除文件

~~~linux
rm -f file1 删除一个叫做 'file1' 的文件' 
rmdir dir1 删除一个叫做 'dir1' 的目录' 
rm -rf dir1 删除一个叫做 'dir1' 的目录并同时删除其内容 
rm -rf dir1 dir2 同时删除两个目录及它们的内容 
~~~

pwd:查看当前目录中的文件

mkdir:创建目录

~~~linux
mkdir dir1 创建一个叫做 'dir1' 的目录' 
mkdir dir1 dir2 同时创建两个目录 
mkdir -p /tmp/dir1/dir2 创建一个目录树
~~~



ls-l:查看文件权限等信息

~~~
[root@www /]# ls -l
total 64
drwxr-xr-x 2 root  root  4096 Feb 15 14:46 cron
drwxr-xr-x 3 mysql mysql 4096 Apr 21  2014 mysql
~~~

find: 文件搜索

mount: 挂载文件系统

passwd: 修改口令

创建一个新用户：useradd user1

删除一个用户： userdel -r user1 (-r 排除主目录)

创建一个新用户组：groupadd group_name

删除一个用户组：groupdel group_name



chomd和chown : 设置权限

~~~
chmod ugo+rwx directory1 设置目录的所有人(u)、群组(g)以及其他人(o)以读（r ）、写(w)和执行(x)的权限 
chmod go-rwx directory1 删除群组(g)与其他人(o)对目录的读写执行权限 
chown user1 file1 改变一个文件的所有人属性 
chown -R user1 directory1 改变一个目录的所有人属性并同时改变改目录下所有文件的属性 
~~~

**打包和压缩文件**

~~~
gzip file1 压缩一个叫做 'file1'的文件 
rar a file1.rar test_file 创建一个叫做 'file1.rar' 的包 
rar x file1.rar 解压rar包 
tar -xvf archive.tar 释放一个包
zip file1.zip file1 创建一个zip格式的压缩包
~~~

**RPM包**

~~~
rpm -qa 显示系统中所有已经安装的rpm包 
rpm -ivh package.rpm 安装一个rpm包 
rpm -e package_name.rpm 删除一个rpm包 
rpm -U package.rpm 更新一个rpm包但不改变其配置文件 
~~~

**APT软件工具**

~~~
apt-get install package_name 安装/更新一个 deb 包 
apt-cdrom install package_name 从光盘安装/更新一个 deb 包 
apt-get update 升级列表中的软件包 
apt-get upgrade 升级所有已安装的软件 
apt-get remove package_name 从系统删除一个deb包 
apt-get check 确认依赖的软件仓库正确 
apt-get clean 从下载的软件包中清理缓存 
~~~

**查看文件内容**

~~~
cat file1 从第一个字节开始正向查看文件的内容 
tac file1 从最后一行开始反向查看一个文件的内容 
more file1 查看一个长文件的内容 
~~~

**网络**

~~~~
ifconfig eth0 显示一个以太网卡的配置
ifup eth0 启用一个 'eth0' 网络设备 
ifdown eth0 禁用一个 'eth0' 网络设备 
ifconfig eth0 192.168.1.1 netmask 255.255.255.0 控制IP地址 
netstat  查看网络是否连通
~~~~

**sudo**

sudo 是一种权限管理机制，管理员可以授权于一些普通用户去执行一些 root 执行的操作，而不需要知道 root 的密码



**关机、重启**

~~~
shutdown -h now 关闭系统
shutdown -r now 重启
~~~



## 常见面试问题



1. 怎么查看当前进程，执行退出，查看当前路径

   `ps	exit	pwd`

2. 建立软链接和硬链接

   `In -s slink source`   // 软链接

   `In link source`	//硬链接

3. 终端是在哪个文件下

   `/dev/tty` 		--终端

   `/dev/null`		--黑洞文件

4. grep命令有什么作用？

   一种强大的文本搜索工具，可以使用正则表达式搜索文本，并打印出来

5. linux 中进程有哪几种状态？

   * 不可中断状态 D
   * 暂停/跟踪状态 T
   * 就绪状态 
   * 运行状态 R
   * 可中断睡眠状态
   * 僵尸状态 Z
   * 退出状态

6. 查看后台任务

   `job -l`

7. 终止进程 用什么命令？

   `kill -编号`

8. 查看当前谁在使用该主机？

   `who` 

   `who am i`   --查看自己所在的终端信息

9. 查看磁盘使用空间

   `df -hl`

10. 如果一个新手想要知道当前系统支持的所有命令？

    `compgen -c`

11. 说一说比较常见的linux命令

    ls、cd、clear、kill、mkdir、mv、rm、ps、grep、vi、cat、tar、

12. 查看端口

    netstat -anp |grep 端口号

13. vim编译器

    三种模式：命令模式、输入模式、末行模式

