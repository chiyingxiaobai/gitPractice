<!--
 * @Author: InsHomePgup
 * @Date: 2022-05-20 09:56:16
 * @LastEditors: InsHomePgup
 * @LastEditTime: 2022-05-20 10:07:27
 * @FilePath: \sport-planingc:\Users\Abraham\my_space\code\git\git1\reset的使用.md
 * @Description:
 *
 *
-->

> 回退到上一个版本

```
git reset --hard HEAD^

后面的 ^ 表示回退一个版本，如果需要回退两个版本则就是   ^^
```

> 回退到指定版本，跳转到指定版本

```
git reset --hard commitId

git reset --hard 992f81d

commitId 就是log 日志里面开头那串字母
```

> 误操作以后怎么回到最新版本？

```
git reflog   Manage reflog information 可以找到旧的commit信息
```
