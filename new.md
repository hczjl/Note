# 命令备忘录

## 甲骨文增加CPU占用

```
docker run --cpus=0.2 -d alpine sh -c "while true; do continue; done"
```

```
docker run --cpus=0.2 -d --name=alpine --restart=always alpine sh -c "while true; do continue; done"
```

## Debian Ubuntu 系统安装宝塔破解版（需要特殊网络）

```
wget -O install.sh http://v7.hostcli.com/install/install-ubuntu_6.0.sh && sudo bash install.sh
```
