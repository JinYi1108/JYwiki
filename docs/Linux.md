Linux.markdown目的在于简单记录一些Linux基本知识点方便后续回顾（内容来自网络）

# Linux系统目录（待细化）


<img src="https://pic2.zhimg.com/v2-1f6cdbc3e0765ae8484624eaa2a08ab9_r.jpg">

![](https://pic2.zhimg.com/v2-1f6cdbc3e0765ae8484624eaa2a08ab9_r.jpg)

```
bin 存放二进制可执行文件(ls,cat,mkdir等)
boot 存放用于系统引导时使用的各种文件
dev 用于存放设备文件
etc 存放系统配置文件
home 存放所有用户文件的根目录
lib 存放跟文件系统中的程序运行所需要的共享库及内核模块
mnt 系统管理员安装临时文件系统的安装点
opt 额外安装的可选应用程序包所放置的位置
proc 虚拟文件系统，存放当前内存的映射
root 超级用户目录
sbin 存放二进制可执行文件，只有root才能访问
tmp 用于存放各种临时文件
usr 用于存放系统应用程序，比较重要的目录/usr/local 本地管理员软件安装目录
var 用于存放运行时需要改变数据的文件
```
# 通配符

*：匹配任何字符和任何数目的字符  
?：匹配单一数目的任何字符  
[ ]：匹配[ ]之内的任意一个字符  
[! ]：匹配除了[! ]之外的任意一个字符，!表示非的意思  

# Linux基本命令

```
pwd：查看用户的当前目录
ls：显示文件或目录信息
mkdir：当前目录下创建一个空目录
mv：移动文件或目录、文件或目录改名
rm：删除文件或目录
ln：建立链接文件 
find：查找文件
file/stat：查看文件类型或文件属性信息
cat：查看文本文件内容
more：可以分页看
less：不仅可以分页，还可以方便地搜索，回翻等操作
tail -10： 查看文件的尾部的10行
head -20：查看文件的头部20行
echo：把内容重定向到指定的文件中 ，有则打开，无则创建
```

#### cd 更改文件目录
切换到主目录
cd
切换到主目录
cd ~
切换到目录/tmp
cd /tmp
切换到当前目录的dir目录
cd dir
切换到根目录
cd /
切换到上一级目录
cd ..
切换到二级目录
cd ../..
切换到主目录，例如是root用户，则切换到/root下
cd ~

#### 压缩解压命令


> * 压缩  
gzip filename  
bzip2 filename  
tar -czvf filename  
> * 解压  
> gzip -d filename.gz  
bzip2 -d filename.bz2  
tar -xzvf filename.tar.gz  



