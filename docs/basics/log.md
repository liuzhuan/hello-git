# 查看提交历史

[版本回退](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000)

作者：廖雪峰

```sh
git log
# 只显示一行提交信息
git log --pretty=oneline
```

Git 的 `commit id` 是 SHA1 计算出来的一个非常大的数字，用十六进制表示。

在 Git 中，用 `HEAD` 表示当前的版本，上一个版本就是 `HEAD^`，上上一个版本就是 `HEAD^^`。往上100个版本写成 `HEAD-100`。

回退到上一个版本，可以使用 `get reset` 命令：

```sh
git reset --hard HEAD^
git reset --hard <commit-id> # 回退到任一提交
```

Git 提供了一个命令 `git reflog` 用来记录你的每一次命令：

```sh
git reflog
```