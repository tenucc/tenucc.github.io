<h2>Hello World!</h2>

<h2>Hi this is tenu</h2>
<h2>and I am learning</h2>
<h2>natural language processing</h2>

  <h1>Learning Git via 廖雪峰のblog</h1>
  
<h2>Git是用C语言开发的</h2>
  <h2>CVS及SVN都是集中式的版本控制系统，而Git是分布式版本控制系统</h2>
  
  <h1>在Mac OS X上安装Git</h1>
  
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

创建版本库

```
mkdir learngit
cd learngit
git init
```

显示隐藏的.git目录
```
ls -ah
```

在ui界面编写一个readme.txt
```
Git is a version control system.
Git is free software.
```




用命令git add告诉Git，把文件添加到仓库：

`$ git add readme.txt`


用命令git commit告诉Git，把文件提交到仓库：

`$ git commit -m "wrote a readme file"`

commit可以一次提交很多文件，所以你可以多次add不同的文件，比如：

```
$ git add file1.txt
$ git add file2.txt file3.txt
$ git commit -m "add 3 files."
```

git status命令可以让我们时刻掌握仓库当前的状态

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```


git diff顾名思义就是查看difference，显示的格式正是Unix通用的diff格式
```
$ git diff readme.txt 
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```


git log命令显示从最近到最远的提交日志

`$ git log`
或者
`$ git reflog`

把当前版本回退到上一个版本，就可以使用git reset命令

`$ git reset --hard HEAD^ `

查看文本内容

`$ cat readme.txt`

指定回到未来的某个版本($git log 获得commend id)

`$ git reset --hard 1094a`

<h2>工作区和暂存区/版本库</h2>

```
$ git status
$ git add LICENSE readme.txt DS_Store
$ git command -m "understand how stage works"
$ git status
On branch master
nothing to commit, working tree clean
```

<h2>管理修改、撤销修改、删除文件</h2>
工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。
`$ git ls -ah`
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。
把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。

你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

我们再练习一遍，先对readme.txt做个修改，比如加上一行内容
然后，在工作区新增一个LICENSE文本文件（内容随便写）
git status 查看一下状态

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	LICENSE

no changes added to commit (use "git add" and/or "git commit -a")
```

Git非常清楚地告诉我们，readme.txt被修改了，而LICENSE还从来没有被添加过，所以它的状态是Untracked。

现在，使用两次命令git add，把readme.txt和LICENSE都添加后，用git status再查看一下：

```
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   LICENSE
	modified:   readme.txt	
```

所以，git add命令实际上就是把要提交的所有修改放到暂存区（Stage），然后，执行git commit就可以一次性把暂存区的所有修改提交到分支。

```
$ git commit -m "understand how stage works"
[master e43a48b] understand how stage works
 2 files changed, 2 insertions(+)
 create mode 100644 LICENSE
```

一旦提交后，如果你又没有对工作区做任何修改，那么工作区就是“干净”的：
(实际操作中还需要
```git add .DS_Store LICENSE.txt readme.txt
git commit -m "understand how stage works"
```
工作区和暂存区stage才是干净的)
工作区和版本库：版本库分为stage和master，stage又称暂存区。
```
$ git status
On branch master
nothing to commit, working tree clean
```

一旦提交后，如果你又没有对工作区做任何修改，那么工作区就是“干净”的：

```
$ git status
On branch master
nothing to commit, working tree clean
```

评论区有点东西


```
工作区>>>>暂存区>>>>仓库和操作指令
九只蜗牛Leo created at December 2, 2019 11:10 AM, Last updated at February 11, 2020 5:05 PM
感觉大家把简单问题复杂化了，看着头晕，

Git管理的文件分为：工作区，版本库，版本库又分为暂存区stage和暂存区分支master(仓库)

工作区>>>>暂存区>>>>仓库

git add把文件从工作区>>>>暂存区，git commit把文件从暂存区>>>>仓库，

git diff查看工作区和暂存区差异，

git diff --cached查看暂存区和仓库差异，

git diff HEAD 查看工作区和仓库的差异，

git add的反向命令git checkout，撤销工作区修改，即把暂存区最新版本转移到工作区，

git commit的反向命令git reset HEAD，就是把仓库最新版本转移到暂存区。
```

Git管理的是修改，当你用git add命令后，在工作区的第一次修改被放入暂存区，准备提交，但是，在工作区的第二次修改并没有放入暂存区，所以，git commit只负责把暂存区的修改提交了，也就是第一次的修改被提交了，第二次的修改不会被提交。

提交后，用git diff HEAD -- readme.txt命令可以查看工作区和版本库里面最新版本的区别：

```
$ git diff HEAD -- readme.txt 
diff --git a/readme.txt b/readme.txt
index 76d770f..a9c5755 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,4 +1,4 @@
 Git is a distributed version control system.
 Git is free software distributed under the GPL.
 Git has a mutable index called stage.
-Git tracks changes.
+Git tracks changes of files.
```
