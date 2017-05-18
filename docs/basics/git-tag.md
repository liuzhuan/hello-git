# How to use git tag?

http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951758572072ce1dc172b4178b910d31bc7521ee4000

Author: Michael Liao

## Add Tag

```
$ git tag v1.0      # add tag
$ git tag           # check all tags
```

默认标签是打在最新提交的 commit 上的。如果要找到历史提交的 commit id，然后打上就可以了。

```
$ git log --pretty=oneline --abbrev-commit
6a5819e merged bug fix 101
cc17032 fix bug 101
6224937 add merge
```

比方说要对 `add merge` 这次提交打标签，它对应的 commit id 是 `6224937`，敲入命令：

```
$ git tag v0.9 6224937
```

再用命令 `git tag` 查看标签：

```
$ git tag
v0.9
v1.0
```

可以用 `git show <tagname>` 查看标签信息：

```
$ git show v0.9
```

还可以创建带有说明的标签，用 `-a` 指定标签名，`-m` 指定说明文字：

```
$ git tag -a v0.1 -m "version 0.1 released" 3628164
$ git show v0.1
```

还可以通过 `-s` 用私钥签名一个标签：

```
$ git tag -s v0.2 -m "signed version 0.2 released" fec145a
```

签名采用 PGP 签名，因此，必须首先安装 gpg (GnuPG)。

## 操作标签

http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001376951885068a0ac7d81c3a64912b35a59b58a1d926b000

删除标签

```
$ git tag -d v0.1
```

推送标签到远程：

```
$ git push origin v1.0
```

一次性推送全部尚未推送到远程的本地标签：

```
$ git push origin --tags
```

如果要删除远程标签，首先删除本地标签：

```
$ git tag -d v0.9
```

然后，从远程删除：

```
$ git push origin :refs/tags/v0.9
```