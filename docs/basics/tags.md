# Git 标签
[online reading](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

## 查看标签
```sh
$ git tag
# 只查看 1.8.5 相关的标签
$ git tag -l "v1.8.5*"
```

## 创建标签
Git 有两种标签：轻量 *lightweight* 和附注 *annotated*。

轻量标签和分支类似，只是指针，指向一个固定的提交。

附注标签，在 Git 仓库中作为一个完整对象存储。可以包含提交信息，加密信息等附注内容。

### 附注标签

使用 `-a` 就可以创建附注标签。`-m` 指定标签信息。

```sh
$ git tag -a v1.4 -m "my version 1.4"
```

### 轻量标签

```sh
$ git tag v1.4-1w
```

### 稍晚打标签

```sh
$ git tag -a v1.2 9fceb02
```

## 分享标签
`git push` 默认不向远程仓库推送标签。需要明确指定标签名称，

```sh
# git push origin <tagname>
$ git push origin v1.5
```

如果标签数量较多，可以使用 `--tags`  选项，将其一次性推到远端：

```sh
$ git push origin --tags
```

## 删除标签
删除本地标签：

```sh
# git tag -d <tagname>
$ git tag -d v1.4-lw
```

删除远程标签：

```sh
# git push <remote> :refs/tags/v1.4-lw
$ git push origin :refs/tags/v1.4-lw
```

## 签出标签
```sh
$ git checkout 2.0.0
```