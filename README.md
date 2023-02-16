# Linux学习笔记，记录网上找到的一些代码和命令

## 甲骨文DD脚本

### MoeClub脚本

DD成Debian 11

```bash
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/MoeClub/Note/master/InstallNET.sh') -d 11 -v 64 -p "自定义root密码" -port 22
```

1. 新增对 Oracle AMD，Oracle ARM全面支持. 可支持从 Ubuntu, Oracle Linux 等系统网络重装.
2. 更新 dd 镜像的基础系统版本.
3. 移除对外部 wget 的依赖.
4. 新增 -port 参数, 可更改默认SSH端口.
5. 更新 内置的网络参数计算 逻辑.
6. 更新 grub 配置文件定位逻辑, 可支持任意引导grub的系统.

以下系统已通过测试(其他自测):

- Debian: 9, 10, 11
- Ubuntu: 18.04, 20.04
- CentOS: 6.10

以下平台已通过测试(其他自测):

- Oracle、Do、Azure

**参数说明**

- -d：Debian系统
- -u：Ubuntu系统
- -c：CentOS系统
- -v：系统位数，64或32
- -p：自定义root密码
- -port：自定义ssh端口

### 备份

```bash
bash <(wget --no-check-certificate -qO- 'https://raw.githubusercontent.com/hczjl/Note/main/InstallNET.sh') -d 11 -v 64 -p "自定义root密码" -port 22
```

## 一键BBR加速脚本

**BBR 原版/BBR 魔改/BBR plus/锐速 四合一脚本**

登陆 ssh 运行`BBR 4 in 1 脚本`

```bash
wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```

安装BBR plus需要先安装内核

![](https://raw.githubusercontent.com/hczjl/Note/main/pic/bbr-1.png)

如图，分别选择 2 和 7，根据提示即可开启成功。


## swap.sh

> SWAP虚拟内存脚本

