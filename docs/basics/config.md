[online read](https://git-scm.com/book/en/v2)

本书使用的 Git 版本是 v2.8.0。查看本地版本 `git --version`

## 第一次设置
`git config` 可以设置 Git 参数。它的存储位置有以下三种：

1. `/etc/gitconfig` 文件：包含操作系统所有用户和所有仓库的参数。使用 `--system` 参数设定（需要管理员权限）。
2. `~/.gitconfig` 或 `~/.config/git/config` 文件：针对个人的设定。使用 `--global` 参数设定。
3. 存在于 Git 仓库的 `config` 文件：位于 `.git/config`，使用 `--local` 参数设定。它是默认值。

### 身份设定
```sh
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

### 设定编辑器
```sh
$ git config --global core.editor emacs
```

### 检查设定参数
```sh
$ git config --list
$ git config user.name
```

## 获取帮助
```sh
# git help <verb>
# OR
# man git-<verb>
$ git help config
```