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
  
