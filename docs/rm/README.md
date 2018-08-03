# 停止追踪文件

`gitignore` 的目的是忽略某些文件，这些文件尚未被仓库追踪。

如果要忽略已经跟踪的文件，需要使用 `git rm --cached`。

`git rm` 可以从当前工作目录和暂存区删除文件。删除目录时，需要使用 `-r` 递归删除子目录。

`--cached` 选项只删除暂存区的文件，工作区的文件，不管有没有改变，都不会受影响。

所以，如果 `build/` 目录已经被追踪，后续需要删除该目录，需要进行如下操作：

```sh
$ vim .gitignore
# add build/ entry
$ git rm --cached -r build
$ git commit -m "Say Something Awesome~"
```

## REF

- [gitignore][gitignore]
- [git-rm][rm]

[gitignore]: https://git-scm.com/docs/gitignore
[rm]: https://git-scm.com/docs/git-rm