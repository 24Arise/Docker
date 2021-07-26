# Docker 安装 Vim

> `Docker` 找不到 `Vim` 命令

```
root@26adb0ff2e8d:# vim mysqld.cnf

bash: vim: command not found
```

- 安装

> `apt-get install vim`

```
root@26adb0ff2e8d:# apt-get install vim
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package vim
```

- 原因

> 未同步 `/etc/apt/sources.list` 和 `/etc/apt/sources.list.d`  中列出的源的索引，不能获取到最新的软件包
>
> - 执行
>
> `apt-get update`

```
root@26adb0ff2e8d:# apt-get update
Get:1 http://security.debian.org/debian-security buster/updates InRelease [65.4 kB]
Get:2 http://deb.debian.org/debian buster InRelease [122 kB]
Get:3 http://repo.mysql.com/apt/debian buster InRelease [21.5 kB]
Get:4 http://security.debian.org/debian-security buster/updates/main amd64 Packages [293 kB]
Get:5 http://repo.mysql.com/apt/debian buster/mysql-5.7 amd64 Packages [5692 B]
Get:6 http://deb.debian.org/debian buster-updates InRelease [51.9 kB]
Get:7 http://deb.debian.org/debian buster/main amd64 Packages [7907 kB]
Get:8 http://deb.debian.org/debian buster-updates/main amd64 Packages [15.2 kB]
Fetched 8481 kB in 10s (844 kB/s)
Reading package lists... Done
```

- 解决

> 再次执行
>
> `apt-get install vim`
