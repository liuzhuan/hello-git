# 底层命令（plumbing）和高层命令（porcelain）

[online reading](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain)

1. Git 底层是内容寻址的文件系统（content-addressable filesystem），上层用户界面为版本控制系统。
2. v1.5 之前，Git 更重视开发底层的文件系统，因此用户界面相当复杂。
3. Git 起初定位版本控制系统工具集，有很多底层命令。它们借鉴 UNIX 做法，可以综合使用。这些命令就是底层命令（plumbing commands，就像自来水网络中的管道系统，虽然看不见，但是极其重要）。
4. 面向用户的指令称为高层指令（porcelain commands，就像卫生瓷具，每天都在用，体验很好，隐藏了底层复杂的排水管道）。
5. 使用命令 `ls -F1 .git` 可以查看 `.git` 目录下的各种文件和目录。其中有以下普通文件：
   * `description` 用于 `GitWeb` 程序
   * `config` 是项目级配置文件
   * `info/` 目录下的 exclude 文件，存储全局忽略文件模板，是 `.gitignore` 的补充
   * `hooks` 包含客户端和服务端的钩子脚本
6. 另外，还有以下四个文件，它们是 Git 的核心：
   * `HEAD` 指向当前签出的分支
   * `index` 存储暂存区数据信息
   * `objects/` 存储所有的内容
   * `res` 存储指向提交的指针