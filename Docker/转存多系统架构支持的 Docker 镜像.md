# 转存多系统架构支持的 Docker 镜像

> 参考文档：https://www.kancloud.cn/spirit-ling/docker-study/1413277

本文以转存Halo 1.6官方镜像为例

## 拉取镜像

```bash
docker pull halohub/halo:1.6@sha256:668f4ec33f099f6b47c73af97432fda1b94ca40e61af5bd7ef0584d70ea565ed
docker pull halohub/halo:1.6@sha256:034bea9cac5622a0eb0dccd1a56d8bfbe88b270a00d35fba77e0b7134ba479af
docker pull halohub/halo:1.6@sha256:d351b5d3df9a11dca3c9933c4a58e367c27d1b282dee4e74653e8a10680b0b53
```

## 分别打上对应的标签

```bash
docker tag ID hczjl/halo:amd64
docker tag ID hczjl/halo:arm64
docker tag ID hczjl/halo:arm32
```

## 推送镜像

```bash
docker push hczjl/halo:amd64
docker push hczjl/halo:arm64
docker push hczjl/halo:arm32
```

## 创建manifest清单包含多个不同架构镜像

```bash
docker manifest create hczjl/halo:1.6 hczjl/halo:amd64 hczjl/halo:arm64 hczjl/halo:arm32
```

## 标注不同架构镜像

```bash
docker manifest annotate hczjl/halo:1.6 hczjl/halo:amd64 --os linux --arch amd64
docker manifest annotate hczjl/halo:1.6 hczjl/halo:arm64 --os linux --arch arm64
docker manifest annotate hczjl/halo:1.6 hczjl/halo:arm32 --os linux --arch arm --variant v7
```

## 推送manifest清单

```bash
docker manifest push hczjl/halo:1.6
```

## 删除本地manifest清单副本

```bash
docker manifest rm hczjl/halo:1.6
```

## 查看manifest清单

```bash
docker manifest inspect hczjl/halo:1.6
```

```shell
{
   "schemaVersion": 2,
   "mediaType": "application/vnd.docker.distribution.manifest.list.v2+json",
   "manifests": [
      {
         "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
         "size": 2412,
         "digest": "sha256:0206a4494a69ad6853c5083561213b6466f6c69f23b8a51cae1317bdab883235",
         "platform": {
            "architecture": "amd64",
            "os": "linux"
         }
      },
      {
         "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
         "size": 2412,
         "digest": "sha256:cd7aa5a288d6ecb6eca55a67da64cb895d253344dfc050b0021f3f91b3474efb",
         "platform": {
            "architecture": "arm",
            "os": "linux",
            "variant": "v7"
         }
      },
      {
         "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
         "size": 2412,
         "digest": "sha256:0402c028c946b219493fb791529b2d814f7998b2e65922f64844b8d1fc9e42fc",
         "platform": {
            "architecture": "arm64",
            "os": "linux"
         }
      }
   ]
}
```

官方halo 1.6 manifest清单

```shell
{
   "schemaVersion": 2,
   "mediaType": "application/vnd.docker.distribution.manifest.list.v2+json",
   "manifests": [
      {
         "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
         "size": 2412,
         "digest": "sha256:668f4ec33f099f6b47c73af97432fda1b94ca40e61af5bd7ef0584d70ea565ed",
         "platform": {
            "architecture": "amd64",
            "os": "linux"
         }
      },
      {
         "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
         "size": 2412,
         "digest": "sha256:d351b5d3df9a11dca3c9933c4a58e367c27d1b282dee4e74653e8a10680b0b53",
         "platform": {
            "architecture": "arm",
            "os": "linux",
            "variant": "v7"
         }
      },
      {
         "mediaType": "application/vnd.docker.distribution.manifest.v2+json",
         "size": 2412,
         "digest": "sha256:034bea9cac5622a0eb0dccd1a56d8bfbe88b270a00d35fba77e0b7134ba479af",
         "platform": {
            "architecture": "arm64",
            "os": "linux"
         }
      }
   ]
}
```
