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

<h2>工作区和暂存区</h2>
```
$ git status
$ git add LICENSE readme.txt DS_Store
$ git command -m "understand how stage works"
$ git status
On branch master
nothing to commit, working tree clean
```
