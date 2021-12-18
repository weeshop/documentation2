---
title: 创建项目工程
weight: 10
---

使用 `composer` 是创建 WeeShop 工程的最佳方式。

```bash
composer create-project weeshop/weeshop_project weeshop  && cd weeshop
php -d memory_limit=256M web/core/scripts/drupal quick-start weeshop
```