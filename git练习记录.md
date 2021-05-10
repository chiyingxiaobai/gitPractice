[练习教程网站][https://www.liaoxuefeng.com/wiki/896043488029600]

```git
git init  初始化
```

将本地仓库与远程仓库gitPractice关联

```git
git remote add origin git@github.com:chiyingxiaobai/gitPractice.git
```

如果添加的时候地址写错了，或者就是想删除远程库，可以用`git remote rm <name>`命令。使用前，建议先用`git remote -v`查看远程库信息：

```git
$ git remote -v
origin  git@github.com:michaelliao/learn-git.git (fetch)
origin  git@github.com:michaelliao/learn-git.git (push)
```

然后，根据名字删除，比如删除`origin`：

```git
$ git remote rm origin
```

```git
git add git练习记录.md #添加文件到仓库 
```

`git commit`命令，`-m`后面输入的是本次提交的说明

```git
git commit -m "提交git练习记录文件"
```

```git
git push -u origin master #提交到远程仓库
```



这里是一个PR  

GitHub PR 

多人协作练习

使用`git pull` 命令拉取远程仓库的代码

```git
git pull
```

### 版本回退练习

2 

```
Git is a distributed version control system.
Git is free software
```

`git status`命令可以让我们时刻掌握仓库当前的状态

`git diff`查看修改，查看difference，显示的格式正是Unix通用的diff格式，可以从上面的命令输出看到，我们在第一行添加了一个`distributed`单词。

