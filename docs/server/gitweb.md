# GitWeb

[online reading](https://git-scm.com/book/en/v2/Git-on-the-Server-GitWeb)

GitWeb 是 Git 自带的 CGI 脚本，可以呈现基于网络的可视化。

```sh
# 开启 webrick 服务器
$ git instaweb --httpd=webrick

# 关闭 webrick 服务器
$ git instaweb --httpd=webrick --stop
```

如何想在私有主机部署 web 界面，则需要自定义 CGI 脚本：

```sh
$ git clone git://git.kernel.org/pub/scm/git/git.git
$ cd git/
$ make GITWEB_PROJECTROOT="/srv/git" prefix=/usr gitweb
$ sudo cp -Rf gitweb /var/www
```

