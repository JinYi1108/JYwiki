# Git基础

## Git工作区、暂存区和版本库

#### 三者的概念   

>- 工作区：电脑里能看到的目录。    
>- 暂存区：stage/index。一般存放在 .git 目录下的 index 文件（.git/index）中,暂存区有时也叫作索引（index）。  
>- 版本库：工作区有一个隐藏目录 .git，这个不算工作区，而是 Git 的版本库。  

#### 三者关系

![](https://www.runoob.com/wp-content/uploads/2015/02/1352126739_7909.jpg)

>- 左侧为工作区，右侧为版本库。    
>- 版本库中标记为 "index" 的区域是暂存区，标记为 "master" 的是 master 分支所代表的目录树。  
>- 图中我们可以看出 "HEAD" 实际是指向 master 分支的一个"游标"。所以图示的命令中出现 HEAD 的地方可以用 master 来替换。   
>- 图中objects 标识的区域为 Git 的对象库，实际位于 ".git/objects" 目录下，里面包含了创建的各种对象及内容。  

#### 互相之间的操作

1. 当对工作区修改（或新增）的文件执行 ***git add*** 命令时，<span style="color: red;">暂存区的目录树被更新，同时工作区修改（或新增）的文件内容被写入到对象库中的一个新的对象中</span>，而该对象的ID被记录在暂存区的文件索引中。

2. 当执行提交操作（***git commit***）时，<span style="color: red;">暂存区的目录树写到版本库（对象库）中</span>，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。

3. 当执行 git reset HEAD 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。

4. 当执行 git rm --cached <file> 命令时，会直接从暂存区删除文件，工作区则不做出改变。

5. 当执行 git checkout . 或者 git checkout -- <file> 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区中的改动。

6. 当执行 git checkout HEAD . 或者 git checkout HEAD <file> 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。

***

## Git创建仓库

#### git init
- Git 使用 ***git init*** 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 仓库中运行。  
- 在执行完成 ***git init*** 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变。



###### 当前目录

使用当前目录作为 Git 仓库，我们只需使它初始化。
```
git init
```
该命令执行完后会在当前目录生成一个 .git 目录。

###### 指定目录

使用指定目录作为Git仓库。
```
git init jinyi
```
初始化后，会在 jinyi 目录下出现一个名为 .git 的目录。

###### 文件纳入
如果当前目录下有几个文件想要纳入版本控制，需要先用 ***git add*** 命令告诉 Git 对这些文件进行跟踪，然后提交：
```
$ git add *.c
$ git add README
$ git commit -m '初始化项目版本'
```
以上命令将目录下以 .c 结尾及 README 文件提交到仓库中。

在 Linux 系统中，commit 信息使用单引号 '，Windows 系统，commit 信息使用双引号 "。

***

#### git clone

我们使用 ***git clone*** 从现有 Git 仓库中拷贝项目（类似 svn checkout）。  
克隆仓库的命令格式为：
```
git clone <repo>
```
如果我们需要克隆到指定的目录，可以使用以下命令格式：
```
git clone <repo> <directory>
```

###### 参数说明

repo:Git 仓库。  
directory:本地目录。

###### 例子

比如，要克隆 Ruby 语言的 Git 代码仓库 Grit，可以用下面的命令：
```
$ git clone git://github.com/schacon/grit.git
```
执行该命令后，会在当前目录下创建一个名为grit的目录，其中包含一个 .git 的目录，用于保存下载下来的所有版本记录。

如果要自己定义要新建的项目目录名称，可以在上面的命令末尾指定新的名字：
```
$ git clone git://github.com/schacon/grit.git mygrit
```
#### 配置

git 的设置使用 ***git config*** 命令。  
显示当前的 git 配置信息：
```
$ git config --list
```
编辑 git 配置文件:
```
$ git config -e    # 针对当前仓库 
```
或
```
$ git config -e --global   # 针对系统上所有仓库
```
设置提交代码时的用户信息：
```
$ git config --global user.name "runoob"
$ git config --global user.email test@runoob.com
```

<span style="color: red;">如果去掉 ***--global*** 参数只对当前仓库有效。</span>

## Git基本操作