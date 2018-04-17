一、创建版本库。
1. git init
把当前目录变成git可以管理的仓库

2. git add XXX.txt
把XXX.txt添加到暂存区里面去
3. git commit -m "msg"
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
1. git checkout -- XXX.txt
情况一：add到暂存区 - commit - 修改了 - "撤销修改" - 丢弃工作区的修改，回到和版本库一样的状态（修改之前的状态）
情况二：add到暂存区 - 修改了 - "撤销修改" - 回到添加暂存区后的状态（修改之前的状态）

2. rm XXX.txt + git commit -m "msg"
删除文件并从版本库中删除。

四、远程仓库GitHub
1. 创建SSH Key
1.1. 在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果有的话，直接跳过此如下命令，如果没有的话，打开命令行，输入如下命令：
ssh-keygen  -t rsa –C “youremail@example.com”
1.2. id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

2. 登录github,打开”settings”中的SSH Keys页面，然后点击“Add SSH Key”,填上任意title，在Key文本框里黏贴id_rsa.pub文件的内容。

3. 如何添加远程库？
登录github上，然后在右上角找到“create a new repo”创建一个新的仓库。

4. 根据提示和需求，进行需要的操作



续

假设需求：我们已经在本地创建了一个Git仓库后，又想在github创建一个Git仓库，并且希望这两个仓库进行远程同步，这样github的仓库可以作为备份，又可以其他人通过该仓库来协作。
操作如下：1. 创建新的仓库 2. 在本地的testgit仓库下运行命令：git remote add origin https://github.com/XXX/YYY.git + git push -u origin master
注意：
* 使用 git push 命令，实际上是把当前分支master推送到远程，把本地库的内容推送到远程。
* 由于远程库是空的，第一次推送master分支时，加上了 –u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
** 从现在起，只要本地作了提交，就可以通过如下命令：git push origin master；即可把本地master分支的最新修改推送到github上了。

五、克隆远程仓库
1. git clone https://github.com/leeJiahuan/testGit2.git

六、创建与合并分支
注意：HEAD指向的就是当前分支；master才是指向提交。
1. 查看分支：git branch
* 会列出所有的分支，当前分支前面会添加一个星号
2. 创建分支：git branch branchname
3. 切换分支：git checkout branchname
4. 创建并切换分支：git checkout -b branchname
相当于两条命令：git branch branchname + git checkout branchname
5. 合并指定分支到当前分支上：git merge otherbranchname
* 通常合并分支时，git一般使用”Fast forward”模式，在这种模式下，删除分支后，会丢掉分支信息；
* 使用 git merge --no-ff  -m "注释" otherbranchname，表示禁用fast forward模式。
6. 删除分支：git branch -d branchname

七、隐藏当前工作现场
假设场景：master 主分支；dev 当前正在进行开发的分支（未add到暂存区）；bugline 从master开的用于修复紧急bug的临时分支

1. 在当前工作分支下将当前的工作现场隐藏起来：(dev)使用命令git stash。
2. 切换到master分支：(dev)使用命令git checkout master
3. 创建并切换至一个临时分支：(master)使用命令git checkout -b bugline
4. 修复bug
5. add 到暂存区 并 commit：(bugline)使用命令git add XXX.txt + git commit -m "msg"
6. 修复完成后，切换到主分支上，并完成合并：(bugline)git checkout master + (master)git merge --no-ff -m "msg" bugline
7. 删除临时分支：(master)使用命令git branch -d bugline
8. 返回工作分支：(master)使用命令git checkout dev
* 注意：此时查看工作区是干净的：(dev)使用命令git status
9. 查看所有被隐藏的文件列表：(dev)使用命令git stash list
10.恢复工作现场：
10.1. 使用命令 git stash apply 恢复：恢复后，stash内容并不删除，你需要使用命令git stash drop来删除。
10.2. 使用命令 git stash pop 恢复：恢复的同时把stash内容也删除了。

八、多人协作
查看远程库的信息：使用 git remote
查看远程库的详细信息：使用 git remote –v

多人协作工作模式一般是这样的：
1. 首先，可以试图用git push origin branch-name推送自己的修改；
2. 如果推送失败，则因为远程分支比你的本地更新早，需要先用git pull试图合并；
3. 如果合并有冲突，则需要解决冲突，并在本地提交。再用git push origin branch-name推送。

（一）推送分支
* 推送分支就是把该分支上所有本地提交到远程库中；推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上。
* 使用命令 git push origin branchname

* 一般情况下，那些分支要推送呢？
** master分支是主分支，因此要时刻与远程同步。
** 一些修复bug分支不需要推送到远程去，可以先合并到主分支上，然后把主分支master推送到远程去即可。


（二）拉取分支
* 拉取分支就是把远程的origin的dev分支拉到本地来。
* 使用命令创建本地dev分支：git checkout  –b dev origin/dev


