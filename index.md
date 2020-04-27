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

ss
