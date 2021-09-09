
`[ 1 ]` [docker 命令没有权限](#Q1)

---

# <a name="Q1">docker 命令没有权限 </a>

- 问题描述

安装完 docker 后，执行 docker 相关命令，出现：

```
”Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock:

Get http://%2Fvar%2Frun%2Fdocker.sock/v1.26/images/json: dial unix /var/run/docker.sock: connect: permission denied“
```

- 原因
  
摘自 docker mannual 上的一段话：

```
Manage Docker as a non-root user

The docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the user root and other users can only access it using sudo. The docker daemon always runs as the root user.

If you don’t want to use sudo when you use the docker command, create a Unix group called docker and add users to it. When the docker daemon starts, it makes the ownership of the Unix socket read/writable by the docker group

--- 

大概的意思就是：docker 进程使用 Unix Socket 而不是 TCP 端口。而默认情况下 Unix socket 属于 root 用户，需要 root 权限才能访问。
```

- 解决方式 1

使用 `sudo` 获取管理员权限，运行 docker 命令

```shell
🔥  ~  sudo docker ps -a          
Password:
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                      PORTS                                                  NAMES
4224b128cb72   hello-world   "/hello"                 58 minutes ago   Exited (0) 55 minutes ago                                                          vigilant_gagarin
49586a76cfa9   minio/minio   "/usr/bin/docker-ent…"   6 weeks ago      Up 30 minutes               0.0.0.0:9000->9000/tcp, :::9000->9000/tcp              ecstatic_leakey
acffd8c2a243   mysql:5.7     "docker-entrypoint.s…"   7 weeks ago      Up 50 minutes               0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql
28a017afa5f7   alpine/git    "git clone https://g…"   8 weeks ago      Exited (128) 8 weeks ago                                                           repo
🔥  ~  
```

- 解决方式 2

docker 守护进程启动的时候，会默认赋予名字为 docker 的用户组读写 Unix socket 的权限，因此只要创建 docker 用户组，并将当前用户加入到 docker 用户组中，
那么当前用户就有权限访问 Unix socket 了，进而也就可以执行 docker 相关命令

```shell
sudo groupadd docker     #添加docker用户组
sudo gpasswd -a $USER docker     #将登陆用户加入到docker用户组中
newgrp docker     #更新用户组
docker ps    #测试docker命令是否可以使用sudo正常使用
```

--- 