# Git CheatSheet

diff & patch

```sh
diff -u hello world > diff.txt # 生成 diff 文件 -u 产生上下文代码行

cp hello world
patch world < diff.txt # patch 是 diff 的逆向操作

cp world hello
patch -R hello < diff.txt
```

```sh
git init # 版本库初始化

git add # 将修改内容加入提交暂存区
git add -A # 将本地删除文件和新增文件都登记到提交暂存区
git add -u # 将所有修改过的文件加入暂存区
git add -i
git add -p # 对一个文件内的修改进行有选择性的添加

git checkout <new_branch> # 签出新分支

git commit
git commit -a
git commit -m 'initialized'
git commit --amend # 修改提交说明

git diff
git diff --word-diff # 进行逐字比较

git push

git pull
git pull mirror master # 将 mirror 版本库中的数据同步到本地

git rebase -i <commit-id>^ # 修改 <commit-id> 对应的提交说明

# 删除不应提交的大文件
git rm --cached winxp.img
git commit --amend

git stash # 保存工作进度
git stash pop # 恢复之前保存的工作进度

git tag v1 # 创建里程碑

git format-patch v1.. HEAD # 将从 v1 开始的历次提交逐一导出为补丁文件

git send-email *.patch # 通过邮件将补丁文件发出

git grep # 在工作区根目录下执行查找（忽略 .git 目录）
```

## REF

- http://www.worldhello.net/gotgit/