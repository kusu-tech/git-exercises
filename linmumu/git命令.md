### git说明

**1、git基础篇**

- git init 初始化git仓库
- git clone `<url>`  克隆现有仓库，下载一个项目和它的整个代码历史
- git status 检查当前文件状态
- git add [file1] [file2] 跟踪新文件,将指定文件添加到缓存区
- git add [dir] 添加指定目录到缓存区，包括子目录
- git add . 添加当前目录的所有文件到暂存区
- git commit 将暂存区的内容提交到仓库区

**2、git分支**

- git branch 查看列出所有本地分支
- git branch -r 查看列出所有远程分支
- git branch -a 查看列出所有本地分支和远程分支
- git branch -b [branch] 新建一个分支，并切换到该分支
- git branch -v 查看列出本地的所有分支并显示最后一次提交，当前所在分支
- git merge [branch] 合并指定分支到当前分支
- git checkou - 切换到上一个分支
- git branch -d [branch-name] 删除分支
- git push origin --delete [branch-name] 删除远程分支

**3、查看信息**

- git status 显示有变更的文件
- git log 显示当前分支的版本历史
- git log --stat 显示commit历史，以及每次commit发生变更的文件
- git diff 显示暂存区和工作区的差异
- git reflog 显示当前分支的最近几次提交

**4、远程同步**

- git remote 列出已经存在的远程仓库
- git remote -v 显示所有远程仓库和对应的地址
- git remote show 显示某个远程仓库的信息
- git clone 添加远程仓库
- git fetch 下载远程仓库的所有变动，只是下载新的变动，不会影响本地工作区
- git pull 取回远程仓库的变化，并与本地分支合并
- git push [remote] [branch] 传本地指定分支到远程仓库（如果远程有人更新，就必须先拉取合并了再进行推送）

**5、标签（tag）**

- git tag 打印所有的标签
- git tag [tag] [commit] 新建一个tag在指定的commit上
- git tag -d [tag] 删除本地标签
- git show [tag] 查看标签信息