1.Git error： hint: Updates were rejected because the remote contains work that you do hint: not have locally. This is usually caused b

![image](https://github.com/liuyu105/Git/blob/master/images/1585969535068.png)

解决方法： 

$ git pull origin master
$ git push origin master 

2.Git冲突：commit your changes or stash them before you can merge.

![image](https://github.com/liuyu105/Git/blob/master/images/1585983143766.png)

解决方法：

放弃本地修改，直接覆盖之

​    git reset *--hard*

​    git pull

最后git push origin master

3.