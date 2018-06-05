# 重写提交历史

在本地，可以随意修改提交历史。一旦提交到远程，将无法轻易更改。所以，下面的所有操作都是针对本地仓库进行。

## 修改上一次提交

如果要修改上一次提交的 commit 信息，可以执行：

```sh
$ git commit --amend
```

该命令会将上一次提交内容加载到一个编辑器会话中。

## 修改多条提交信息

如果要修改前三条提交历史，可以执行交互的变基操作：

```sh
$ git rebase -i HEAD~3
```

## REF

- [7.6 Git Tools - Rewriting History][rewrite]

[rewrite]: https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History