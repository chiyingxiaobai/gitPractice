练习fetch 以后merge

首先我完成提交

get fetch origin master:temp

git diff temp

git merge temp

这里造成冲突
<<<<<<< HEAD
测试有冲突的fetch
测试有冲突的fetch]
合并冲突
来点不一样的

=======
测试有冲突的fetch]
合并冲突

来点不一样的
>>>>>>> 3b3fd55a1e705c9587e66208ae022ea5cac1b449
