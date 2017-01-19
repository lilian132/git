# Git

## 配置

安装 Git 之后，你要做的第一件事情就是去配置你的名字和邮箱，因为每一次提交都需要这些信息

```
git config --global user.name "bukas"
git config --global user.email "bukas@gmail.com"
```

获取Git配置信息，执行以下命令

```
git config --list
```

## Git GUI

Git GUI是git封装了命令行的图形用户界面工具，下载安装之后可以结合Git Shell一起使用

## 创建仓库

```
mkdir mygit //创建mygit目录
cd mygit	//进入目录
git init	//初始化仓库
```

通过git init命令将生成一个隐藏的.git目录，该目录文件承担了版本控制的功能

## commit文件

```
touch readme.md		//生成md文件
git add readme.md	//添加md文件到版本库
git commit -m "wrote a readme file" //提交文件，-m后面输入的是本次提交的说明
```

一次可以`add`多个不同的文件，以空格分隔：

```
git add a.txt b.txt c.txt
```

## 仓库状态

```
git status
```

`git status`命令可以让我们时刻掌握仓库当前的状态。

<img src="img/1.png"/>

查看具体修改内容

```
git diff readme.md
```

## 版本日志和回退

### 基本日志

首先可以查看git日志文件：

```
git log
```

<img src="img/log.png">

这里显示了所有commit的ID、提交人、提交时间、提交信息；`git log`命令显示从最近到最远的提交日志。如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数：

```
git log --pretty=oneline
```

### 完全日志

git reflog 可以查看所有分支的所有操作记录（包括（包括commit和reset的操作），包括已经被删除的commit记录，git log则不能察看已经删除了的commit记录

```
git reflog
```

比较区别：

<img src="img/reflog.png">





### 版本回退

在 Git中，用`HEAD`表示当前版本，也就是最新的提交`commit id`，上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个^比较容易数不过来，所以写成`HEAD~100`。

现在我们要把当前版本回退到上一个版本，就可以使用`git reset`命令：

```
git reset --hard HEAD^
```

或者直接指定reset到具体某一个版本，以前的版本id可以通过`git reflog`查看

```
git reset --hard 2e70fdf //版本号写前几位即可
```

