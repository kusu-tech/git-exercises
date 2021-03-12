# Git Exercises

## Preparations

- Install [Windows Terminal](https://github.com/microsoft/terminal/releases) | [官方文档](https://docs.microsoft.com/zh-cn/windows/terminal/)
- Install [PowerShell](https://github.com/PowerShell/PowerShell/releases) | [官方文档](https://docs.microsoft.com/zh-cn/powershell/)
- Install [Git](https://git-scm.com/downloads) | [官方文档](https://git-scm.com/doc)
- [Windows Terminal Themes](https://windowsterminalthemes.dev/)

## Round 01  常用命令

### PowerShell

- [ ] `set-location/sl/cd` 进入指定目录
- [ ] `mkdir/md` 新建目录
- [ ] `new-item/ni` 新建文件
- [ ] `ls/dir` 查看当前目录内容
- [ ] `add-content/ac` 向文件写入内容
- [ ] `set-content/sc` 向文件写入内容替换原内容
- [ ] `cat/more` 查看文件内容
- [ ] `remove-item/rm/ri/del` 删除文件或目录
- [ ] `rename-item/ren` 重命名文件或目录
- [ ] `move-item/mi/move` 移动文件或目录
- [ ] `copy-item/cp/copy` 复制文件或目录
- [ ] `clear-host/cls/clear` 清屏
- [ ] `get-command/gcm` 列出所有命令
- [ ] `get-help` 查找某一命令具体用法

----

### 基础设置

- [ ] `git config --global user.name "[your-name]"` 设置提交者姓名
- [ ] `git config --global user.email "[your-email-address]"` 设置提交者邮箱地址

----

### 工作区-暂存区-本地仓库 基本操作

- [ ] `git status` 检查文件状态
- [ ] `git init` 在当前目录下初始化 Git 仓库
- [ ] `git add [file/dir]` 追踪文件和目录
- [ ] `git restore` 撤销修改
- [ ] `git checkout [file/dir]` 从暂存区更新文件或目录到工作区
- [ ] `git diff` 查看尚未暂存的改动
- [ ] `git commit` 提交暂存区文件
- [ ] `git diff [commit]` 查看工作区与某一提交之间的差异
- [ ] `git rm [file]` 从工作区和暂存区删除某个文件
- [ ] `git rm --cached [file]` 将仓库中的某个文件删除（同时从暂存区移除），但保留在工作区
- [ ] `git log` 查看提交历史
- [ ] `git log --follow [file]` 查看指定文件的版本历史，包括重命名
- [ ] `git show [commit]` 查看指定提交的元数据和内容变化
- [ ] `git mv [file-from] [file-to]` 对文件重命名
- [ ] `git diff --cached` 查看已提交和暂存区的变化

----

### 标签

- [ ] `git tag` 列出已有标签
- [ ] `git tag --list "[tag-name*]"` 列出匹配通配符的标签
- [ ] `git tag -a [tag-name] -m "[tag-msg]"` 创建标签
- [ ] `git tag -a [tag-name] [commit]` 给某个提交打标签
- [ ] `git push origin [tag-name]` 推送某个标签到远程仓库
- [ ] `git push origin --tags` 把所有不在远程服务器的标签推送到远程服务器
- [ ] `git tag -d [tag-name]` 删除标签
- [ ] `git push origin --delete [tag-name]` 删除远程标签

----

### 分支

- [ ] `git branch [branch-name]` 创建一个新分支
- [ ] `git checkout [branch-name]` 切换到指定分支并更新工作目录
- [ ] `git checkout -b [branch-name]` 创建一个新分支并切换到这个新分支上
- [ ] `git merge [branch-name]` 将指定分支的历史合并到当前分支
- [ ] `git diff [branchA] [branchB]` 查看两个分支之间的差异
- [ ] `git branch -d [branch-name]` 删除指定分支

----

### 远程

- [ ] `git clone [repo-url]` 完整下载指定的仓库，并在工作区迁出 master 分支的 HEAD 版本
- [ ] `git fetch` 下载远端跟踪分支的所有历史
- [ ] `git push` 从本地提交推送分支改变到远程
- [ ] `git pull` 从远程版本库取得修改到当前分支

----

### 临时存档库

- [ ] `git stash push [msg]` 保存当前修改到新的存档
- [ ] `git stash pop [stash-name]` 从某个存档中将改变应用到工作区，然后从存档库丢弃它，默认最近存档
- [ ] `git stash apply [stash-name]` 从某个存档中将改变应用到工作区，默认最近存档
- [ ] `git stash list` 显示当前所有存档
- [ ] `git stash show [stash-name]` 显示存档中记录的改动，对比存档生成时的原来状态，默认最近存档
- [ ] `git stash drop [stash-name]` 从存储区中删除指定存档，默认最近存档
- [ ] `git stash clear` 清空存档库,此操作不可恢复

## Round 02

- [ ] 根据实际文档撰写和协作需求，模拟操作流程，并用命令行的方式完成实例模拟
