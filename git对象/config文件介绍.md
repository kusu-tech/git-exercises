#config文件介绍
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

###推送
- 推送指定分支到远程服务器的指定分支：
>>$ git push origin master:refs/heads/qa/master

- 每次都按照指定的推送方式推送，可以在config文件中配置一项push
- 删除远程服务器的某分支：
>>$ git push origin :topic

>>$ git push origin --delete topic