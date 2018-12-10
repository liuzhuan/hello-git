# Git 别名
[online reading](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases)

```sh
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status

$ git config --global alias.unstage 'reset HEAD --'

$ git config --global alias.last 'log -1 HEAD'
```