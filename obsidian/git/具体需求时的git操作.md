# 撤回
>当自己发现最新的修改没有用，需要回到最后一次提交时的状态时，可以使用"git checkout -- <file\>..."或"git restore <file\>..."可以丢弃工作区的修改。
>
>如果发现已经git add到缓存区了，可以使用"git reset HEAD <file\>"或"git restore --staged <file\>..."可以把暂存区的修改撤销掉（unstage），重新放回工作区。然后和上一个步骤一样。
>
>如果发现不仅git add还git commit，可以版本回退。


```bash
$ git checkout -- readme.txt
```

命令`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，这里有两种情况：

一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态。
