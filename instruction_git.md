# 如何使用 git 工具

1.下载 git 客户端，安装。

2.新建工作目录，使用 git bash 进入工作目录。

3.git 本地库初始化。
  命令：git init
  效果：生成一个 .git 的隐藏目录，里面包含本地库的文件。

4.设置签名
  形式
       用户名：walden
       Email：walden94me@gmail.com
  作用：区分不同开发人员的身份。这里的签名和登录远程库(代码托管中心)的账号、密码没有任何关系
  命令：
       项目/仓库级别
       		gitconfig user.name yuliang
		gitconfig user.email 550620502@qq.com
		配置信息可以到本地库 .git/config 查看
       系统级别(常用):
       		gitconfig --global user.name walden
		gitconfig --global user.email walden94me@gmail.com
		配置信息可以到根目录 .gitconfig 查看

5.查看系统状态
  git status
  文件的状态：
  	a. touch 创建了文件，但是 git 无法追踪，呈红色
	b. git add 无法追踪的文件添加的暂存区，git 可以追踪，稍后可以提交到本地库

6.追踪文件，添加到缓存区
  git add filename 		//将文件添加到暂存区
  git rm --cache filename 	//将文件移出暂存区

7.提交到本地库
  git commit filename   //提交操作
  提交完成后自动进入vim编辑模式，可以在第一行备注提交信息。

8.查看提交日志
  git log

9.前进后退版本
  a.基于索引操作【推荐】  
  	git reset --hard 【局部索引值】
	git reset --hard  xxxxxx
  b.使用^符号 —— 只能后退
  	git reset --hard HEAD^^^
	一个^符号表示后退一步，n个^表示后退n步
  c.使用~符号
  	git reset --hard HEAD~5
	~后面的数字，表示后退步数，上面的优化版

  删除文件并找回
  	前提：删除前，文件存在时的状态已经被提交到本地库
  	操作：git reset --hard [已经存在的指针处]
  
  文件比较：
  	git diff [文件名]   			//将工作区和暂存区的文件进行比较
	git diff [本地库中历史版本] [文件名]	//将工作区和本地库历史记录进行比较
	不带文件名可以比较库中的所有文件

10.分支操作
  创建分支：
	git branch [分支名]
  查看分支：
  	git branch -v
  切换分支：
  	git checkout [分支名]
  合并分支：
  	第一步：切换到接受修改的分支上（被合并，需要增加新内容的老分支）
		git checkout [分支名]
		git checkout master   //切换到主分支，准备添加版本1的内容
	第二步：执行 merge 命令
		git merge [分支名] （做出修改的新分支）
		git merge banben1     //将版本1的内容加入到 master 分支

----------------------------------------------------------

git 命令：

状态：git status                                       //查看工作区、暂存区状态

添加：git add [filename]			       //将工作区的“新建/修改”添加到暂存区

提交：git commit -m "commit message" [filename]	       //将暂存区的内容提交到本地库

日志：git log					       //查看提交日志
      多屏显示控制方式：空格 向下翻页； b 向上翻页； q 退出。
      git log --pretty=oneline    	//简洁显示日志
      git log --oneline			//简洁显示日志（简洁的哈希值）
      git reflog			//oneline版本增加了移动版本需要的步数

版本切换：git reset --hard [局部哈希值]  或者
	  git reset --hard HEAD^^^	 或者
	  git reset --hard HEAD~2

比较：git diff [文件名]
      git diff [某个历史版本] [文件名]
      git diff HEAD~2 filename 
