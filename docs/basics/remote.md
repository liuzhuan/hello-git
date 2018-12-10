# 操作远程仓库

[online reading](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)

## 查看远程仓库
```sh
$ git remote
$ git remote -v
```

## 增加远程仓库
```sh
# git remote add <shortname> <url>
$ git remote add pb https://github.com/paulboone/ticgit
```

## 获取远程仓库的新代码
```sh
# git fetch <remote>
$ git fetch pb
```

## 推送到远程仓库
```sh
# git push <remote> <branch>
$ git push origin master
```

## 检查远程仓库
```sh
# git remote show <remote>
$ git remote show origin
```

## 重命名和删除远程仓库
```sh
$ git remote rename pb paul
$ git remote remove paul
```