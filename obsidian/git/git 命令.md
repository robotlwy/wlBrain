# 创建版本库
## git init 
初始化版本库
## git add
将文件添加到仓库
## git commit
将文件提交到仓库
## git status
**git status** 是一个用于查看 Git 仓库当前状态的命令。
**git status** 命令可以查看在你上次提交之后是否有对文件进行再次修改。
git status 命令会显示以下信息：

- 当前分支的名称。
- 当前分支与远程分支的关系（例如，是否是最新的）。
- 未暂存的修改：显示已修改但尚未使用 `git add` 添加到暂存区的文件列表。
- 未跟踪的文件：显示尚未纳入版本控制的新文件列表。
根据 git status 的输出，你可以判断当前工作目录中的文件状态，并采取适当的操作。

通常我们使用 -s 参数来获得简短的输出结果：

$ git status -s
AM README
A  hello.php

## git diff
git diff 命令比较文件的不同，即比较文件在暂存区和工作区的差异。

git diff 命令显示已写入暂存区和已经被修改但尚未写入暂存区文件的区别。

git diff 有两个主要的应用场景。

- 尚未缓存的改动：**git diff**
- 查看已缓存的改动： **git diff --cached**
- 查看已缓存的与未缓存的所有改动：**git diff HEAD**
- 显示摘要而非整个 diff：**git diff --stat**


# Git 查看提交历史
查看 Git 提交历史可以帮助你了解代码的变更情况和开发进度。

Git 提供了多种命令和选项来查看提交历史，从简单的日志到详细的差异对比。

Git 提交历史一般常用两个命令：

- **git log** - 查看历史提交记录。
- **git blame <file\>** - 以列表形式查看指定文件的历史修改记录。

## git log
在使用 Git 提交了若干更新之后，又或者克隆了某个项目，想回顾下提交历史，我们可以使用 git log 命令查看。

**git log** 命令用于查看 Git 仓库中提交历史记录。

**git log** 显示了从最新提交到最早提交的所有提交信息，包括提交的哈希值、作者、提交日期和提交消息等。

**git log** 命令的基本语法：

git log [选项] [分支名/提交哈希]

常用的选项包括：

- `-p`：显示提交的补丁（具体更改内容）。
- `--oneline`：以简洁的一行格式显示提交信息。
- `--graph`：以图形化方式显示分支和合并历史。
- `--decorate`：显示分支和标签指向的提交。
- `--author=<作者>`：只显示特定作者的提交。
- `--since=<时间>`：只显示指定时间之后的提交。
- `--until=<时间>`：只显示指定时间之前的提交。
- `--grep=<模式>`：只显示包含指定模式的提交消息。
- `--no-merges`：不显示合并提交。
- `--stat`：显示简略统计信息，包括修改的文件和行数。
- `--abbrev-commit`：使用短提交哈希值。
- `--pretty=<格式>`：使用自定义的提交信息显示格式。

针对我们前一章节的操作，使用 git log 命令列出历史提交记录如下：

```bash
$ git log
commit d5e9fc2c811e0ca2b2d28506ef7dc14171a207d9 (HEAD -> master)
Merge: c68142b 7774248
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:55:58 2019 +0800

    Merge branch 'change_site'

commit c68142b562c260c3071754623b08e2657b4c6d5b
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:52:12 2019 +0800

    修改代码

commit 777424832e714cf65d3be79b50a4717aea51ab69 (change_site)
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:49:26 2019 +0800

    changed the runoob.php

commit c1501a244676ff55e7cccac1ecac0e18cbf6cb00
Author: runoob <test@runoob.com>
Date:   Fri May 3 15:35:32 2019 +0800
```

我们可以用 --oneline 选项来查看历史记录的简洁的版本。

```bash
$ git log --oneline
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
c68142b 修改代码
7774248 (change_site) changed the runoob.php
c1501a2 removed test.txt、add runoob.php
3e92c19 add test.txt
3b58100 第一次版本提交
```

这告诉我们的是，此项目的开发历史。

我们还可以用 --graph 选项，查看历史中什么时候出现了分支、合并。以下为相同的命令，开启了拓扑图选项：

```bash
$ git log --graph
*   d5e9fc2 (HEAD -> master) Merge branch 'change_site'
|\  
| * 7774248 (change_site) changed the runoob.php
* | c68142b 修改代码
|/  
* c1501a2 removed test.txt、add runoob.php
* 3e92c19 add test.txt
* 3b58100 第一次版本提交
```

现在我们可以更清楚明了地看到何时工作分叉、又何时归并。

你也可以用 **--reverse** 参数来逆向显示所有日志。

```bash
$ git log --reverse --oneline
3b58100 第一次版本提交
3e92c19 add test.txt
c1501a2 removed test.txt、add runoob.php
7774248 (change_site) changed the runoob.php
c68142b 修改代码
d5e9fc2 (HEAD -> master) Merge branch 'change_site'
```

如果只想查找指定用户的提交日志可以使用命令：git log --author , 例如，比方说我们要找 Git 源码中 Linus 提交的部分：

```bash
$ git log --author=Linus --oneline -5
81b50f3 Move 'builtin-*' into a 'builtin/' subdirectory
3bb7256 make "index-pack" a built-in
377d027 make "git pack-redundant" a built-in
b532581 make "git unpack-file" a built-in
112dd51 make "mktag" a built-in
```

如果你要指定日期，可以执行几个选项：--since 和 --before，但是你也可以用 --until 和 --after。

例如，如果我要看 Git 项目中三周前且在四月十八日之后的所有提交，我可以执行这个（我还用了 --no-merges 选项以隐藏合并提交）：

```bash
$ git log --oneline --before={3.weeks.ago} --after={2010-04-18} --no-merges
5469e2d Git 1.7.1-rc2
d43427d Documentation/remote-helpers: Fix typos and improve language
272a36b Fixup: Second argument may be any arbitrary string
b6c8d2d Documentation/remote-helpers: Add invocation section
5ce4f4e Documentation/urls: Rewrite to accomodate transport::address
00b84e9 Documentation/remote-helpers: Rewrite description
03aa87e Documentation: Describe other situations where -z affects git diff
77bc694 rebase-interactive: silence warning when no commits rewritten
636db2c t3301: add tests to use --format="%N"
```

### 常用选项

限制显示的提交数:

git log -n <number\>

例如，显示最近的 5 次提交：

git log -n 5

显示自指定日期之后的提交：

git log --since="2024-01-01"

显示指定日期之前的提交：

git log --until="2024-07-01"

只显示某个作者的提交：

git log --author="Author Name"

更多 **git log** 命令可查看 [http://git-scm.com/docs/git-log](http://git-scm.com/docs/git-log) 或使用 git log --help 命令查看帮助信息。

## git blame

**git blame** 命令用于逐行显示指定文件的每一行代码是由谁在什么时候引入或修改的。

**git blame** 可以追踪文件中每一行的变更历史，包括作者、提交哈希、提交日期和提交消息等信息。

如果要查看指定文件的修改记录可以使用 git blame 命令，格式如下：

git blame [选项] <文件路径>

常用的选项包括：

- `-L <起始行号>,<结束行号>`：只显示指定行号范围内的代码注释。
- `-C`：对于重命名或拷贝的代码行，也进行代码行溯源。
- `-M`：对于移动的代码行，也进行代码行溯源。
- `-C -C` 或 `-M -M`：对于较多改动的代码行，进行更进一步的溯源。
- `--show-stats`：显示包含每个作者的行数统计信息。

显示文件每一行的代码注释和相关信息：

git blame <文件路径>

只显示指定行号范围内的代码注释：

git blame -L <起始行号>,<结束行号> <文件路径>

对于重命名或拷贝的代码行进行溯源：

git blame -C <文件路径>

对于移动的代码行进行溯源：

git blame -M <文件路径>

显示行数统计信息：

git blame --show-stats <文件路径>

git blame 命令是以列表形式显示修改记录，如下实例：

```bash
$ git blame README 
^d2097aa (tianqixin 2020-08-25 14:59:25 +0800 1) # Runoob Git 测试
db9315b0 (runoob    2020-08-25 16:00:23 +0800 2) # 菜鸟教程 
```

更多内容可以使用 git blame --help 查看完整的帮助文档，了解更多选项和使用方式。
# 恢复和回退
Git 提供了多种方式来恢复和回退到之前的版本，不同的命令适用于不同的场景和需求。

以下是几种常见的方法：

- **`git checkout`**：切换分支或恢复文件到指定提交。
- **`git reset`**：重置当前分支到指定提交（软重置、混合重置、硬重置）。
- **`git revert`**：创建一个新的提交以撤销指定提交，不改变提交历史。
- **`git reflog`**：查看历史操作记录，找回丢失的提交。
## git checkout
git checkout 命令用于切换分支或恢复工作目录中的文件到指定的提交。

恢复工作目录中的文件到某个提交：

git checkout <commit\> -- <filename\>

例如，将 file.txt 恢复到 abc123 提交时的版本：

git checkout abc123 -- file.txt

切换到特定提交：

git checkout <commit\>

例如：

git checkout abc123

这种方式切换到特定的提交时，处于分离头指针（detached HEAD）状态。
## git reset 
git reset 命令用于回退版本，可以指定退回某一次提交的版本。

git reset 命令语法格式如下：

git reset [--soft | --mixed | --hard] [HEAD]

**--mixed** 为默认，可以不用带该参数，用于重置暂存区的文件与上一次的提交(commit)保持一致，工作区文件内容保持不变。

git reset  [HEAD] 

实例：

$ git reset HEAD^            # 回退所有内容到上一个版本  
$ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  $ git  reset  052e           # 回退到指定版本

**--soft** 只重置 HEAD 到指定的提交，暂存区和工作目录保持不变：

git reset --soft HEAD

实例：

$ git reset --soft HEAD~3   # 回退上上上一个版本 

**--hard** 重置 HEAD 到指定的提交，暂存区和工作目录都重置：

git reset --hard HEAD

实例：

$ git reset --hard HEAD~3  # 回退上上上一个版本  $ git reset –hard bae128  # 回退到某个版本回退点之前的所有信息。 $ git reset --hard origin/master    # 将本地的状态回退到和远程的一样 

**注意：**谨慎使用 **–-hard** 参数，它会删除回退点之前的所有信息。

**HEAD 说明：**

- HEAD 表示当前版本
    
- HEAD^ 上一个版本
    
- HEAD^^ 上上一个版本
    
- HEAD^^^ 上上上一个版本
    
- 以此类推...
    

可以使用 ～数字表示

- HEAD~0 表示当前版本
    
- HEAD~1 上一个版本
    
- HEAD^2 上上一个版本
    
- HEAD^3 上上上一个版本
    
- 以此类推...
## git revert
git revert 命令创建一个新的提交，用来撤销指定的提交，它不会改变提交历史，适用于已经推送到远程仓库的提交。

git revert <commit\>

例如，撤销 abc123 提交：

git revert abc123
## git reflog
git reflog 命令记录了所有 HEAD 的移动。即使提交被删除或重置，也可以通过 reflog 找回。

git reflog

利用 reflog 可以找到之前的提交哈希，从而恢复到特定状态。例如：

git reset --hard HEAD@{3}

