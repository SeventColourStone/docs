# 数据库迁移

好的开发者总是会用版本控制系统管理他们的代码，那为什么不同样对数据库进行版本控制呢？

Phinx 可以让开发者简洁的修改和维护数据库。 它避免了人为的手写 SQL 语句，它使用强大的 PHP API 去管理数据库迁移。开发者可以使用版本控制管理他们的数据库迁移。 Phinx 可以方便的进行不同数据库之间数据迁移。还可以追踪到哪些迁移脚本被执行，开发者可以不再担心数据库的状态从而更加关注如何编写出更好的系统。

stone 使用 phinx 作为数据库版本工具，预置了数据库备份功能

```shell

Description:
  phinx seeder create 一键数据库备份

Usage:
  phinx:seeder:create [options]

Options:
  -t, --table[=TABLE]   数据库表 名称
  -p, --path[=PATH]     生成的文件路径，默认为插件下plugin/stone/database/seeds_[path] 不填默认为YmdHi
  -h, --help            Display help for the given command. When no command is given display help for the list command
  -q, --quiet           Do not output any message
  -V, --version         Display this application version
      --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
  -n, --no-interaction  Do not ask any interactive question
  -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

Help:
  phinx seeder create 数据备份


#例如：
php .\webman phinx:seeder:create --table=system_menu --path=test

```

更多使用请参考 [phinx](https://book.cakephp.org/phinx/0/en/intro.html) 官网文档