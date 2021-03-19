## git生成的文件结构与内容

**当我们克隆(git clone)或者新建(git init)一个git仓库时，git会帮我们在当前文件夹下自动生成 .git 文件夹(即git本地版本仓库)。**

### 初始化后的文件结构：

- [ ] `.git` 进入.git目录
- [ ] `hooks`文件夹
- [ ] `info`文件夹
- [ ] `objects`文件夹
- [ ] `refs`文件夹
- [ ] `config`
- [ ] `description`
- [ ] `HEAD`

### 新增文件add之后的结构变化：

- [ ] `.git` 进入.git目录
- [ ] `hooks`文件夹
- [ ] `info`文件夹
- [ ] `objects`文件夹
- [ ] `refs`文件夹
- [ ] `config`
- [ ] `description`
- [ ] `HEAD`
- [ ] `index`  add后的新增文件

**1. hooks文件夹**

`hooks(钩子)`文件夹中共存放了13个示例都是shell脚本。

钩子函数脚本用于自定义一些git命令执行时候触发的脚本。比如commit、applypatch、push、rebase被执行会触发相关脚本。要使这些生效，把文件的sample后缀去掉。

git有很多的操作，在某些操作之前或者之后实际上是可以触发一些特定的`hooks`来去做特定的事情，可以用于条件判断的设置。例如：在执行`commit`之前，可以使用一个`pre-commit`脚本，然后在触发`commit`之后，还可以使用`prepare-commit-msg`脚本，这样是对本地的`hooks`；其实还可以对远程设置一些`hooks`。

**2. info文件夹**

`info文件夹`目录中包含一个全局性排除文件，用于放置那些不希望被记录在`.gitignore`文件中的忽略模式（ignored patterns）。（记录不需要git进行管理的文件，忽略的文件不会提交到共享库中，所以不会被协作者共享）

**3. objects文件夹**

刚初始化后的新的git版本库中，objects自动创建了两个pack和info子目录，但均为空。

`info` 存放仓库的一些信息。
`logs（日志管理）` 保存所有的更新的引用记录，
`数据对象(blob)` 存放所有数据。

1. 数据对象的产生是在使用`git add`命令将文件或者目录加入暂存区时产生的，git会把一个文件中要存储的数据和一个头部信息一起做SHA-1散列运算，将得到的散列值作为这个文件的路径。
如：初始化一个git仓库，然后将test.txt add加入仓库暂存区，这时`objects`目录下回看到一个`e6/9de29bb2d1d6434b8b29ae775ad8c2e48c5391`，git会根据数据对象的内容计算出40位的SHA-1散列值，前两个字母用于命名子目录，剩余的38个字符则用作文件名，这样就已经得到一个git下的数据对象。

2. `git cat-file -t` 选项查看该内容的对象类型。例：git cat-file -t e69d 会得到 blob 类型。

3. `git cat-file -p` 选项可以指示该命令自动判断内容的类型，并显示内容。

4. git对象一共有三种：数据对象(blob)、树对象(tree)以及提交对象(commit)。

**4. refs文件夹**

存储指向数据(分支)的提交对象的指针

`trfs` 保存当前自信的一次提交的哈希值

`tags` 记录任何对象的名称（不一定是提交对象或指向提交对象的标签对象）

**5. config**

文件包含项目特有的配置选项

**6. description**

仓库的描述信息，主要给gitweb等git托管系统使用

**7. HEAD**

HEAD指针，指向当前分支，即：记录当前活动的分支。

如果打开查看.HEAD文件内容，就可以清除的看到它指向了master分支。

**8. index**

暂存区（stage），一个二进制文件。文件保存暂存区信息。