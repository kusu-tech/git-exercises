## 引用

- 引用的作用是记录一系列提交对象。git初始化后在ref文件夹中自动生成head和tag两个空文件夹。
- 当在git中进行了第一次commit以后，在**head文件夹**中自动生成了默认的引用-master文件，master同时也是主分支的名字。在master文件中保存了一系列在该分支中commit的提交对象的SHA-1值。当创建了其他分支也是同理。使用``git log <branch>``可以查看到在某分支中提交的所有SHA-1值。
- ref文件夹中的**tag文件夹**中保存了被创建的所有标签。给某一个提交对象打标签的同时，tag文件夹中也会对应生成一个tagName的文件，该文件保存着该对象的SHA-1值。与head文件中保存内容的区别是，tag文件中保存的SHA-1值是一个，而head文件中保存的是一系列提交的SHA-1值。使用``git log <tagName>``可以查看到某标签对应的SHA-1值。
- **remotes远程引用**，当在本地添加了某一个远程应用且向远程服务器推送了提交时会记录一个SHA-1值，这个值只是为了记录一个与远程联系的状态，所以记录的是最后一次与远程服务器交互的SHA-1值
- **HEAD是指向引用的指针**，当执行``git checkout <branch>``命令时，HEAD从当前引用指向切换的引用。
- ``git checkout``命令可用于切换任意一种类型的引用：
  - 执行``branch``时，切换到指定分支最后一次commit的SHA-1值
  - 执行``tagName``时，切换到指定tag指向的SHA-1值，如果切换到tag没有任何分支指向，修改内容并提交将找不到该SHA-1值，这是由于tag区别于branch，它指向唯一SHA-1值，而branch指向一系列SHA-1值
  - 执行``remotes``时，只能只读最后一次向远程提交的对象，而HAED并不会真的指向该切换

## 引用规范

- 引用规范用于本地映射远程仓库的场景
- 引用规范是一行配置代码，用于指定拉取/推送远程仓库的某个引用，以及远程引用将放在本地的位置：

   - ``[remote"origin"] ``
   - ``url="远程地址"``
   - ``fetch=+refs/head/*:refs/remotes/origin/*`` 其中"+"是要求拉取的时候强制快进（即便有冲突也要强行合并）;``<scr>:<dst>``=远程引用:本地跟踪远程引用的位置
   - 指定远程引用：``fetch=+refs/head/branchName1:refs/remotes/origin/branchName2 其中branchName1指的是远程以存在的某个分支，branchName2可以等branchName1，意味着本地建立一个同样名字的文件用于跟踪branchName1远程引用。但当branchName2≠branchName1时，意味着将branchName1远程引用拉取至本地已有的branchName2分支中。
   - 引用规范可以配置多个，例如指定拉取远程了某两个分支
   - 推送本地引用至远程仓库 ``push=refs/head/branchName1:refs/head/branchName2 本地引用分支:远程引用
   - 删除引用 
     - ``git push origin :branchName`` 将``<src>``留空
     - ``git push prigin --delete branchName``


