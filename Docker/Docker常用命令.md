# Docker常用命令

## Docker服务命令

启动Docker服务

```bash
systemctl start docker
```

停止Docker服务

```bash
systemctl stop docker
```

开机自动启动Docker服务

```bash
systemctl enable docker
```

查看docker版本

```bash
docker version
```

查看docker服务状态。

```bash
systemctl status docker
```

## Docker容器命令

查看已经创建的容器

```
docker ps -a
```

查看已经启动的容器

```
docker ps
```

启动名为con_name的容器

```
docker start con_name
```

停止名为con_name的容器

```
docker stop con_name
```

重启名为con_name的容器

```
docker restart con_name
```

删除名为con_name的容器

```
docker rm con_name
```

进入名为con_name的容器

```
docker exec -it con_name /bin/bash
```

开机自启动名为con_name的容器

```
docker update --restart=always con_name
```

关闭开机自启动名为con_name的容器

```
docker update --restart=no con_name
```

## Docker镜像命令


