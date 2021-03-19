# config文件介绍
## remote
- 在config中生成配置文件 
>>$ git remote add origin 地址

指定远程版本库的名称（origin）、URL 和一个用于获取操作的 引用规范（refspec）

>>url=远程仓库地址
>>fetch = +refs/heads/*:refs/remotes/origin/*

引用规范的格式由一个可选的 + 号和紧随其后的 <src>:<dst> 组成， 其中 <src> 是一个模式（pattern），代表远程版本库中的引用； <dst> 是本地跟踪的远程引用的位置。 + 号告诉 Git 即使在不能快进的情况下也要（强制）更新引用。

- 只获取远程master分支，而非所有分支，Git 获取服务器中 refs/heads/ 下面的所有引用，并将它写入到本地的 refs/remotes/origin/ 中：
>>fetch = +refs/heads/master:refs/remotes/origin/master
- 可以在配置文件中指定多个用于获取操作的引用规范
- 不能在模式中使用部分通配符，以下是不规范的例子：
>>fetch = +refs/heads/qa*:refs/remotes/origin/qa*

### 推送
- 推送指定分支到远程服务器的指定分支：
>>$ git push origin master:refs/heads/qa/master

- 每次都按照指定的推送方式推送，可以在config文件中配置一项push
- 删除远程服务器的某分支：
>>$ git push origin :topic

>>$ git push origin --delete topic

## core
- core.repositoryFormatVersion 内部变量，用于标识存储库格式和布局版本。
- core.fileMode告诉Git是否尊重工作树中的可执行文件。

当签出标记为可执行文件的文件或签出可执行文件位的非可执行文件时，某些文件系统会丢失可执行文件位。 git-clone或git-init探测文件系统以查看其是否正确处理了可执行位，并根据需要自动设置了此变量。

但是，存储库可能位于正确处理文件模式的文件系统上，并且 在创建该变量时将其设置为true，但是以后可以从丢失文件模式的另一个环境中进行访问（例如，通过CIFS挂载导出ext4，访问Cygwin使用Windows或Eclipse的Git创建存储库）。在这种情况下，可能有必要将此变量设置为false。参见git-update-index。

默认值为true（在配置文件中未指定core.filemode时）。

- core.bare 
  If true this repository is assumed to be bare and has no working directory associated with it. If this is the case a number of commands that require a working directory will be disabled, such as git-add or git-merge.

This setting is automatically guessed by git-clone or git-init when the repository was created. By default a repository that ends in "/.git" is assumed to be not bare (bare = false), while all other repositories are assumed to be bare (bare = true).

- core.logallrefupdates
启用引用日志 Enable the reflog. Updates to a ref <ref> is logged to the file "$GIT_DIR/logs/<ref>", by appending the new and old SHA-1, the date/time and the reason of the update, but only when the file exists. If this configuration variable is set to true, missing "$GIT_DIR/logs/<ref>" file is automatically created for branch heads (i.e. under refs/heads/), remote refs (i.e. under refs/remotes/), note refs (i.e. under refs/notes/), and the symbolic ref HEAD. If it is set to always, then a missing reflog is automatically created for any ref under refs/.

This information can be used to determine what commit was the tip of a branch "2 days ago".

This value is true by default in a repository that has a working directory associated with it, and false by default in a bare repository

- core.symlinks
If false, symbolic links are checked out as small plain files that contain the link text. git-update-index and git-add will not change the recorded type to regular file. Useful on filesystems like FAT that do not support symbolic links.

The default is true, except git-clone or git-init will probe and set core.symlinks false if appropriate when the repository is created.

- core.ignoreCase
内部变量，它使各种变通办法可以使Git在不区分大小写的文件系统上更好地工作。例如，如果目录列表在Git期望“ Makefile”时找到了“ makefile”，则Git将假定它确实是同一文件，并继续将其记住为“ Makefile”。
缺少设置则设置为false，在git clone 或者git init 创建的库，则设置为true
  