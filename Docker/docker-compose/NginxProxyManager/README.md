# Nginx Proxy Manager反向代理

官方网站：https://nginxproxymanager.com/

## 特点：

- 基于Tabler的美观安全的管理界面
- 在对 Nginx 一无所知的情况下轻松创建转发域、重定向、流和 404 主机
- 使用 Let's Encrypt 的免费 SSL 或提供您自己的自定义 SSL 证书
- 主机的访问列表和基本 HTTP 身份验证
- 超级用户可用的高级 Nginx 配置
- 用户管理、权限和审计日志

## 创建docker-compose文件

```yml
version: "3"
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      # These ports are in format <host-port>:<container-port>
      - '80:80' # Public HTTP Port
      - '443:443' # Public HTTPS Port
      - '81:81' # Admin Web Port
      # Add any other Stream port you want to expose
      # - '21:21' # FTP
    environment:
      DB_MYSQL_HOST: "db"
      DB_MYSQL_PORT: 3306
      DB_MYSQL_USER: "npm"
      DB_MYSQL_PASSWORD: "npm"
      DB_MYSQL_NAME: "npm"
      # Uncomment this if IPv6 is not enabled on your host
      # DISABLE_IPV6: 'true'
    volumes:
      - ./data:/data
      - ./letsencrypt:/etc/letsencrypt
    depends_on:
      - db

  db:
    image: 'jc21/mariadb-aria:latest'
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: 'npm'
      MYSQL_DATABASE: 'npm'
      MYSQL_USER: 'npm'
      MYSQL_PASSWORD: 'npm'
    volumes:
      - ./data/mysql:/var/lib/mysql
```

```bash
docker-compose up -d
```

## 初始运行

应用程序首次运行后，将发生以下情况：
1. 数据库将使用表结构进行初始化
2. GPG密钥将生成并保存在配置文件中
3. 将创建一个默认的管理员用户

此过程可能需要几分钟，具体取决于您的机器。

## 登录网址

http://127.0.0.1:81

## 默认管理员用户

```txt
Email:admin@example.com
Password: changeme
```

使用此默认用户登录后，系统会立即要求您修改详细信息并更改密码。



