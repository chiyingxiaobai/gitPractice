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
Git is free software distributed under the GPL.
```

`git status`命令可以让我们时刻掌握仓库当前的状态

`git diff`查看修改，查看difference，显示的格式正是Unix通用的diff格式，可以从上面的命令输出看到，我们在第一行添加了一个`distributed`单词。

`git log`命令显示从最近到最远的提交日志，我们可以看到3次提交

如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数：

```git
$ git log --pretty=oneline
1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master) append GPL
e475afc93c209a690c39c13a46716e8fa000c366 add distributed
eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0 wrote a readme file
```

在Git中，用`HEAD`表示当前版本，也就是最新的提交`1094adb...`（注意我的提交ID和你的肯定不一样），上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。

使用`git reset`命令回退到上一个版本

```git
$ git reset --hard HEAD^
HEAD is now at e475afc add distributed
```

找到指定版本的`commit id`,可以指定回到未来的某个版本

```git
$ git reset --hard 1094a
HEAD is now at 83b0afe append GPL
```

### 小结

现在总结一下：

- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

使用git log 查看历史后，输入 `q`返回git命令行，就可以继续练习git命令了

