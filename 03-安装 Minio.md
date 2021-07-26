# 1、安装

> 查找镜像
>
> `docker images`

```bash
🔥 ~ docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
mysql        5.7       9f1d21c1025a   6 days ago     448MB
alpine/git   latest    b8f176fa3f0d   2 months ago   25.1MB
🔥 ~
```

> 搜索 `minio`
>
> `docker search minio`

```bash
🔥 ~ docker search minio
NAME                           DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
minio/minio                    Kubernetes Native, High Performance Object S…   467                  [OK]
minio/mc                       Minio Client (mc) provides a modern alternat…   23                   [OK]
minio/console                  A graphical user interface for MinIO server     8
pixelchrome/minio-arm          This Dockerfile installs Minio on your ARM-P…   5
jessestuart/minio              Minio server — supports arm (arm32v6, arm32v…   5
opennms/minion                 Application container runs Minion by OpenNMS…   3                    [OK]
webhippie/minio                Docker images for Minio                         3                    [OK]
rook/minio                     Minio is a high performance distributed obje…   2
azinchen/minio                 Minio server Docker image. Always up-to-date…   1
teamwork/minio                 Minio for Teamwork                              1
zenithar/minio-server          Minio.io Server in Alpine Linux docker          1                    [OK]
tobilg/minio-dcos              minio on DC/OS                                  0                    [OK]
minio/mint                     Collection of tests to detect overall correc…   0                    [OK]
keikoproj/minion-manager       https://github.com/orkaproj/minion-manager      0
joepll/minio-exporter          Prometheus exporter for Minio server            0
topdockercat/minio-unraid      Minio is an Amazon S3 compatible object stor…   0                    [OK]
opsmx11/minio                  Minio for Openshift                             0                    [OK]
rwsdockercf/minio-resource                                                     0
leviy/minio                    Minio image for development and testing of (…   0                    [OK]
minio/k8s-operator             Minio Operator for k8s https://kubernetes.io/   0
nerc/minio                     Minio container for use in the datalab proje…   0                    [OK]
kimurashuhei/minio             minio server for using it in github actions     0
kazesberger/miniomc-postgres   this image is used to create postgres dumps …   0
sourcegraph/minio                                                              0
enzime/minio-docker            Modifies the default command of the minio:mi…   0                    [OK]
🔥 ~ 
```

>拉取 `minio`
>
>`docker pull minio/minio`
>
>执行完成后，`docker images` 可看到 `minio` 已在镜像列表中

```bash
🔥 ~ docker pull minio/minio
Using default tag: latest
latest: Pulling from minio/minio
158b4527561f: Pull complete
a3ba00ce78fe: Pull complete
a151cbf2ea2b: Pull complete
3496ebb2bcd5: Pull complete
93422f11e447: Pull complete
21a579802bf9: Pull complete
2bff17d809fa: Pull complete
Digest: sha256:6f97f549a31e2157821bd40c13f70d9469bb4f599ffcac1e55ed6f4d7c9bc8d1
Status: Downloaded newer image for minio/minio:latest
docker.io/minio/minio:latest
🔥 ~
```





# 2、启动

> `docker run -it -p 9000:9000 -d minio/minio server /data`
>
> *参数说明*
>
> - `docker run`：运行 docker 容器命令
> - `-p 9000:9000`：将容器的 `9000` 端口映射到主机「宿机」的 `9000` 端口，格式 ***主机「宿机」端口:容器端口***
> - `-d`：后台运行容器，并返回容器`id`
> - `/data`：指定 `minio` 文件存放目录


