# Git CheatSheet

## diff & patch

```sh
diff -u hello world > diff.txt # 生成 diff 文件 -u 产生上下文代码行

cp hello world
patch world < diff.txt # patch 是 diff 的逆向操作

cp world hello
patch -R hello < diff.txt
```

## git 基本操作

```sh
git init # 版本库初始化

git add # 将修改内容加入提交暂存区
git add -A # 将本地删除文件和新增文件都登记到提交暂存区
git add -u # 将所有修改过的文件加入暂存区
git add -i
git add -p # 对一个文件内的修改进行有选择性的添加

git checkout <new_branch> # 签出新分支

git clean
git clean -fdx # 删除没有被版本控制的文件和目录

git commit
git commit -a
git commit -m 'initialized'
git commit --amend # 修改提交说明

git config --global color.ui true # 彩色字符输出
git config --global core.pager 'less -+$ LESS -FRX' # 改变分页器的默认行为

git diff
git diff --word-diff # 进行逐字比较

git fetch # 获取最新的版本

git push

git pull
git pull mirror master # 将 mirror 版本库中的数据同步到本地

git rebase -i <commit-id>^ # 修改 <commit-id> 对应的提交说明

git reset --hard

# 删除不应提交的大文件
git rm --cached winxp.img
git commit --amend

git stash # 保存工作进度
git stash pop # 恢复之前保存的工作进度

git tag # 查看里程碑
git tag v1 # 创建里程碑

git format-patch v1.. HEAD # 将从 v1 开始的历次提交逐一导出为补丁文件

git send-email *.patch # 通过邮件将补丁文件发出

git grep # 在工作区根目录下执行查找（忽略 .git 目录）
```

## install git

```sh
# linux

## 包管理方式安装

### Ubuntu 10.10+ (maverick) || Debian (squeeze)+
sudo aptitude install git
sudo aptitude install git-doc git-svn git-email git-gui gitk

### Ubuntu 10.04- (lucid) || Debian (lenny)-
sudo aptitude install git-core
sudo aptitude install git-doc git-svn git-email git-gui gitk # 因为 git 被 GNU Interactive Tools 提前占用

### RHEL || Fedora || CentOS
yum install git
yum install git-svn git-email git-gui gitk

## 从源代码进行安装

tar -jxvf git-1.7.4.1.tar.bz2
cd git-1.7.4.1/
make prefix=/usr/local all
sudo make prefix=/usr/local install

make prefix=/usr/local doc info # 安装文档 
sudo make prefix=/usr/local install-doc install-html install-info

## 从 Git 版本库进行安装
git clone git://git.kernel.org/pub/scm/git/git.git
cd git
git fetch
git clean -fdx
git reset --hard
git tag
git checkout v1.7.4.1
make prefix=/usr/local all doc info
sudo make prefix=/usr/local install install-doc install-html install-info
```

## git with svn

```sh
git svn clone <svn_repos_url> # 将 svn 版本库克隆为一个本地的 Git 库

git svn fetch
git svn rebase
git svn dcommit
```

## REF

- http://www.worldhello.net/gotgit/