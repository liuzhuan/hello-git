# Merging vs. Rebasing

来源：[Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

## 概念

`git rebase` 与 `git merge` 目的一样，都是为了把某一分支的变化整合到另一分支，只是处理方式不同。

假如我们为了开发新特性，从 master 主干拉取新分支 `feature` 单独开发。然后，其他人更新主干后，就会造成**分叉历史**（forked history）。

![A forked commit history](https://wac-cdn.atlassian.com/dam/jcr:01b0b04e-64f3-4659-af21-c4d86bc7cb0b/01.svg?cdnVersion=dr)

如果主干的新提交与开发中的新特性相关，需要合并到 `feature` 分支。我们有两种选择：合并（merging）或变基（rebasing）。

## Merge 选项

最简单的做法是将 master 分支合并到 feature 分支：

```
git checkout feature
git merge master
```

它会在 feature 分支产生一个新的 `merge commit`，把两个分支历史合并到一起，形成如下的分支结构：

![Merging master into the feature branch](https://wac-cdn.atlassian.com/dam/jcr:e229fef6-2c2f-4a4f-b270-e1e1baa94055/02.svg?cdnVersion=dr)

Merge 的好处是：它是*无损*操作（*non-destructive* operation），现存分支没被更改，这能避免 rebase 潜在的一些陷阱。

但是这还意味着，每次我们整合上游的变化时，feature 分支都生成多余的 commit 节点。如果 master 分支比较活跃，将严重污染 feature 的分支历史。尽管 `git log` 的高级特性可以缓解这个问题，其他人理解项目历史时，还是会很困难。

## Rebase 选项

作为 merge 的替代选项，我们还可以将 feature `变基`（rebase）到 master 分支。命令如下：

```
git checkout feature
git rebase master
```

这会把整个 feature 分支移动到 master 分支的顶端，实际上整合了 master 所有的新提交。rebase 没有使用新的提交，而是重写了项目历史：旧分支的每个提交，都会转换为一个全新的提交。

![Rebasing the feature branch onto master](https://wac-cdn.atlassian.com/dam/jcr:5b153a22-38be-40d0-aec8-5f2fffc771e5/03.svg?cdnVersion=dr)

rebase 的主要优点是，项目的提交历史能变得十分清爽。首先，它能避免 `git merge` 引入的多余 commit 节点。第二，从上图可以看出，rebase 可以产生完美的线性提交历史。这样在提交历史中导航就会十分简单，可以使用 `git log`, `git bisect` 和 `gitk` 等命令。

但是，纯洁的提交历史也有两个代价：安全性和可回溯性。如果不遵循 **rebase 黄金法则**，重写项目历史可能会对合作开发带来灾难性的后果。并且，rebase 失去了 merge 带来的上下文信息 - 你会看不出什么时间上游提交引入到当前分支。

## 交互式 rebase

交互式 rebase 让你有机会修改提交历史。它提供了对新分支历史的完全控制。它主要用来清理 feature 混乱分支历史，然后再合并至 master 分支。

使用 `i` 选项开启交互式 rebase：

```
git checkout feature
git rebase -i master
```

这会打开一个文本编辑器，列举出所有的提交：

```
pick 33d5b7a Message for commit #1
pick 9480b3d Message for commit #2
pick 5c67e61 Message for commit #3
```

这个列表精确定义了 rebase 提交后的分支结构。通过修改 `pick` 命令，或者调整列表元素的顺序，可以随意修改提交历史。举个例子，如果第二个提交只是修改了第一个提交的小问题，可以把二者合并为一个条目，使用 `fixup` 命令即可：

```
pick 33d5b7a Message for commit #1
fixup 9480b3d Message for commit #2
pick 5c67e61 Message for commit #3
```

当保存关闭文件后，Git 就会依照你的指令执行 rebase 操作，形成下面的分支结构：

![Squashing a commit with an interactive rebase](https://wac-cdn.atlassian.com/dam/jcr:fe6942b4-7a60-4464-9181-b67e59e50788/04.svg?cdnVersion=dr)

像这样删除掉无关紧要的提交节点后，feature 分支历史就能更容易理解。git merge 做不到这些。

## rebase 黄金法则

理解了 rebase 的概念后，最重要的是知道什么时候不要 rebase 。`git rebase` 的黄金法则是**永远不要在公共分支上执行 `git rebase` 操作**。

比如，如果把 master 变基到 feature 分支，分支结构就会变成：

![Rebasing the master branch](https://wac-cdn.atlassian.com/dam/jcr:1d22f018-b2c7-4096-9db1-c54940cf4f4e/05.svg?cdnVersion=dr)

rebase 会把所有 master 提交节点移动到 feature 分支提交历史的顶端。问题是这个变动只是发生在你的仓库，其他人还继续在原来 master 分支工作。因为 rebase 产生了全新提交，Git 会认为你的 master 分支已经与其他人的 master 分支产生分歧。

所以，执行 `git rebase` 前，一定先问问自己，“有没有其他人也在这个分支做开发？”如果回答“有”，马上离开键盘，考虑一种无损的方式（比如，`git revert` 命令）。如果只是自己开发，你可以随心所欲的修改历史。