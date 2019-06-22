# 数据库设计

## 项目表

当前表存放所有项目，后面的组、权限都会与项目挂钩。

```sql
CREATE TABLE `project` (
  `id` int(11) unsigned NOT NULL AUTO_INCREMENT,
  `key` varchar(16) NOT NULL DEFAULT '' COMMENT '项目唯一KEY',
  `name` varchar(32) NOT NULL DEFAULT '' COMMENT '项目名',
  `comment` varchar(512) NOT NULL DEFAULT '' COMMENT '项目介绍',
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `UNIQUE_KEY` (`key`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```