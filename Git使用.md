 https://www.cnblogs.com/zhangxiaoyong/p/6000084.html#_label2 

## 基本命令

创建文件  touch  test.txt

编辑文件  vim  test.txt

查看文件内容 cat test.txt

## Git配置

1.查看配置 git config -l

![1585969783143](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1585969783143.png)

2.设置用户名和邮箱

当你安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中：

```
$ git config --global user.name "liuyu"  #名称
$ git config --global user.email 947892227@qq.com   #邮箱
```



## Git创建仓库

**1. git init**  

​     在执行完成 **git init** 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变 

使用方法： 使用当前目录作为Git仓库，我们只需用git init使它初始化。 

（也可以在指定目录下初始化，如git init newrepo 会在 newrepo 目录下会出现一个名为 .git 的目录 ）

**2.git clone****

 使用 **git clone** 从现有 Git 仓库中拷贝项目：git clone <repo>

 如果我们需要克隆到指定的目录，可以使用以下命令格式：

​     git clone <repo> <directory>

​	(repo:Git 仓库。  directory:本地目录。)

3.将文件添加到版本库

第一步：**git add <file>**

第二步：**git commit -m "wrote a readme file**" 

（ `-m`后面输入的是本次提交的说明 ）

## vi/vim编辑器

1.vi/vim 共分为三种模式，分别是**命令模式（Command mode）**，**输入模式（Insert mode）**和**底线命令模式（Last line mode）**。 

（1）命令模式

 用户刚刚启动 vi/vim，便进入了命令模式。如vim readme.txt 

若想要编辑文本：启动Vim，进入了命令模式，按下i/a/o，切换到输入模式。

（2）输入模式

在命令模式下按下i就进入了输入模式。

（3）底线命令模式

在命令模式下按下:（英文冒号）就进入了底线命令模式。

基本命令有：

:q 退出程序

:w 保存文件

:wq 保存并退出

![image](https://github.com/liuyu105/Git/blob/master/images/vi-vim-cheat-sheet-sch.gif)

## 查看仓库状态

1. **git status**

   命令可以让我们时刻掌握仓库当前的状态 

2. **git diff**

   查看具体修改的内容

   如：git diff readme.txt

   ```
   diff --git a/readme.txt b/readme.txt
   index 46d49bf..9247db6 100644
   --- a/readme.txt
   +++ b/readme.txt
   @@ -1,2 +1,2 @@
   -Git is a version control system.
   +Git is a distributed version control system.
    Git is free software.
   ```

3. **git commit**

    Git也是一样，每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为`commit`。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个`commit`恢复，然后继续工作，而不是把几个月的工作成果全部丢失。 

4. **git log**

    `git log`命令显示从最近到最远的提交日志 

    如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline` ，即git log --pretty=oneline

## 版本回退

1.首先，Git必须知道当前版本是哪个版本，在Git中，用`HEAD`表示当前版本，也就是最新的提交`1094adb...`，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。

2.回退到上一个版本：**git reset --hard HEAD^**

3.当回退到上一版本后，最新版本已经看不到了。 只要上面的命令行窗口还没有被关掉， 就可以找到其版本的commit  id，输入 git reset --hard 1094a【 版本号没必要写全，前几位就可以了 】

4.**git reflog**用来记录你的每一次命令 ,当找不到其版本号时，可以通过这种方式查找。

![1582271456168](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1582271456168.png)

5.cat readme.txt  查看文件的内容

6.**撤销修改**

（1）`git checkout -- file`可以丢弃工作区的修改： 

命令`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，这里有两种情况：

一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态。

**注意：**命令git checkout — readme.txt 中的 — 很重要，如果没有 — 的话，那么命令变成创建分支了。

（2） `git reset HEAD `可以把暂存区的修改撤销掉 ，重新放回工作区

所以后面还要使用checkout丢弃工作区的修改 



## 删除文件

![1585911717806](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1585911717806.png)

rm test.txt

只要没有commit之前，若想在版本库中恢复此文件，只需要checkout就可。

![1585911947025](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1585911947025.png)

## 远程仓库

 先注册github账号，由于你的本地Git仓库和github仓库之间的传输是通过SSH加密的，所以需要一点设置： 

   第一步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果有的话，直接跳过此如下命令，如果没有的话，打开命令行，输入如下命令：

 ssh-keygen 

第二步：登录github,打开” settings”中的SSH Keys页面，然后点击“Add SSH Key”,填上任意title，在Key文本框里黏贴id_rsa.pub文件的内容。

 第三步：git config –global 参数，有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱。 

![1585912221716](C:\Users\梦晨涌京\AppData\Roaming\Typora\typora-user-images\1585912221716.png)



 git pull origin master --allow-unrelated-histories //把远程仓库和本地同步，消除差异 

