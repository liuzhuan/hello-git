# 管理分支

[online reading](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

Git 不存储变更，只存储一系列快照 snapshots 。

当创建一次提交，Git 会储存一个提交对象，其中包含一个指向暂存区内容的指针。这个对象还包含作者信息，以及指向父提交的指针。

第一次提交：

![commit and tree](https://git-scm.com/book/en/v2/images/commit-and-tree.png)

在 Git 中创建分支很简单，就是向一个文件写入 41 字节。

## 创建分支及合并
[online reading](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

## 分支管理
[online reading](https://git-scm.com/book/en/v2/Git-Branching-Branch-Management)

查看所有本地分支

```sh
$ git branch
```

查看各分支的最新提交

```sh
$ git branch -v
```

查看哪些分支已经合并到当前分支

```sh
$ git branch --merged
```

查看所有未合并至当前分支的分支：

```sh
$ git branch --no-merged
```

## 分支工作流
[online reading](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)

有几种使用 Git 分支的工作流：长期分支、话题分支

## 远程分支
[online reading](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches)

远程引用 *remote references* 是指向远程仓库的指针。远程跟踪分支 *remote-tracking branches* 是远程分支的引用。

To Be Continued