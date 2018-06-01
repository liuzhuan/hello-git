# Working With Remotes

https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes

## Showing Your Remotes

```
git remote
git remote -v
```

## Adding Remote Repositories

To add a new remote Git repository as a shortname you can reference easily, run `git remote add <shortname> <url>`:

```
git remote add pb https://github.com/paulboone/ticgit
```

## 删除远程分支

使用 `git push` 的 [`--delete`][remote-branches] 选项，可以删除远程分支。

```sh
$ git push origin --delete serverfix
```

[remote-branches]: https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches