一、创建版本库。
1. git init
把当前目录变成git可以管理的仓库

2. git add XXX.txt
把XXX.txt添加到暂存区里面去
3. git commit -m "xxx"
告诉git，把文件提交到仓库

4. git status
查看是否还有文件未提交
5. git diff XXX.txt
查看XXX.txt文件改动了什么内容但未被提交

二、版本回退
1. git log / git log --pretty=oneline
查看历史记录

2. 回退到上N个版本
git reset --hard HEAD^：N个版本就N个^
git reset --hard HEAD~1：N个版本就把"1"换成"N"

3. 回退到指定版本号的版本
git reset --hard 版本号
4. git reflog
获取每次提交的版本号

三、撤销修改和删除文件操作



