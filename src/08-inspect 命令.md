# inspect 命令

> 使用 `docker inspect` 来查看 Docker 的底层信息。它会返回一个 JSON 文件记录着 Docker 容器的配置和状态信息

- 命令

> `docker inspect <CONTAINER ID>`

- 实例

```shell
🔥  ~/Developer/docker  docker ps -a                           
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                      PORTS                                                  NAMES
4224b128cb72   hello-world   "/hello"                 49 minutes ago   Exited (0) 45 minutes ago                                                          vigilant_gagarin
49586a76cfa9   minio/minio   "/usr/bin/docker-ent…"   6 weeks ago      Up 21 minutes               0.0.0.0:9000->9000/tcp, :::9000->9000/tcp              ecstatic_leakey
acffd8c2a243   mysql:5.7     "docker-entrypoint.s…"   7 weeks ago      Up 41 minutes               0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql
28a017afa5f7   alpine/git    "git clone https://g…"   8 weeks ago      Exited (128) 8 weeks ago                                                           repo
🔥  ~/Developer/docker  docker inspect acffd8c2a243
[
    {
        "Id": "acffd8c2a243d5fbb425c9f125f02c0a2e6ad4a1f6698a7c8b7c8a132b642976",
        "Created": "2021-07-21T14:13:19.635344968Z",
        "Path": "docker-entrypoint.sh",
        "Args": [
            "mysqld"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 2630,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2021-09-09T15:01:00.230493465Z",
            "FinishedAt": "2021-09-09T14:58:44.026208594Z"
        },
        "Image": "sha256:9f1d21c1025ab10f9994398f01bb09eb7b6bd0861b3cff0fc9e0a8c265615772",
        "ResolvConfPath": "/var/lib/docker/containers/acffd8c2a243d5fbb425c9f125f02c0a2e6ad4a1f6698a7c8b7c8a132b642976/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/acffd8c2a243d5fbb425c9f125f02c0a2e6ad4a1f6698a7c8b7c8a132b642976/hostname",
        "HostsPath": "/var/lib/docker/containers/acffd8c2a243d5fbb425c9f125f02c0a2e6ad4a1f6698a7c8b7c8a132b642976/hosts",
        "LogPath": "/var/lib/docker/containers/acffd8c2a243d5fbb425c9f125f02c0a2e6ad4a1f6698a7c8b7c8a132b642976/acffd8c2a243d5fbb425c9f125f02c0a2e6ad4a1f6698a7c8b7c8a132b642976-json.log",
......
```