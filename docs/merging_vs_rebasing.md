# [Merging vs. Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing)

作者：Atlassian

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

或者简写为单行指令：

```
git merge master feature
```

它会在 feature 分支产生一个新的 `merge commit`，把两个分支历史合并到一起，形成如下的分支结构：

![Merging master into the feature branch](https://wac-cdn.atlassian.com/dam/jcr:e229fef6-2c2f-4a4f-b270-e1e1baa94055/02.svg?cdnVersion=dr)

## The Golden Rule of Rebasing

## Workfow walkthrough

## Summary