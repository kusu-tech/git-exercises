
## Git分支
1. **分支管理**
- git branch
  - git branch 创建分支
  - git branch -d 删除分支
  - git branch 查看全部分支，*标注的是当前分支
  - git branch -v 查看全部分支最后一次提交的对象及提交的备注
  - git branch --merged 查看已经合并到当前分支的分支
  - git branch --no-merged 查看未合并到当前分支的分支
2. **切换分支**
- git checkout 
3. **合并分支**
- git merge
  - 快进合并。
  - 三方合并。三方合并有可能产生冲突，该冲突是在多次提交中同时修改了同一个文件产生的。产生冲突之后，git会提示合并不成功，并用特定方式标记出冲突的位置，可以手动修改冲突，然后用git add的方式解决冲突。
4.**变基**
- git rabase 
- 变基是合并的另一种方式。它的逻辑是找到当前分支指向的快照与需要合并的分支指向的快照的祖先，然后对比当前分支相对于组件的历次提交，抽取出不一样的地方形成一个临时的文件，并指向需要合并的分支，然后用“快进”的方式进行合并。该种方式避免了三方合并冲突。

*tips:git log 遇上end 按q可退出命令*

## Git标签
1. **附注标签**
- git tag -a tagName -m "tagContent" 
- tag不需要commit，直接给当前快照添加tag
2. **轻量标签**
- git tag tagName 
3. **给已形成的快照打标签**
- git tag -a tagName objectHash 
4. **删除标签**
- git tag -d tagName 
- 该命令不会删除远程标签
5. **推送某个标签到远程服务器**
- git push origin tagName 
6. **删除远程某个标签**
- git push origin --delete tagName 
7. **切换到某标签标记的快照**
- git checkout tagName 
- 在没有分支指向的标签标记的快照中修改了内容并提交，该快照将不属于任意一个分支且找无法访问，因此建议需要更改内容时，可先建立一个分支
8. **查看标签列表**
- git tag -l 

## Git贮藏
1. **将当前工作区的内容暂存**
- git stash 
  - 此时使用git status可查看到状态是干净的
  - 切换到另外分支中，应用贮藏内容可能会产生冲突，此时需要解决冲突才能切换分支
2. **查看全部贮藏列表**
- git stash list 
3. **应用贮藏列表中的记录**
- git stash apply 应用贮藏列表中最近保存的那一次记录
- git stash apply stash@{num} 选择应用某一次贮藏记录
4. **删除记录**
- git stash drop 删除最近保存的那一次记录
- git stash drop stash@{num} 选择删除某一次贮藏记录
5.  **清空贮藏**
- git stash clear

## Git远程仓库
1. **查看远程仓库**
- git remote
  -  origin是git给克隆仓库的默认名字
  -  git remote -v 查看远程仓库保存对应的简写和URL，如果有多个远程仓库则会列出多组信息
  -  git remote show <remote> 列出某个远程仓库的信息，包括当前处于的分支，所有分支、执行git pull命令将会拉取哪些信息，执行git push命令将会推送哪些信息
2. **添加远程仓库**
- git clone <url>
3. **从远程仓库抓取**
- git fetch 从远程仓库抓取信息，只会抓取新的内容，并不会与本地工作区合并
- git pull 从远程抓取信息并与本地工作区合并
4. **推送到远程服务器**
- git push 
    1. 需要获得写入权限
    2. 之前有人写入需要先拉取合并再推送
5. **修改远程仓库的简写名**
- git remote rename <oldName> <newName>
6. **移除某个远程仓库**
- git remote remove
