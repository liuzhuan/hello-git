# Git 基础操作
[online reading](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)

## 获取 Git 仓库
有两种获取 Git 仓库的方法：
1. 在本地创建目录，将其转换为仓库
2. 克隆其他的 Git 仓库

### 初始化本地目录

```sh
$ git init
$ git add .
$ git commit -m 'initial project version'
```

### 克隆现存仓库

```sh
# git clone <url>
$ git clone https://github.com/libgit2/libgit2 mylibgit
```

## 向仓库新增记录
仓库中的文件只有两种状态：跟踪中 tracked 和未跟踪 untracked。Git 只认识跟踪中的文件。

```sh
$ git status
$ git add README
```

### 查看简洁状态

```sh
$ git status -s
```

### 忽略文件

`.gitignore` 可以忽略文件。其语法如下：

```
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

### 查看暂存和未暂存的改动

```sh
# 查看未暂存的改动
$ git diff
# 对比暂存区和最新提交的改动
$ git diff --staged
# cached 和 staged 是同义词
$ git diff --cached
```

### 提交改动

```sh
$ git commit
$ git commit -m "Story 182: Fix benchmarks for speed"
```

每次提交都会生成独特的 SHA-1 校验和。

### 跳过暂存区

```sh
$ git commit -a
```

### 删除文件

```sh
# Remove files from the working tree and from the index
$ git rm PROJECTS.md
# 支持 glob 通配符，注意转义符
$ git rm log/\*.log
```

如果想删除暂存区文件，但保留工作区文件，需要使用 `--cached` 选项：

```sh
$ git rm --cached README
```

### 移动文件

```sh
$ git mv file_from file_to
```

## 查看提交历史
[online reading](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)

```sh
$ git log
```

查看改动内容使用 `-p` 或 `--patch`，使用 `-2` 可以只显示最新 2 条提交。

```sh
$ git log -p -2
```

使用 `--stat` 查看提交的简报：

```sh
$ git log --stat
```

另一个有用选项是 `--pretty`

```sh
$ git log --pretty=oneline
$ git log --pretty=short
$ git log --pretty=full
$ git log --pretty=fuller
```

最有趣的选项是 `format`，可以自定义输出格式：

```sh
$ git log --pretty=format:"%h - %an, %ar : %s"
```

常用的 format 选项修饰符如下：

* `%H` Commit hash
* `%h` Abbreviated commit hash
* `%T` Tree hash
* `%t` Abbreviated tree hash
* `%P` Parent hashes
* `%p` Abbreviated parent hashes
* `%an` Author name
* `%ae` Author Email
* `%ad` Author date
* `%ar` Author date, relative
* `%cn` Committer name
* `%ce` Committer email
* `%cd` Committer date
* `%cr` Committer date, relative
* `%s` subject

`oneline` 和 `format` 选项和另一选项 `--graph` 很配。会输出分支的图形。

### 限制日志输出

时间分割选项，比如 `--since` 和 `--until` 很有用。比如，以下命令输出最近两周的提交：

```sh
$ git log --since=2.weeks
```

还可以设定一些日志输出的过滤条件，比如 `--author` 可以过滤特定作者，`--grep` 可以过滤提交信息的某些关键字。

另一个有用的选项是 `-S`，即俗话说的“鹤嘴锄”选项，它的输入是一个字符串，输出是所有改变该字符串的提交。

```sh
$ git log -S function_name
```

还可以使用路径，将输出限定在指定路径的提交之中。通常，它是最后一个选项，之前会用 `--` 与参数做分隔。

结合使用过滤选项，可以精确定位一些提交：

```sh
$ git log --pretty="%h - %s" --author='Junio C Hamano' --since="2008-10-01" --before="2008-11-01" --no-merges -- t/
```

## 撤销操作
[online reading](https://git-scm.com/book/en/v2/Git-Basics-Undoing-Things)

如果要修改最近的提交信息，可以使用 `--amend` 选项：

```sh
$ git commit --amend
```

### 撤销暂存区的文件

```sh
$ git reset HEAD <file>
```

### 撤销编辑文件

```sh
$ git checkout -- <file>
```
