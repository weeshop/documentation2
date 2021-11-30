---
title: "快速开始"
linkTitle: "快速开始"
weight: 10
---


本项目提供了预置的 Docker 镜像，并编排到了模板工程根目录的 `docker-compose.yml` 中。

如果使用 `docker-compose`，你将无须关心PHP环境问题，您的电脑啥都不需要安装，除了基本的 `Docker` 服务和 `docker-compose`。

如果docker镜像下载慢，请自行了解 [如何加速docker镜像下载](https://www.baidu.com/s?wd=docker%E5%8A%A0%E9%80%9F)

如果不希望使用 docker 快速安装，也可以参考 [通过传统的手工方式安装](user_guide/install.html)

先决条件：
- 确保本机8080端口没有被占用。这是因为 `docker-compose.yml` 中需要映射 Web 容器的 80 端口到物理机的 8080 端口。

```bash
# 创建 WeeShop 模板工程sdsdfsdf
composer create-project weeshop/project-base:dev-8.x-1.x WeeShop --stability dev --no-interaction -vvv

# 进行工程目录
cd WeeShop

# 启动 docker 容器
docker-compose up -d

# 进入 docker 容器
docker-compose exec web bash

# 进入容器后，在容器内继续运行下面的命令
# 安装实例
su - application -c \
"cd /app/web/sites && /usr/local/bin/drupal site:install --force --no-interaction weeshop  \
--langcode='en'  \
--db-type='mysql'  \
--db-host='db'  \
--db-name='drupal'  \
--db-user='root'  \
--db-pass='123'  \
--db-port='3306'  \
--site-name='My WeeShop'  \
--site-mail='164713332@qq.com'  \
--account-name='admin'  \
--account-mail='164713332@qq.com'  \
--account-pass='123'"

# 更新翻译
su - application -c "cd /app/web/sites && \
/usr/local/bin/drush -vvv locale:check && \
/usr/local/bin/drush -vvv locale:update"
```

浏览器访问 `http://localhost:8080`，开始体验吧！
