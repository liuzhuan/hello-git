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

git add -A # 
git add -u
git add -i

git commit
git commit -a
git commit -m 'initialized'

git push

git pull
git pull mirror master # 将 mirror 版本库中的数据同步到本地

git tag v1 # 创建里程碑

git format-patch v1.. HEAD # 将从 v1 开始的历次提交逐一导出为补丁文件

git send-email *.patch # 通过邮件将补丁文件发出
```

## REF

- http://www.worldhello.net/gotgit/