---
title: "Get started"
linkTitle: "Documentation"
menu:
  main:
    weight: 30
---

<div style="width: 200px; margin-left:60px;">

[![WeeShop](images/WeeShop.png)](https://github.com/weeshop/weeshop)

</div>

<p style="text-align: center; display: flex;">

![GitHub stars](https://img.shields.io/github/stars/weeshop/weeshop?style=social)
![GitHub forks](https://img.shields.io/github/forks/weeshop/weeshop?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/weeshop/weeshop?style=social)

</p>


优雅易用的开源商城，支持多货币，多语言，包含 [移动端以及微信小程序](https://github.com/weeshop/WeeApp)
基于 GPL-2.0 开源协议发布，真开源，这是属于中国开源社区的商城。
基于 Laravel 的基因，来自 Symfony 的底层技术，来自 Drupal Commerce 的核心技术，由 Drupal 中国开源社区维护。

## 加入 WeeShop 社区
QQ群：714023327


感谢您的关注，WeeShop的成功离不开您的意见和支持：
- 马上Star此项目，最好同时Fork此项目，以帮助让更多的人看到此项目。
- 我们万分欢迎您参与开发，我们的组织在 [github.com/weeshop](https://github.com/weeshop)。 
- 我们希望听见您的心声，请 [创建issue](https://github.com/weeshop/WeeShop/issues/new) 来表达您的意见。

## 界面截图

简洁的美观的 UI 界面：

![](images/screenshot.jpg)

![](images/screenshot3.jpg)

支持使用 `Apache Solr` 集群对商品进行`全文检索`，支持使用属性进行`分面搜索`，支持对搜索结果进行预提示：

![](images/screenshot2.png)


工程 [WeeShop/WeeShop](https://github.com/weeshop/weeshop) 后台与服务端，微信小程序端的工程在 [WeeShop/WeeApp](https://github.com/weeshop/WeeApp)。


## 特性
- 灵活的商品属性系统，可表达任意类型的商品，包括虚拟商品。
- 支持多仓库存管理，也支持不需要库存管理的商品。
- 灵活的结账过程，可以针对任意商品类型定制结账过程。
- 支持全球的物流信息对接，支持国内各大快递公司。
- 完备的多语言系统，支持全球100多种语言。
- 支持全球流行的各种支付手段，Paypal、支付宝、微信、银行卡等。
- 使用全文检索技术，可以选择使用各种流行的全文检索方案，如Apache solr等。
- 支持符合工业标准的RESTful接口，可配置多种认证方式HTTP Basic、Oauth2.0 等，轻松进行移动应用开发。

## 快速安装


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


#### 重要Issuse 
- Docker for windows, volume默认权限是755，而无法更改 [#issues39](https://github.com/docker/for-win/issues/39)
  
  - 解决办法，使用Mac或Linux系统
  - 在 `docker-compose.yml` 中把 `/app/web/sites` 目录的volume注掉，让文件留在容器内