[练习教程网站][https://www.liaoxuefeng.com/wiki/896043488029600]

[toc]

## 基础git操作



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
git add git练习记录.md #添加文件到暂存区 
```

`git add .`添加所有修改的文件到暂存区

```
git add .
```

`git commit`命令，`-m`后面输入的是本次提交的说明

```git
git commit -m "提交git练习记录文件"
```

```git
git push -u origin master #提交到远程仓库
```

使用命令`git push -u origin master`第一次推送master分支的所有内容；

此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；

```
git push origin master
```



这里是一个PR  

GitHub PR 

多人协作练习

使用`git pull` 命令拉取远程仓库的代码

```git
git pull
```

## git本地仓库练习

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

#### 小结

现在总结一下：

- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

使用git log 查看历史后，输入 `q`返回git命令行，就可以继续练习git命令了

### 工作区和暂存区

隐藏目录`.git`，这个不算工作区，而是Git的版本库。

![git-repo](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

们把文件往Git版本库里添加的时候，是分两步执行的：

第一步是用`git add`把文件添加进去，实际上就是把文件修改添加到暂存区；

第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。

我们创建Git版本库时，Git自动为我们创建了唯一一个`master`分支，所以，现在，`git commit`就是往`master`分支上提交更改。

你可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

### 管理修改

用`git diff HEAD -- readme.txt`命令可以查看工作区和版本库里面最新版本的区别

```git
$ git diff HEAD -- readme.txt
diff --git a/readme.txt b/readme.txt
index edff317..e4b910f 100644
--- a/readme.txt
+++ b/readme.txt
@@ -2,4 +2,4 @@
 Git is a distributed version control system
 Git is a free software distributed under the GPL
 Git has a mutable index called stage
-Git tracks changes
\ No newline at end of file
+Git tracks changes of files
\ No newline at end of file

```

### 删除文件

通常直接在文件管理器中把没用的文件删了，或者用`rm`命令删了：

这个时候，Git知道你删除了文件，因此，工作区和版本库就不一致了，`git status`命令会立刻告诉你哪些文件被删除了：

现在你有两个选择，一是确实要从版本库中删除该文件，那就用命令`git rm`删掉，并且`git commit`：

文件就从版本库中被删除了。

> 小提示：先手动删除文件，然后使用git rm <file>和git add<file>效果是一样的。

另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：

```git
git checkout -- test.txt
```

> 注意：从来没有被添加到版本库就被删除的文件，是无法恢复的！

命令`git rm`用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失**最近一次提交后你修改的内容**。

## 远程仓库

###　添加远程仓库

把本地库的内容推送到远程，用`git push`命令，实际上是把当前分支`master`推送到远程。

新建远程库是空的，我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。

#### SSH警告

当你第一次使用Git的`clone`或者`push`命令连接GitHub时，会得到一个警告：

```
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
RSA key fingerprint is xx.xx.xx.xx.xx.
Are you sure you want to continue connecting (yes/no)?
```

这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入`yes`回车即可。

Git会输出一个警告，告诉你已经把GitHub的Key添加到本机的一个信任列表里了：

```
Warning: Permanently added 'github.com' (RSA) to the list of known hosts.
```

这个警告只会出现一次，后面的操作就不会有任何警告了。

#### 小结

要关联一个远程库，使用命令

```
git remote add origin git@server-name:path/repo-name.git
```

关联一个远程库时必须给远程库指定一个名字，`origin`是默认习惯命名；

关联后，使用命令`git push -u origin master`第一次推送master分支的所有内容；

此后，每次本地提交后，只要有必要，就可以使用命令`git push origin master`推送最新修改；

第一次推送

```
git push -u origin master
```

n+1(n>=0)次推送

```
git push origin master
```

#### 从远程库克隆

使用`git clone`克隆仓库

```
git clone git@github.com:michaelliao/gitskills.git
```

