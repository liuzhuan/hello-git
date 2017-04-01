# gitlab/github 多账户下设置 ssh keys

作者：YonBo

日期：2015年7月16日

## 背景

公司用 gitlab, 个人用 github，默认情况下本地生成的密钥位于 `~/.ssh/` 下，会冲突。

解决办法是生成后一个密钥，对其重命名，同时将不同密钥配置到相对应的Host上。具体操作如下：

## 生成 gitlab 密钥

本地生成 ssh keys:

```sh
ssh-keygen -t rsa -C "注册的gitlab邮箱"
```

查看公钥内容：

```sh
cat ~/.ssh/id_rsa.pub
```

## 生成 github 密钥

终端执行命令：

```sh
ssh-keygen -t rsa -C "注册的github邮箱"
```

这次要对密钥进行重命名，暂且重命名为 `id_rsa_home`。可以看到公私密钥分别被重命名为 `id_rsa_home.pub` 和 `id_rsa_home`。

查看公钥里面的内容：

```sh
cat ~/.ssh/id_rsa_home.pub
```

## 配置 config

在 `.ssh/` 目录下新建 config 文件：`touch config`，然后进行如下设置：

```
# gitlab
Host gitlab
    HostName gitlab.****.com
    IdentityFile ~/.ssh/id_rsa

# github
Host github
    HostName github.com
    IdentityFile ~/.ssh/id_rsa_home
```

## 检测

检测 gitlab 和 github 连接：

```
ssh -T git@github
ssh -T git@gitlab
```

## Reference
- [gitlab/github 多账户下设置 ssh keys](https://segmentfault.com/a/1190000002994742)